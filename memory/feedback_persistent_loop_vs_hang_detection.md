---
name: feedback_persistent_loop_vs_hang_detection
description: "Hang detection (a task 'Running' too long is killed via schtasks /end) must never apply uniformly to every registered loop: a long-lived, always-on process shows its scheduled task as continuously Running by design, and treating that as a hang killed King's own progress_board.py loop for real, 5 Sep, ~78 minutes of silent outage before it was caught."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-05T10:28:00.309Z
---

Real hang-detection code, built the same night for Stage 3.7's concurrent-loop drill, was
deployed live via the already-running `KD_Loop_Supervise` scheduled task (every 5 min) before
its one real blind spot was found: it had no way to distinguish a ONE-SHOT task that started
and got stuck (a real hang) from a task whose own scheduled entry launches a LONG-LIVED,
always-on process by design (never a hang, "Running" forever is its correct, healthy state).

`progress_board.py --loop 60` is exactly the second kind: its scheduled task fires once at
logon and the script itself loops internally forever. Windows Task Scheduler correctly shows
that task as "Running" continuously for as long as the process lives, which could be hours or
days. The hang-detection code, applying the same "Running past its own stale_limit_h = hang"
rule to every loop in the registry, treated that entirely normal state as a stuck task and
genuinely killed it via `schtasks /end`. Confirmed after the fact in the real
`KD_LOOP_LEDGER.md`: turn 20, `progress_board | supervisor | ... | FAILED | 3899` (3899
seconds, ~65 minutes of "running", exactly matching progress_board's own 1-hour stale_limit_h
being crossed). The board went stale for about 78 minutes before this was noticed, while
investigating an unrelated failing test.

**Why:** because hang detection was written and tested (real tests, a real drill) against
one-shot tasks only (the drill's own `hang_drill`, a task that sleeps once and should finish),
and the registry it ran against in production also contains a genuinely different shape of
loop (a persistent background process) that nobody had reason to think about until it broke
for real. The bug was real, live, and self-repeating (the scheduled task would have kept
re-triggering it every 5 minutes) until the fix landed on disk.

**How to apply:** before adding any "kill a task that's been Running too long" mechanism to a
registry of scheduled things, check whether EVERY entry in that registry is genuinely meant to
run-and-exit each cycle. If even one entry is a long-lived, always-on process (check its real
live Task Scheduler state: does it ever show anything other than "Running" once started?),
that entry needs an explicit opt-out (here: `LoopDef.persistent = True`), not an assumption
that the same rule fits everything the registry holds. Verify by checking each entry's REAL
live state (`Get-ScheduledTask | Select State`), not by reading its registration and assuming.

See [[project_kd_robot_three_nodes_2026-08-29]] for the full incident record and the fix.
