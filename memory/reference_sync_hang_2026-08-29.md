---
name: reference-sync-hang-2026-08-29
description: "Root cause and remediation for brain sync hang (third occurrence, 9 hours)"
metadata: 
  node_type: memory
  type: reference
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-11T19:17:19.459Z
---

# Brain Sync Hang Root Cause · 2026-08-29

## The Three Incidents

1. **23 Aug 14:00 to 05:00 (15 hours):** `git add -A` blocked at zero CPU in kernel wait, held `.git/index.lock`. Evidence: Task Scheduler showed Running, Last Result 0x800710E0.
2. **28 Aug 17:15 to 19:48 (~2.5 hours):** Same signature. Killed by hand.
3. **28 Aug 20:30 to 29 Aug 02:11 (4 h 40 min):** Same. Third time.

## Evidence (frozen at incident #3, line 28 Aug 20:16 in .git/index)

- **Lock file:** `.git/index.lock` = 0 bytes (no owner, no work in progress)
- **Index file:** `.git/index` = 519,092 bytes (untouched since 20:15)
- **Git objects:** No writes after 20:16 (checked `ls -lt .git/objects`)
- **Processes:** PIDs 12136 (PowerShell wrapper), 34332 (real git), 18332 (child) all at zero CPU, in Executive kernel wait
- **Unsynced files:** 6 changed files, never left laptop

## Why the Mutex Could Not Help

