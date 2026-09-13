---
name: project-real-module-test-coverage
description: "The brain's ~2,020 tests are a PATTERN suite (~1% real tools/ coverage); real import-and-run tests are being added tool by tool. Status + method."
metadata: 
  node_type: memory
  type: project
  originSessionId: 8e8d2c5b-aeef-4d11-bebd-2548c143419d
  modified: 2026-08-02T05:02:19.499Z
---

# Real-module test coverage (started 2026-07-10)

**The non-obvious truth:** the "~2,020 tests / 25% coverage" headline was theatre. Almost every phase test defined a throwaday function INSIDE the test (docstrings literally said "simulates X") and tested that, importing nothing from `tools/`. Real line coverage of `tools/` was ~1%. Verified independently; the repo's own `README.md` + `tests/README.md` now say the same.

**What's done (12 real modules, 220 tests, all green):** `goals.py` 100 · `send_file_smtp.py` 91 · `auto_handoff.py` 71 · `sync_claude_to_drive.py` 56 (asserts secrets like `.env.master`/`token.json` are NEVER uploaded) · `skill_finder.py` 56 · `seo_keywords.py` 51 · `context_check.py` 45 · `gen_router.py` 42 (money router: cheapest provider wins) · `produce_spec.py` 36 · `hook_harvest.py` 36 · `brain_link_scan.py` 26 · `edit_analyze.py` 17. The 3 fake tests (`test_produce_spec/edit_analyze/email`) were rewired to the real modules.

**Bug found + fixed via this work:** `auto_handoff.py` reused the `filename` variable (holding the output name `handoff_latest_auto.md`) as the loop var in the secret-warning loop, so a detected secret rerouted the recovery packet to the wrong file. Renamed the loop var; added a regression test. Proof that real tests catch real bugs.

**The method (repeatable):** extract the pure decision logic into importable functions; guard side effects (SMTP send, API calls, file writes) under `main()`/`__main__`; defer heavy credential/API imports INTO the functions that use them so the module imports on any machine. Then point a test at the real function, mock the network boundary. `goals.py` (already 100%) is the model.

**CI gate LIVE:** `.github/workflows/test-coverage.yml` has a blocking `real-coverage` job running `sh tests/real_coverage_gate.sh 40` (fails the build under 40%; combined is ~47%). Verified locally (YAML parses, gate exits 0 at 40 / 1 above ~47); the first real CI run confirms on next push.

**Env note:** system Python (3.12) had no pytest/hypothesis; installed `pytest`+`pytest-cov`+`pytest-mock` on 2026-07-10. Full pattern suite still needs `pip install -r requirements-test.txt`.

**Next tools:** remaining network fetchers, email senders, `auto_handoff.py`, `brain_link_scan.py`. Detail lives in `tests/README.md` (canonical). Related: [[feedback-no-overselling-verify-before-send]] · [[feedback-consensus-everything-rule]]

## Verified locally 2026-07-18 (Windows, Python 3.12) — fresh numbers, replaces stale claims above

- **Real-module gate: GREEN.** `sh tests/real_coverage_gate.sh 40` → 220 passed in ~10s, combined coverage **46.64%**. This also proves the real-module suite runs clean on Windows.
- **Full suite is now 701 tests, NOT ~2,020.** The spree cleanup shrank it; `tests/README.md` line 5 and master `CLAUDE.md` "Test Coverage" section still claim 2,020 and reference phase 16-30 files that no longer exist (Rule 19 contradiction, not yet fixed).
- **7-8 pattern tests FAIL on Windows** (varies per run = flaky): the `test_phase_15_performance_load.py` throughput family fails deterministically (`assert 0 > 200` — throughput computes as 0, Windows timer resolution), `test_phase_7_google_advanced.py::test_quota_exceeded_backoff` has a mock-construction bug, `test_phase_critical_5_file_io.py::test_version_history_pattern` flakes intermittently. **Consequence: the CI Windows legs will stay red even after the Actions quota resets** until these are fixed or pruned — separate from the 07-17 path-assertion fix.
- **Alerting gap confirmed in code:** `tools/sync_brain.ps1` line 78 handles a failed push with a log line only (`WARN: push failed` → `.kd_brain_sync.log`), no ntfy push. Same for the pull-conflict and not-on-main skips. This is the exact mechanism of the 6-day silent break; still open. See [[reference-sync-break-2026-07-16]].

## ✅ FIXED 2026-08-02 — the 3 Windows-only CI failures (King asked to check Gmail after a failure alert)

Gmail showed 4 consecutive "Run failed: Tests - main" emails (Jul 31→Aug 1), always the same shape: `Tests (windows-latest, py3.12)` failed with 3 annotations, every `ubuntu-latest` leg + the blocking `real-coverage` gate + `Code Quality` all green every time. So nothing merge-blocking was ever broken, but the Windows leg had been red for 4+ runs straight.

