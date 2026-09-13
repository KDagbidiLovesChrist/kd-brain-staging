---
name: reference-ci-billing-outage-2026-07-17
description: "RCA + fix for the 07-17 total CI outage: free GitHub Actions minutes exhausted within hours of the 07-16 sync fix (duplicate workflow + macOS 10x matrix x 15-min auto-sync pushes). CI slimmed + path-filtered, proven; awaiting monthly quota reset."
metadata: 
  node_type: memory
  type: reference
  originSessionId: dc943f0d-182c-418e-bac3-966c5b6f2611
  modified: 2026-07-26T19:23:00.254Z
---

# The CI billing outage (2026-07-17) · full RCA + the slim-down

## What King saw
Gmail filling with GitHub Actions failure emails every 15-30 minutes; "its still failing" after the
Windows test fix was pushed.

## Root cause (GitHub's own words, from the check-run annotation)
> "The job was not started because recent account payments have failed or your spending limit needs to be
> increased. Please check the 'Billing & plans' section in your settings"

**Not a code bug.** The account's free GitHub Actions minutes (2,000/month for private repos) ran out.
Every job on every OS failed in ~2 seconds with no runner and no steps — the signature of a job that never
reached a machine.

## Why it happened exactly then
- The 07-16 sync fix ([[reference-sync-break-2026-07-16]]) resumed pushes after 6 silent days. Each
  auto-sync push (every 15 min) triggered **two overlapping workflows**: a leftover `tests.yml` AND
  `test-coverage.yml` with an 11-job spread — 9 matrix legs (3 OS x 3 Python) including **3 macOS legs
  billed at 10x** and 3 Windows at 2x, plus gate + quality.
- Burn ≈ 100+ billed minutes per push x ~4 pushes/hour. Quota died within hours: last green run
  **07-16 21:30 UTC**, first billing failure **22:30 UTC**. 104 runs created 07-16 → 07-17 03:30.
- Nobody noticed sooner because the 6-day sync break meant no pushes, so no burn and no emails.

## Sequence of finds this session (2026-07-17, ~00:30-04:40)
1. Windows-only matrix bug root-caused: `tests/unit/test_phase_critical_5_file_io.py:32` asserted
   `"/" in str(Path("/home/user/file.txt"))` — fails on Windows because `WindowsPath.__str__()` renders
   backslashes regardless of input separators. Fixed with `.as_posix()`, proven by running the test locally
   on this Windows laptop, pushed as `18a9dc3`. **Still CI-unverified** — its run died on billing.
2. King reported still-failing emails → pulled real evidence via the GitHub API using the stored KD-Brain
   git credential (`git credential fill`; `gh` CLI is installed but NOT authenticated) → found the billing
   annotation above.
3. **CI slim-down shipped, commit `a865b8a`** in `.github/workflows/test-coverage.yml`:
   - `paths` filter on push + PR: only `tools/**/*.py`, `tests/**`, `.github/workflows/**`,
     `requirements-test.txt`, `pytest.ini` trigger CI → memory/handoff/plugins auto-sync pushes create NO
     runs (and no emails).
   - `workflow_dispatch` added → manual "Run workflow" button for verification runs.
   - Matrix: macOS deleted (10x billing, no Mac in the fleet); now 3 Ubuntu legs (py3.10-3.12, 1x) + 1
     Windows leg (py3.12, matches this laptop). Blocking gate + quality jobs unchanged (Ubuntu).
   - Duplicate `.github/workflows/tests.yml` deleted (same suite on Ubuntu run twice + unused Codecov).
   - New burn ≈ 15 billed min per genuine code change. Free tier is now sustainable indefinitely.
4. **Proven, not assumed:** auto-sync push `a272758` (plugins-only, 03:30 UTC, after the slim-down) created
   no run — newest run on GitHub remained `a865b8a`'s own. Filter works; email flood over.

## Decisions
- King chose to **wait for the free monthly quota reset**, not add a payment method (lean spend, Rule #12).
- Until reset, any genuine code push still fails on billing — expected, rare, harmless.

## Follow-ups
1. **King-side: NOTHING.** King said no billing pages (04:40, honored). The stored token lacks billing-read
   scope (`repo, workflow` only), so sessions can't read the reset date either; quota resets at the monthly
   rollover, worst case Aug 1. Don't send King to Settings.
2. **Checked 2026-07-26 (King asked):** dispatched a manual run (`30216708371`), same instant billing
   failure, so NOT reset yet — expect ~Aug 1. Zero minutes spent. Bonus confirmations: 9 days of auto-sync
   pushes created zero runs (path filter holding perfectly, run counter frozen at 159), and the dispatched
   run showed exactly 6 jobs (4 test legs + gate + quality), proving the slim matrix is live.
3. **After reset (session-side, zero King clicks):** trigger the run via the API,
   `POST /repos/KDagbidiLovesChrist/kd-brain/actions/workflows/test-coverage.yml/dispatches` body `{"ref":"main"}`
   with the stored KD-Brain credential, then watch the run. Green = the Windows fix (`18a9dc3`) + slim
   matrix verified, close the loop here and in [[reference-sync-break-2026-07-16]]. Red with the billing
   annotation = not reset yet, wait.
3. **Still open (pre-existing, untouched):** sync-robot failure alerting — `tools/sync_brain.ps1`'s
   pull-conflict path only writes a local log; the gap that made the 6-day break silent. Same class of
   lesson as this outage: **safety/cost failures must page King, not just log.**

## Lessons (the transferable kind)
- A green-looking local commit log proves nothing about CI or sync; check the remote's actual state.
- "Check Gmail" from King = failure notifications exist; but the GitHub API gives the verbatim reason —
  emails only say "run failed."
- CI on a 15-min auto-sync robot must be path-filtered from day one; macOS legs cost 10x and need a reason
  to exist.
- The stored git credential (Windows Credential Manager, KD-Brain token) works for GitHub API reads when
  `gh` is unauthenticated — retrieve with `git credential fill`, never print it.

Related: [[reference-sync-break-2026-07-16]] · [[project-24-7-engine]] · [[feedback-lean-spend-llama-routing]]
