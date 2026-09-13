---
name: project-engine-home-tenant-isolation-2026-09-11
description: "R5.3 done 11 Sep (engine b97e2aa): kd-faceless listed first so Talk and /command default to it; every prover gets its own throwaway database and ledger, and the engine refuses the live file during a test run. Exposed: prove-grounding was grading against the wrong brief, and the fabrication checker let 'six months' through once."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T18:58:58.100Z
---

# Home tenant first, and provers kept out of the live database (R5.3, 11 Sep 2026)

**Why:** Talk opened on the prover tenant `prove-local-concurrency`, so a spoken brief could land
there. Tenants were listed oldest first and every default (Talk `tenants[0]`, the /command select's
first option, /command's fallback) takes the head of the list; the prover tenant (9 Sep) was older
than kd-faceless (re-seeded 11 Sep). And provers wrote into the LIVE `v0.sqlite3`:
`run-provers.ts` handed them the laptop's environment, so `prove-local-concurrency` and
`prove-gateway-router` left 49 `gateway.response` rows there, 9 of them fakes.

**Built (engine `b97e2aa`, pushed):**
- `db.ts listTenantsWithCounts`: home tenant first (`LOGOS_HOME_TENANT`, default `kd-faceless`, ""
  means none, the same `??` rule as `LOGOS_BRAIN_TENANTS`). One change fixes all three defaults. A
  partner instance has no kd-faceless row, so its order is unchanged.
- `run-provers.ts`: seeds one throwaway database (default profile) and gives every prover its own
  copy plus its own spend ledger, marked `LOGOS_PROVER_RUN=1`.
- `db.ts getDb`: during a prover run it refuses `v0.sqlite3`, `klarnow.sqlite3`,
  `backupnode.sqlite3`, checked before the file is opened (opening creates it).
- `prove-grounding.ts` self-contained: it used kd-faceless's FIRST real mission as the brief for
  cases 2 and 3, which since the re-seed is the Buka brief, and wrote real-model rows into King's
  world. Now carries his 9 Aug Hook Engine brief verbatim (from the 30 Aug snapshot on D:) on its
  own fixture missions, and marks itself a prover run, so by hand against live it refuses.
- `prove-lanes.ts`: eight lanes by name, voice included (it still expected seven: a miss from the
  voice lane work earlier the same day).

**Proof:**
- `prove-home-tenant` red 4 failed, green 8/8. `prove-prover-isolation` red 4 failed (the stand-in
  "live" database grew 0 to 14 rows, 1 to 2 tenants), green 8/8. `tsc` clean.
- Full suite of 42 under the new runner: live database 143 rows, 2 tenants, 7 missions, ledger
  1,037 bytes, before and after. No temp folder left.
- Live after restart: `GET /api/world` lists `kd-faceless, prove-local-concurrency`.
- By hand, `prove-grounding` against .env: "Refusing to open v0.sqlite3 during a prover run",
  before any model call. Live unchanged.

**Failures left, each reproduced against a copy of live data (not caused here):**
`prove-cloud-branch` (spend gate refuses, no approval, no money spent), `prove-local-only`
(ANTHROPIC_API_KEY in engine/.env breaks the V0 local-only rule, already open),
`prove-live-providers` (opt-in, fails when unset).

**⚠️ FINDING for King, not fixed:** with the right brief, the fabrication checker (grounding,
local model, temperature-sampled) let the 10 Aug "six months" invention through once (case 2, 4
specifics checked, none flagged). On the old wrong brief this case only looked correct because
everything fails against the wrong brief. Known class (the 6 Sep flake was a false alarm on case 3),
but this is the dangerous direction: a missed invention.
- **Measured 11 Sep 19:34 to 19:45** (King: "measure first", then "Do what you want"): 5 runs of
  prove-grounding. Case 2 ("six months") missed in runs 2, 3, 5: **3 of 5, 4 of 6 counting the
  first**. Case 1 (Chopiva) caught 5 of 5. Case 3 (the honest output) never falsely flagged.
- **Root cause, measured (scratchpad `grounding_diag.ts`, 3 checks):** the model (llama3.2)
  LISTED "six months" every time. Twice labelled `invented`, and triage failed it. Once labelled
  `dropped`, quoted with the words reordered ("zero copies sold in six months" against the output's
  "has sold zero copies in six months"). triage's rule: a `dropped` claim only escalates if it is
  verbatim in the OUTPUT, else it is a note. Not verbatim, so a note, so a pass. **The miss is one
  deterministic rule in `triage`, not the model.**
- **FIXED by Codex, engine `e19ea89`** (brief `_ops/briefs/CODEX_grounding_dropped_rule_2026-09-11.md`,
  one `codex exec` pass, about 5 min): a `dropped` claim not verbatim in the output now runs the
  same new-specifics test as the invented branch (one shared helper, `anyInOutput`); if a specific
  the brief lacks is in the output, it FAILS as invented. Codex: red "dropped replay" FAIL, green 4
  new checks, prove-grounding 3 of 3 correct on the real model (153 s), tsc 0. **Claude re-ran it
  independently:** with the pre-fix grounding.ts the replay fails, with the fix all pass, tsc clean,
  tree matches the commit. Pushed (0 0); engine restarted 19:58, health check reads CURRENT.

**Left as is:** the 53 old prover rows (9 fakes) stay in the live log, which is add-only by design;
the WORKING light ignores prove-* tenants. His call if he wants them removed.
