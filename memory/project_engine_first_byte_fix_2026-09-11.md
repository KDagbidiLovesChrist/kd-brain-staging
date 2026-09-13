---
name: project-engine-first-byte-fix-2026-09-11
description: "R2 (11 Sep) found the engine dropped a brief whenever the local model took over 5 min to start answering; root-caused to Node's hidden 300 s headersTimeout, fixed test-first (engine d65685f), live proven. Plus four pre-existing issues found on the way."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T13:56:47.141Z
---

# The engine's 5-minute cliff, found in R2 and fixed (11 Sep 2026)

**Status:** fixed, committed and pushed as engine `d65685f` on `phase-1-logos-os`. The engine was
restarted on the fix at 14:10:47. The R2 rerun of both mic-test briefs is recorded at the end.

King approved Claude making this one engine change. Engine code is Codex's lane under the 10 Sep
rule ([[feedback_agent_lanes_one_working_tree]]).

## What R2 found
Both mic-test briefs were pre-verified by text into kd-faceless, with actor `preverify`.

| Brief | Mission | Result |
|---|---|---|
| Hook Engine (the refusal) | `5d875a3d` | **`not_ready`**, naming all four negatives, in 370 s |
| The Buka (the pass) | `d3f54eb8` | **no verdict**: `station.finished {ok:false, message:"fetch failed"}` at 5 m 12 s |

Mission `d3f54eb8` is left in the live DB as a draft, as the record of the defect.

## Root cause, proven
Ollama sends nothing, not even response headers, until it has loaded the model and read the
whole prompt. Its log recorded the failed call as HTTP 500, which it can only do before headers
go out.
- The Buka call was the first after the reboot, with a cold model, on a machine busy with the
  13:00 jobs.