The mutex (`Global\KDBrainSyncMutex`) gates new instances. **It does not gate the same instance if it hangs mid-add.** A hung `git add -A` holds the lock but never returns, so:
- The mutex prevents a second instance starting (good)
- But the first instance never releases the mutex
- Next cycle: mutex held = skip, log "another sync is running" (false; it's hung)
- No alert (the script sees the mutex as normal, not a stale lock)

**Result:** Silent 15-hour backup failure.

## The Prompt Mechanism Hypothesis

The strongest candidate for the root cause:

- `git add -A` internally calls `git update-index`, which may open stdin to prompt for credentials
- When stdin is a console (Task Scheduler runs scripts with inherited stdio), an interactive prompt blocks forever if no input comes (it waits for a user who never arrives)
- The kernel wait at zero CPU matches: it's waiting for stdin, not doing work
- **Evidence:** No error message logged; it's not a timeout or crash, it's a clean wait

## The Hardening (Stage B, 2026-08-29)

**File-redirected stdio:** The revised `sync_brain.ps1` pipes stdin from an empty file (`/dev/null` equivalent), so if `git` tries to prompt, it gets EOF and errors out instead of blocking forever. The error text becomes actionable proof.

**Task cap:** Set `ExecutionTimeLimit` to `PT10M` (was PT72H). If a git call times out, Windows kills the whole tree after 10 minutes, not 72 hours. Safe because the longest real git step in the log is 37 seconds.

**Orphan lock rule:** Lock older than 10 minutes = remove it, since any legitimate git process from a prior cycle would have finished long before.

**Exit codes:** Failures now exit 1 (not 0), so Task Scheduler's Last Result turns red. Honest status.

## The Trace That Will Name It Next Time

Set `GIT_TRACE2_PERF` to `~\.kd_brain_git_trace.log`, rotated at run start. If it hangs again:
- The trace file holds the last `region_enter` before the hang
- Git shows which command/phase was running when time ran out
- The name becomes the proof

Example: if the last line is `region_enter category:delta-islands`, then it's git's internal algorithm, not a prompt.

## Token Findings (Bonus)

The sync's actual login is **Git Credential Manager OAuth (`gho_`)**, mirrored to `~\.git-credentials` by the store helper. No expiry. The three "expiring" tokens are classic `ghp_` in `.env.master` and sandbox test scripts. They expire ~31 Aug, not the sync itself.

---

## Incident #4 · 2026-09-09 ~19:17, caught live

Same signature as the first three, observed while it was happening rather than after:

- `git add -A` (PIDs 5112 and 25752), **7.7 minutes old, 0.3 and 0.0 CPU seconds**. Not working,
  blocked. That CPU figure is the whole diagnosis: a real `git add -A` on this repo finishes in
  seconds and burns CPU while it does.
- `.git/index.lock` present at **0 bytes**, exactly as recorded at incident #3.
- It blocked a real commit for the duration, which is how it was noticed at all.

### What the script actually does, read from it rather than from this file

Checked line by line during the incident, because the section above describes intentions and the
script is what runs.

| the RCA above says | `tools/sync_brain.ps1` actually | verdict |
|---|---|---|
| `ExecutionTimeLimit` PT10M | `KD_Brain_Sync` carries it, state was `Running` | **in place** |
| file-redirected stdin | `git add -A` at line 103, invoked bare | **not done** |
| `GIT_TRACE2_PERF` to a rotated log | no match anywhere in the script | **not done** |
| lock older than 10 min = remove it | line 92 to 100: warns above **30** min and exits 1, never removes | **different, and better** |

The lock rule is not a defect. The script deliberately refuses to auto-clear, and says why in its
own warning: *"Clear it at the laptop after checking nothing guarded is about to be staged."*
Auto-removing an index lock to unblock a backup is how a half-staged index becomes a corrupt one.
The RCA text is what is wrong here, not the code.

### The finding that actually matters: the leading hypothesis looks wrong

The section above names a credential prompt blocking on stdin as "the strongest candidate". **Line
17 of the script already sets `GIT_TERMINAL_PROMPT = '0'`, commented "never hang on a login
prompt".** That defence has been in place across incidents #2, #3 and #4, and it hung anyway.

So the prompt mechanism is either not the cause or not the whole cause. Anyone reading this RCA
should stop treating it as the working theory.

### A candidate specific to THIS occurrence, stated as a candidate

Three full pytest runs over the whole brain were running back to back while the sync fired, one of
them a 761-second coverage run, on a laptop whose C: drive is at 91 percent. Zero-CPU kernel wait is
what disk starvation looks like from the outside. That fits incident #4 and explains nothing about
#1 to #3, which happened with nobody at the machine. Recorded so it is not mistaken for a root
cause, and so the next reader knows the machine was under load.

### Second gap, found in the same check

The cap was applied to `KD_Brain_Sync` but **`KD_Binder_Sync` is still `ExecutionTimeLimit =
PT72H`**, the original value. One task was hardened and its sibling was not, so the 72-hour
silent-failure window this RCA exists to close is still open on the binder sync.

### Both closed, 9 Sep evening, on King's word

1. **`GIT_TRACE2_PERF` IS WIRED**, in `sync_brain.ps1` beside the terminal-prompt line. Rotated at
   run start with the previous run kept as `.prev`, because a hang is noticed on the NEXT cycle and
   by then this run has already rotated. Proven by running a real git command under it: **36 regions
   logged**. Four incidents produced no evidence; the fifth will.

2. **`KD_BINDER_SYNC` WAS NOT ONE LINE, AND THE CAP WAS THE SMALL HALF.** Reading it before
   changing it found the task had **never successfully run in its life**:

   | | KD_Brain_Sync | KD_Binder_Sync (before) |
   |---|---|---|
   | refuse to start on battery | False | **True** |
   | stop if going on battery | False | **True** |
   | ExecutionTimeLimit | PT10M | **PT72H** |
   | last result | 0x0 | **0x800710E0** |

   `0x800710E0` is Task Scheduler refusing to start it, and on a laptop that is usually on battery
   that refusal is permanent. The proof it had never run: the task redirects output with `>>`, which
   creates the file on first execution even when the script prints nothing, and
   `_private/binder_sync.log` **did not exist**. So the binder had never once been pushed to LOGIC-B
   on a schedule.

   All three settings now match its sibling. The power ones are the fix; the cap is the hardening
   King actually asked for. Allowing it on battery is a small cost by comparison: this task runs
   **once daily**, while `KD_Brain_Sync` already runs on battery every fifteen minutes.

   **Proven by running it, not by reading the settings back.** 7.4 seconds, result `0x0`, and the
   log finally exists:

   ```
   [2026-09-09 19:54 UTC] binder rebuilt, 5 home-lane lines removed
   night log pulled home
     CLAUDE.md              VERIFIED 3598b3f7d69a
     RUNBOOK_LOGIC_B.md     VERIFIED fd2ce83b3a7a
     CAMPUS_STATE.js        VERIFIED 3789f173c369
     HANDOFF.md             VERIFIED 29b1dcb1ff9f
   [2026-09-09 19:54 UTC] binder on LOGIC-B, every file hash-verified
   ```

   7.4 s against a 10-minute cap is 80x headroom, so PT10M is generous and correct. The script is
   bounded by construction anyway: SSH with `ConnectTimeout 10` and per-call timeouts of 60 s, and
   it exits 0 with a "skipped" note when the box is unreachable.
3. Correct the lock-rule paragraph above so it describes the 30-minute warn-and-stop the script
   really implements, rather than a 10-minute auto-remove it deliberately refuses to do.

---

## Incident #5 · 2026-09-11 20:00, the FIRST with trace evidence, cause found

- **What hung:** `git pull --rebase --autostash origin main` inside the 20:00 sync. The trace's last
  line is 20:00:35.905, `unpack_trees` left, then nothing. 0.33 CPU seconds in 3 minutes, a 0-byte
  `.git/index.lock`, `.git/rebase-merge` holding only `autostash`. The PT10M cap ended it at 20:10
  (task result 0x41306).
- **Cause:** `_ops/brain_fts5_index.sqlite3-journal` was TRACKED. `.gitignore` covered `*.sqlite3`
  but not SQLite's `-journal`, `-wal` or `-shm` side-files. Claude's index rebuild (fix R5.4, started
  19:49) held the journal open and rewrote it constantly. The 20:00 sync's `git add -A` committed it
  (f873a0a2, its first ever commit), then the autostash tried to reset it while the rebuild held it.
  On Windows git then waits on "Unlink of file ... failed. Should I try again? (y/n)", which
  `GIT_TERMINAL_PROMPT=0` does not cover. Zero CPU, waiting on stdin: the signature of every incident.
- **Cleared 20:11:** `git rebase --quit` (the autostash, only that journal, kept as stash@{0});
  journal untracked; `.gitignore` now covers `-journal`, `-wal`, `-shm` for `.db`, `.sqlite`,
  `.sqlite3` (commit 5f92458e, pushed). **The 20:15 sync: "synced OK" 20:16:03, result 0x0.**
- **Lesson for the earlier four:** look for a file another process holds open. A tracked file that a
  running program writes (a database side-file, a log, a lock) makes the sync hang, and the rule is
  to ignore such files, never to kill the writer.
