---
name: feedback-verify-route-by-last-run
description: A backup or sync route is only real when its LAST SUCCESSFUL RUN has been checked. A script existing is not a route running.
metadata: 
  node_type: memory
  type: feedback
  originSessionId: c5d66f2f-ab81-4e5f-854d-e8813d381bfd
  modified: 2026-08-10T09:45:19.036Z
---

# A route is real only when its last run is checked

**Found 2026-08-10 after the same failure appeared three separate times in one session.** This extends
the 08-10 law ("a file is guarded only when EVERY route is checked") from *coverage* to *liveness*.

## The rule

**Never treat a backup, sync or guard as working because a script for it exists, a schedule mentions it,
or a log says "OK". Check the last successful run against a real timestamp on the destination.**

The failure is always silent, and it always looks like success from the inside.

## Why · three instances, one night

1. **The git sync was dead six days** (found 08-09) behind a stale `.git/index.lock`, while the robot
   kept logging "synced OK" every cycle. The log was written before the failure could be detected.
2. **The guarded set had exactly one copy** (found 08-10, Stage 0) despite two backup routes existing.
   Both routes excluded it **by design**, so the design was working perfectly and the outcome was a
   single point of failure. Every guarded file returned exactly one copy on disk.
3. **The Drive brain sync had never been automated** (found 08-10). `tools\sync_claude_to_drive.py`
   exists, is maintained, and had two rounds of security hardening in two days, but **no scheduled task
   runs it.** Newest brain material on Drive was **May 2026**, roughly eleven weeks stale. The "road to
   the Amazon work laptop" only opens when someone runs that script by hand.

Instance 3 is the sharpest, because effort was being spent hardening a route that was not flowing, and
that effort *felt* like protection.

## ⚠️ CREDIT CORRECTION (2026-08-10): King had already built this principle in code

**This lesson was filed on 2026-08-10 as if it were new. It was not. King had implemented it himself,
earlier, in `tools\mission_control.py`.** Reading that file end to end later the same morning found:

- Module docstring: *"real Windows Task Scheduler + real logs + real state files, **no fake green**"* and
  *"Reads Task Scheduler live; **never trusts a schedule's 'Ready' as 'healthy'**."*
- `status_of()`: *"Derive the **TRUE** status"*, returning `stale` with *"no successful run in Nh"* when a
  task claims Ready while its log is cold.

**So the principle is King's, in his own code, before Claude wrote it down.** Per the standing rule: check
the record before crediting anything to a session, because most of it is already his.

### But the implementation had one hole, and it is exactly why the 6-day death went unseen

The staleness check carried a **blanket exemption list**, and **`KD_Brain_Sync` was on it**. So the
fake-green detector was **structurally incapable of flagging the one task that faked green.** The intent was
sound (a 40-hour limit is meaningless for a job that runs every 15 minutes), but exempting a task removes
the only detector, when what a frequent job needs is a **tighter** limit, never no limit.

**The generalised lesson, which is sharper than the original:** *an exemption in a monitoring rule is a
blind spot with a comment on it.* When a check does not fit a case, **narrow the threshold, do not waive the
check.** Every waiver should be read as "this thing can now die silently."

**Status: HALF FIXED as of 2026-08-10 10:15.** A `STALE_LIMIT_H` dict (per-task hours, Brain Sync at 2h) was
added to `mission_control.py` but is **NOT yet wired into `status_of()`**, which still runs the old exemption
logic. Behaviour is unchanged and the dict is currently dead code. Two lines finish it.

**And an honest scope limit on the fix itself:** a staleness limit catches a job that **stopped running**. It
does not catch a job that runs, fails internally, and still writes a fresh log. That needs the non-zero
`Result` check plus the script's own exit code (`sync_brain.ps1` now exits 1 when `git add` fails). The
strongest check would ask the **destination** whether it actually received anything, for example whether
`origin/main` advanced. Not built.

## How to apply

Three cheap checks, in this order:

1. **Destination timestamp, not source intent.** Ask the destination what it last received. For git:
   compare `main` against `origin/main` and read the newest commit date. For Drive: search for a file
   you know should be there and read its `modifiedTime`.
2. **Prove the negative.** An empty search result from a broken query looks identical to a clean
   destination. Always run a control query that *should* return something. On 08-10 this is exactly what
   turned "nothing guarded is on Drive" from a guess into a verified fact.
3. **Confirm it is scheduled.** `schtasks /query /fo CSV` and look for the task by name. A tool with no
   task is a manual tool, whatever the docs imply.

**The generalisation worth keeping:** a guard, a backup and a test all share this property. They are
claims about the future, and a claim is only worth what its last verification is worth. This is the same
error class as listing a file as existing because it appeared in `.gitignore`, which also happened this
session.

**And the fix that actually holds: write the guard as a test, not as a list.** On 2026-08-10 a
cross-route consistency test was added to `tests\unit\test_sync_claude_to_drive.py`. It parses
`.gitignore`'s guarded sections and asserts every concrete laptop-only file is also in `SKIP_FILENAMES`.
**It failed on its first run and found a third live leak** that two careful manual passes had missed, in
0.55 seconds. A comment cannot enforce a rule. A test can.

**Order of operations for a new guarded file (upgraded 2026-08-22):** the brain auto-commits and pushes every
15 minutes (`tools\sync_brain.ps1`, `git add -A`), so "add the rule in the same commit" has a window in which the
file is already public. **Ignore rule first, `git check-ignore -v` proves it, then create the file.** Reserving a
filename in `.gitignore` and `SKIP_FILENAMES` before it exists is the safe pattern; `LOGOS_0_MATHS.md` sat reserved
from 10 Aug to 22 Aug and was created without a single edit to either guard.

Related: [[feedback_audit_before_build_own_brain]] · [[feedback_hold_king_to_literal_accuracy]] ·
[[feedback_asymptote_c_and_e_moves]] · [[reference_anthropic_data_terms]]