Root cause matched the 07-18 diagnosis above almost exactly — all Windows-clock-resolution bugs (`time.time()` reads exactly `0.0` for fast operations on Windows more often than on Linux):
- `tests/unit/test_phase_15_performance_load.py::TestThroughputBenchmarks` (4 tests) — `elapsed==0.0` forced `throughput=0` via an `else 0` fallback, failing every threshold assert deterministically. **Fixed:** floor `elapsed` at `1e-6` instead of substituting `0`.
- `tests/unit/test_phase_critical_5_file_io.py::test_version_history_pattern` — backup filenames keyed only on a timestamp string could collide within one clock tick, silently overwriting a prior backup. **Fixed:** include the loop index in the filename.
- **Bonus find during verification** (not in the original 3): `test_linear_scaling_latency` — tied `0.0` elapsed readings broke a strict-increase assertion between sizes. **Fixed:** switched `time.time()` → `time.perf_counter()` (the correct higher-resolution tool for timing short operations); re-ran 5x to confirm not a fluke.
- **Left alone (scope decision, King's call):** `test_quota_exceeded_backoff`'s bare-raise bug — real bug, but its module is gated by `pytest.importorskip("googleapiclient")` and CI's install step never installs that package on either OS, so it almost certainly *skips* in CI rather than being one of the 3 red annotations. Fixing it wouldn't change CI's red/green state. Also left: `tests/README.md`'s stale "9 jobs" claim (workflow is actually 4 jobs since macOS was dropped 2026-07-17).

Verified locally (79 passed in the 2 target files) and committed as `12e969d5`. **⚠️ This local-only verification was NOT sufficient** — the sync robot auto-pushed the commit ~15 min later, triggering a real CI run, which **still failed** on `windows-latest, py3.12` (1 annotation this time, not 3 — so 3 of the original 4 real culprits were fixed, one was missed). King reported the fresh failure; this time the actual failing test name was pulled straight from the GitHub Actions job log (now possible — the token fix below made API reads work) instead of relying on the 07-18 memory's list, which turned out to be incomplete/wrong for one instance:

```
FAILED tests/unit/test_phase_10_integration_workflows.py::TestWorkflowPerformance::test_email_send_throughput - assert 0 > 10
```

Same bug pattern (`elapsed if elapsed > 0 else 0` division guard) in a **file the original diagnosis never looked at**. Fixed the same way (floor at `1e-6`), then swept all of `tests/` for every remaining instance of the pattern (`grep` for `elapsed` used in a division or a strict lower-bound assert) to avoid a third round of whack-a-mole — confirmed this was the only one left. Full local suite: 700 passed, 1 failed (`test_quota_exceeded_backoff`, the already-known, CI-skipped, explicitly-out-of-scope one). Committed as `b95d591f`, pushed on King's ask.

**✅ CONFIRMED GREEN 2026-08-02 ~05:05 UTC** — pulled run `30731769063` (commit `b95d591f7508...`) directly from the Actions API: all 6 jobs `success`, including `Tests (windows-latest, py3.12)`. The Windows CI leg is fully fixed, not just locally-verified this time.

## 🩺 2026-08-02 06:xx — King asked for a full whole-brain health sweep after the CI fix

Ran a comprehensive read-only audit (no spend, no real sends) across the whole `.claude` brain, triggered by King saying "go through my whole brain and test... make sure everything is functioning." Full findings archived here since this doesn't fit any single existing project file. Method: direct checks (test suite, `schtasks`, log tails, deployment curls, `brain_confidence_test.py`, both GitHub Actions workflows) + 2 parallel background agents (credential liveness across `.env.master`, memory-link integrity).

**Confirmed healthy:** both GitHub Actions workflows green (`Tests` 6/6 jobs, `Sweep phone branches` 5/5 recent runs) · local suite 700 passed/1 known-skip · sync robots (`.claude` git, Notion mirror, Remote Control) all clean logs, zero errors · all 6 checked flagship Vercel deployments return 200 · repo clean (0 secrets ever committed, 3/3 backups, DCEO_BRAIN + the-truth intact, 62GB free) · MEMORY.md has 0 broken links out of 159 · 21/27 checkable `.env.master` keys LIVE.

**Real findings, ranked:**
1. **Supabase project fully deleted** (not paused) — `nvopnmjywqtiibiqqjlu.supabase.co` is NXDOMAIN on 2 independent resolvers. All 5 `SUPABASE_*` keys in `.env.master` are dead as a result. This is the backend for the old Relay CRM / VendorIQ / Lead Finder demo sites used in June Upwork proposals — those demos are currently broken if a prospect clicks through. Needs King's decision: resurrect the project or abandon those demos.
2. **✅ FIXED same session:** 4 scheduled tasks (`KD_Daily_Client_Scan`, `KD_Daily_Ingest`, `KD_Revenue_Radar`, `KD_Weekly_Audit`) were failing every trigger (error `2147946720`/`0x800710E0`) because `StartWhenAvailable=False` + laptop asleep at trigger time — a gap already flagged 07-31 but never fixed until now. Flipped `StartWhenAvailable` to `True` via PowerShell `Set-ScheduledTask` on all 4, verified `Ready` state + `StartWhenAvailable: True` on re-query. Missed runs will now catch up instead of silently skipping.
3. **Obsidian's Local REST API isn't listening** — `OBSIDIAN_API_KEY`/`OBSIDIAN_URL` both dead, connection refused on `127.0.0.1:27124`, despite 4 `Obsidian.exe` processes running. Breaks the `obsidian-cli`/`obsidian-bases` skills. Likely the Local REST API plugin needs re-enabling inside Obsidian. Not fixed (needs King at the app).
4. **Gmail app-password dead** (535 bad credentials) — already known from 08-01, already worked around (sends go via the OAuth `token.json` path, confirmed still working — used it live this session). Not urgent, just re-confirmed.
5. **Memory housekeeping (cosmetic, not fixed):** 28 files in `memory/` are true orphans — not linked from MEMORY.md, `RULES_INDEX.md`, or any wikilink (several look like superseded duplicates, e.g. `project_flagship_rebuild.md` / `project_galaxy_hub.md` / `project_hub_vision.md` sitting next to the live `project_hub_rebuild_v3.md` / `project_galaxy_site_references.md`). 2 files missing YAML frontmatter entirely (`project_dceo_brain_bedrock.md`, `reference_cheap_lane_setup.md` — both still linked and readable, just non-conformant). 1 dead `[[wikilink]]` (`[[project-muba-promo-video]]` points to an archived file, not live `memory/`).
6. **Minor heads-up, not fixed:** Cal.com's v1 API is fully decommissioned server-side (v2 still works, no evidence anything here still calls v1) · `OPENROUTER_API_KEY` and `VAPI_API_KEY` are blank in `.env.master` (may be intentionally unused — not flagged as breaking anything active).

**Next session:** King wants to connect Claude to more tools for work efficiency — discuss after he's back from work, ~18:30+ tonight (2026-08-02). See `project_upcoming_tasks.md` or the next handoff for the live pointer.

**Lesson for next time:** don't trust a stale memory's list of "which tests are broken" as complete — when GitHub API access is available, pull the actual job log (`GET /repos/{owner}/{repo}/actions/jobs/{job_id}/logs`) and grep for `FAILED`/`short test summary info` rather than pattern-matching against an old diagnosis. Local pytest runs on this machine and CI's `windows-latest` runner can behave identically for this bug class (both hit the same clock-resolution issue), so local reproduction is trustworthy for confirming a fix — it just needs to actually run the SAME test CI is failing on, which requires knowing its real name first.

**⚠️ Separate but adjacent finding, same investigation thread: a dead GitHub PAT was silently breaking `/find-skills` — AND `.git-credentials` turned out to be owned/rewritten by Windows Git Credential Manager, not a stable place to hand-fix.** At investigation time, both `.git-credentials` and `.env.master`'s `GITHUB_TOKEN=` held a token returning `401 Bad credentials`. The git sync robot was unaffected (authenticates via GCM, confirmed still pushing/pulling clean). `tools/skill_finder.py` (the engine behind `/find-skills`) reads the token straight from `.git-credentials` for its GitHub search leg — every query hit `401`, swallowed per-query, so `/find-skills` had been silently returning **zero GitHub results**. King generated a fresh classic PAT (`repo` scope), pasted it, verified live (200). Written into `.env.master` — that stuck (nothing else touches that file). Written into `.git-credentials` too, but **within ~15 min the next `sync_brain.ps1` git push overwrote it back** — git's credential subsystem propagates a successful auth back to *all* configured helpers (`credential.helper` = `manager` then `store`), so whatever GCM has cached wins the file every sync cycle regardless of manual edits. Turned out fine this time: GCM's own cached token (a `gho_...` device token) independently verified live (200) and the smoke test passed both before and after the revert (39 real GitHub results each time) — so `/find-skills` is confirmed working right now. **But the plaintext file itself is not a durable fix point.** If this breaks again, the actual fix is re-authenticating GCM (`git credential-manager github login` or equivalent), not hand-editing `.git-credentials` — any manual edit there will be silently clobbered within one sync cycle. `.env.master`'s `GITHUB_TOKEN=` is durable but isn't what `skill_finder.py` actually reads, so it's a correct value sitting unused by current code. Not fixed (flagged for later, low priority): `skill_finder.py`'s per-query error-swallowing doesn't distinguish "no token" from "bad token," so a future GCM-side regression would again fail silently with no visible error to King.
