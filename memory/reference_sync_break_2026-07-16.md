---
name: reference-sync-break-2026-07-16
description: "Full RCA + fix + verification for a 6-day silent brain-sync break found 2026-07-16: laptop push to GitHub had failed every cycle since 07-10 08:32, hidden by a script that logs but never alerts."
metadata:
  node_type: memory
  type: reference
  originSessionId: 103a68c9-2bd8-421d-b4dd-0a66681a49a0
  modified: 2026-07-31T22:48:41.223Z
---

# The 6-day silent sync break (2026-07-16) · full RCA

## Root cause, step by step
1. On **2026-07-10 08:32:23**, this laptop's `main` and the GitHub `origin/main` last shared a common commit
   (`f4563dc`). After that point they diverged, both sides kept working, neither knew about the other.
2. On the remote side (another device/session), a real and good thing happened: **`TEST_SPREE_CLEANUP_2026-07-10.md`**
   documents that Jul 7-10 runaway sessions had pushed 33 fake "phases," 1,672 tests that tested toy code
   inside the test files, not the brain's real tools, straight to `main` with no review. That remote session
   caught it, deleted the filler (~21,600 lines), trimmed `requirements-test.txt`, and fixed a second real bug
   in the same pass: `.gitignore` had never allowlisted `handoffs/`, so every `/save` handoff was silently
   un-committable since the safety lock went in.
3. Meanwhile, unaware of any of that, **this laptop kept working locally for 6 more days**, including its own
   separate, legitimate real-test conversion (`test_produce_spec.py`, `test_edit_analyze.py`, `test_email.py`,
   each importing the real tool module, not toy copies) plus six days of ordinary brain work, 594 files' worth.
4. Every ~15-30 minutes, `tools/sync_brain.ps1` ran as scheduled. Step 1 (commit local changes) always
   succeeded, which is why the local commit log looked perfectly healthy. **Step 2 (`git pull --rebase`) failed
   every single time** because of the real, substantive conflict between local's un-merged pre-cleanup history
   and the remote's cleanup. On failure the script correctly aborts the rebase (no data loss, by design) and
   exits **before ever reaching step 4 (push)**.
5. Result: **83 consecutive sync cycles committed locally but never pushed**, and nothing surfaced this,
   because the only record was a WARN line in `C:\Users\Dell\.kd_brain_sync.log`, which nothing reads or
   alerts on. Confirmed directly: that log shows the identical `WARN: pull conflict - skipped this cycle`
   line on every cycle back to 07-10 21:30.
6. This was caught 2026-07-16 only because King asked for a manual sync push, which surfaced the conflict
   in the foreground instead of failing silently in the background.

**In one line:** a good, correct safety behavior (never force a rebase past a real conflict) had no matching
alert behavior, so "safe" quietly became "silently broken" for 6 days. The fix below closes both gaps: the
one-time conflict, and the missing alert.

## The fix, step by step
1. Used a real **merge** (not another rebase) so only files touched on *both* sides needed a decision, verified
   via `comm -12` on the two changed-file lists: exactly 9 files, not 594.
2. `.gitignore` — auto-merged cleanly by git itself (both sides had touched different lines): kept the remote's
   `!/handoffs/` fix and local's own later additions (`!/README.md`, `!/.pre-commit-config.yaml`,
   `!/.coveragerc`, `.env.master` re-block).
3. `requirements-test.txt` — took the remote (trimmed, documented) version; local's expanded version predated
   the cleanup and was the stale one.
4. Four fake-spree files still on local disk (`test_load.py`, `test_performance_regression.py`,
   `test_phase_16_advanced_coverage.py`, `test_property_based.py`) — checked each for a real `tools/` import
   first (none had one), then deleted, matching the documented cleanup.
5. Three real, locally-rewritten files (`test_produce_spec.py`, `test_edit_analyze.py`, `test_email.py`) — each
   confirmed importing its real tool module, kept as-is, not overwritten by the remote deletion.
6. `memory/MEMORY.md` — kept local's newer, more complete index; folded in the one genuinely new fact from
   remote (the test-spree cleanup itself) as a dated note, since local's own file was factually stale on that
   point (Rule 19).
7. Committed the merge, pushed to `origin/main`.

## Results, verified
- `git status` clean, zero conflict markers remain in any file (checked by grep).
- Local `main` and `origin/main` now point at the same commit (checked via `git rev-parse` on both, matched).
- The 3 real local test files are present in the pushed tree; the 4 fake ones and the ~50 other spree files
  are gone from both local and remote, matching the cleanup doc's intent.
- Tonight's actual content, the family-story file, the elevated-state pattern log, the Foundation update, is
  confirmed present in the pushed commit.

## Update, later the same night: the CI failure + token fix
Fixing the merge exposed two more real, separate issues, both closed before the night ended:
- **Push itself got blocked**, GitHub refused the merge because it touched `.github/workflows/test-coverage.yml`
  and the stored token (classic, `ghp_...`, named "KD-Brain") only had `repo` scope, not `workflow`. King fixed
  this himself on GitHub (Settings → Developer settings → Tokens (classic) → KD-Brain → ticked `workflow` →
  Update token), no laptop-side change needed, verified by a clean push straight after.