- The prompt (King's method file plus the brief, about 2,700 tokens) was read at about 8.5
  tokens a second. The Hook Engine call, warm, ran at about 17.
- That was over 300 s of silence, and Node's built-in fetch (undici) drops a request whose
  response has not started within 300 s (`UND_ERR_HEADERS_TIMEOUT`), whatever
  `LOGOS_LOCAL_TIMEOUT_MS` (10 min) says.
- The 22 Aug streaming fix and the 6 Sep serialising fix both assumed "the first byte arrives in
  seconds". A cold or busy prefill breaks that assumption even with one call in flight.

## The fix
`engine/src/lib/local-transport.ts`: node:http is built in, adds no dependency and has no timeout
of its own. `ai-gateway.ts` `runLocal` now calls it, so the AbortSignal is the only limit. There
is an explicit test hook, `setLocalTransportForTests`.

## Proof, test first
| Check | Before the fix | After the fix |
|---|---|---|
| `scripts/prove-local-first-byte.ts`, 305 s of silence from a fake Ollama | threw at 303,610 ms, `fetch failed`, `UND_ERR_HEADERS_TIMEOUT` | answered at 305,041 ms |
| `prove-local-only`, a real cold `qwen3:8b` call | n/a | PASS in **309,215 ms**; the old code would have died at 300 s. Loopback only |

- The prove-local-only fence now wraps the new transport, and fails if it saw no call. Pointed at
  10.255.255.1, it fails at step 3 as it must.
- `prove-builder-gate` (its fakes moved to the new hook) and `prove-local-concurrency` pass.
  `tsc --noEmit` is clean.
- Every prover ran on a database COPY. The live `v0.sqlite3` stayed at 125 audit rows, with 0
  prover rows.
- A preset `DATABASE_URL` wins over `process.loadEnvFile(".env")`, which was tested. That is how
  any prover can be kept off the live DB.

## Found on the way, NOT fixed (King's calls)
1. **`prove-local-only` fails its step 2 on the live `.env`.** `ANTHROPIC_API_KEY`, the cloud
   lane key (fingerprint `4ef355df8a17`, `engine/.env:16`), is in it, and the 15 Aug V0 rule says
   the local engine must not carry it. It has been failing whenever it reads that file.
2. **Notes silently dropped.** `brain.ts` gives LOGOI 8 s. A cold LOGOI took longer, so the Buka
   brief ran with NO notes, and no audit row says so.
3. **Near the context limit.** With notes the prompt was 3,677 of Ollama's 4,096 tokens. Growing
   notes will be truncated.
4. **Slow for a live mic test.** A warm brief takes about 6 minutes on this CPU. King should know
   before he speaks.

## R2 rerun on the fixed engine (14:11 to 14:17)
- **The Buka brief now gets its verdict: `build`.**
  - Mission `3a05b2e8`, angle "Bring Nigerian flavors to Dublin's doorstep".
  - The model answered in 226 s, and the verdict was saved at 13:15:04 UTC.
  - It had no notes again: no `brain.consulted` row, which is issue 2 above.
- **Then a SECOND defect killed the engine:** `Error: database is locked` at `db.ts:790`, from
  `standalone-server.ts:1327`.
  - `db.ts` opens SQLite with no busy timeout (journal mode `delete`). Another process holding a
    read lock at the moment of a write makes the write fail at once. The other reader was most
    likely Claude's own pre-verify script, which polled every 2 s; the deck may read too.
  - `startStation` writes `station.finished` inside `void run().then(...)`, so that throw is an
    unhandled rejection, and Node exits. **One failed log write takes the whole engine down.**
  - King's live mic test could hit the same thing, with the deck reading while the engine
    writes.
- **The Hook Engine brief was not re-sent.** `POST /command` got `ECONNRESET` because the engine
  was already dead.
- **The engine was restarted** through `KD_Engine_AtLogon` at 14:17:34, and the pre-verify script
  was stopped.
- **King ruled: hand it to Codex** (his 10 Sep lane rule). The brief is
  `_ops/briefs/CODEX_engine_db_lock_2026-09-11.md`. Its fix:
  - a busy timeout when the DB opens;
  - a failed audit write in `startStation` that can never kill the engine;

  both test-first on a throwaway DB, with no WAL switch.
- **Codex fixed it: engine `a0c2061`, 14:44**, pushed to the `github` remote. Claude verified
  every step from Codex's own session log (`~\.codex\sessions\2026\09\11\rollout-...01a090ae...`)
  and the repo.
  - **RED** on the old code, `scripts/prove-db-lock.ts`, 1 passed and 4 failed. A 1 s write lock
    gave "database is locked" in 1 ms, and the resolve, reject and relay station paths all killed
    the server. The journal-mode check passed.
  - **GREEN**, 8 passed and 0 failed.
  - **The fix:** `PRAGMA busy_timeout = 5000` in `getDb()`, plus a `.catch` on `startStation`'s
    promise chain that sends a failed terminal audit write to stderr.
  - **Regressions:** `prove-async-runs` 10/0, `prove-local-concurrency` PASS,
    `prove-local-first-byte` PASS (305,054 ms). `tsc` is clean. Every test ran on a database
    copy, and there were 0 live rows since Codex started. No WAL switch, no keys touched, and
    it stayed in `engine/`.
  - **The commit** holds exactly 3 files. Codex asked King's permission for the restart.
  - **Its new comment** says the open start row is closed at the next restart. That is true:
    `reconcileOrphanedStations` wrote `station.abandoned` for the crashed Buka mission at the
    14:17:35 restart.
  - **The engine restarted on the fix** through `KD_Engine_AtLogon` at 14:45:14, with the deck
    untouched.
- **The final R2 run of both briefs** on the doubly fixed engine is recorded below.

## R2 PASSED (14:45 to 14:56, engine pid 16920 on `a0c2061`)

| Brief | Mission | Verdict | Time | Full chain |
|---|---|---|---|---|
| The Buka | `e765e75f` | **`build`**. Angle: "Help local Dubliners find The Buka online". Audience: local customers in Dublin looking for Nigerian food | 418 s (the model 415 s, 3,669 tokens) | mission.created, station.started, brain.consulted (3 files), gateway.call, gateway.response, station.finished |
| The Hook Engine | `b43a09ff` | **`not_ready`**. Audience: "No audience, no traffic, no email list and no distribution". All four named, and the reason quotes the founder's own words | 177 s | the same, all six |

- **The Buka run proves the first fix mattered.** The model spent about 376 s reading the prompt
  before its first token, since only 39 s of the 415 s was generation. The old fetch path would
  have died at 300 s.
- **The engine stayed up throughout**, while the pre-verify script polled the DB every 2 s. That
  is Codex's lock fix, proven live.
- **Tell King before his mic test:** a spoken brief can take up to about 7 minutes on this CPU.
- **Next:** R3, King's own mic test.