- **The push that followed triggered real CI for the first time in days, and it failed**, self-inflicted:
  taking origin's trimmed `requirements-test.txt` dropped `requests`, which the kept-real test files
  (`test_edit_analyze.py`, `test_gen_router.py`, `test_hook_harvest.py`, `test_produce_spec.py`) need to even
  import. Fixed by adding `requests==2.31.0` back, and while in there, found and deleted one more fake-spree
  leftover the original cleanup missed (`test_phase_11_property_based.py`, hypothesis-only, no real tool
  import). Pushed, then actually watched the GitHub Actions run finish (not just claimed it): **success**,
  confirmed against the exact commit hash.
- **A separate, pre-existing issue surfaced and was deliberately left alone**: the same workflow's broader
  Windows-only test matrix (3 Python versions) fails while macOS/Linux all pass and the actual blocking gate
  ("Real-module coverage gate") passes clean. This predates tonight, isn't the blocking gate, and wasn't
  chased further given the hour, flagged for a future session with fresh eyes.

## The still-open gap (not fixed tonight, flagged for next session)
The alert gap that let this run silent for 6 days is still there: `sync_brain.ps1` step 2's failure path only
writes to a local log file nobody watches. **Fix for later:** make a pull-conflict WARN push King's phone the
same way a failed daily automation does (same pattern as `KD_Brain_Health` should already be doing for the
other automations found broken 2026-07-16). Not done tonight, deliberately, this needed a rested second look,
not a 3am code change layered on top of an already-long night.

## Update, next day (2026-07-17): Windows-only test matrix — root-caused and fixed
The Windows-only test matrix failure flagged above got the fresh-eyes look. Root cause, verified (not
guessed): `tests/unit/test_phase_critical_5_file_io.py`'s `test_path_absolute_unix_style` asserted
`"/" in str(Path("/home/user/file.txt"))`. `pathlib.Path` instantiates `WindowsPath` on Windows, and
`WindowsPath.__str__()` always renders backslashes regardless of the original string's separators — so the
assertion failed deterministically on every Python version on `windows-latest`, while Linux/macOS (where
`Path` is `PosixPath`) passed. Confirmed empirically on a real Windows machine (`str(Path("/home/user/file.txt"))`
→ `'\\home\\user\\file.txt'`, no `/` present), then grepped the whole `tests/` tree for the same pattern and
every other `Path("/...")` literal to confirm this was the only Windows-fragile line (5 other matches all
check filename substrings or expect `FileNotFoundError`/`OSError`, which raise fine on Windows too). Fixed by
swapping to `unix_path.as_posix()` (always forward-slash, any platform) — one line, `tests/` only, no tool
code touched. Verified locally: the specific test passes, full local suite run (695 passed, 6 unrelated
pre-existing failures in timing-sensitive throughput/mock tests, untouched — separate issue, not bundled in).
Committed (`18a9dc3`) and pushed to `origin/main`, fast-forward, no conflict.
**Superseded later the same session — CI can't verify ANYTHING right now:** checking the live run revealed a
TOTAL CI outage since 07-16 22:30 UTC. Not code: GitHub's free 2,000 Actions minutes were exhausted (the
sync fix's resumed 15-min pushes x duplicate workflow x macOS-10x matrix burned the month's quota in hours).
Every job fails instantly with GitHub's billing error. CI was slimmed + path-filtered (commit `a865b8a`,
proven: post-fix auto-sync pushes create no runs) and the duplicate `tests.yml` deleted; the matrix is now
4 legs (3 Ubuntu + 1 Windows py3.12), not 9. King waits for the monthly quota reset, then one click of the
new "Run workflow" button verifies the Windows fix. Full RCA: [[reference-ci-billing-outage-2026-07-17]].
(Evidence was pulled via the GitHub API using the stored KD-Brain git credential — `gh` remains
unauthenticated, and that turned out not to block anything.)
**Still open, unchanged:** the sync-robot alert gap above — not touched this session either.

## Update (2026-07-31): the alert gap is CLOSED — sync WARNs now ping King's phone
`sync_brain.ps1` routes its three sync-critical WARNs (pull conflict · stuck phone branch · push failed)
through a `Warn` function that POSTs to the ntfy channel (same one as the Payhip sale alerts; canonical
topic in `tools/push_kd.py`), throttled to **once per unique problem per day** via
`~\.kd_brain_sync_alerted.txt` so a stuck branch = 1 reminder/day, never a ping every 15 min. Alert
failure is never fatal to the sync itself (try/catch → log NOTE). DCIM-refresh WARNs stay log-only by
choice (non-blocking, avoids alert fatigue). **Proven live:** full cycle synced OK with the new script,
test ping received on the phone, duplicate call throttled (state file shows exactly one entry).
Context: closed the same night a **second demonstration of this gap** was found — the 07-14 phone branch
(`claude/idea-brainstorming-2btvht`, the scavenge-proven-assets rule) sat stuck for 17 days with the robot
warning into the unread log every 15 min; it was hand-merged, pushed, and the rule is live in
MEMORY.md + RULES_INDEX.md.

Related: [[feedback-elevated-state-pattern]] · [[project-24-7-engine]] · [[reference-ci-billing-outage-2026-07-17]].
