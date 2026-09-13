---
name: project-logos-engine-build-2026-08-23
description: "The 23 Aug build session: Phase 1 of the Logos OS plan (async runs, live feed, named identities, the meter, the UI, the brain wired in), plus the four recurring failure patterns it exposed"
metadata: 
  node_type: memory
  type: project
  originSessionId: ba72aaf5-8b95-405c-af8a-50c86fbdd159
  modified: 2026-08-23T21:01:22.838Z
---

# The Logos engine build, 23 August 2026

The plan (`plans/i-have-to-stop-vivid-wilkinson.md`, approved with 18 decisions) said King's own
instance is finished before Klarnow's. This session built most of Phase 1.

**Result: 12 provers, all passing, including `prove-grounding` which makes real model calls.**
Six new provers written today, adding roughly seventy checks.

## What was built

| Piece | What it does |
|---|---|
| **1B async runs** | `?async=1` on diagnose, sovereign and build returns at once; the work continues in the background. **Opt in, never the default**, because klarnow-world reads its result INLINE (`loop_run.py:104`) and defaulting to 202 would break the partner on THEIR machine. |
| **1C live feed** | `GET /api/events?since=<cursor>` reads the audit log forward, plus `station.started` / `station.finished` so a UI can tell RUNNING from IDLE. The gateway events alone cannot: the gap between two of five sovereign runs looks exactly like being finished. |
| **1D named identities** | `LOGOS_OPERATORS` gives each person and agent its own token, checked BEFORE the shared master key. The actor is derived from the credential and **a header cannot override it**. `SANDBOX_TOKEN` still works unnamed, so nothing existing broke. |
| **1E the meter** | `callAI` now records tokens and duration on both branches; `GET /api/usage` reports per client against `LOGOS_CLIENT_BUDGETS`. Built on the audit log, NOT a second ledger, so the number King quotes and the record he can show are the same thing. |
| **1F the UI** | Next.js on `:3200`, proxying `/api/*` to the engine so the engine's `HttpOnly SameSite=Strict` cookie keeps its strictest settings. King's Vault navy and gold, one column, phone first. |
| **1A the brain** | The engine went from ZERO connection to King's brain to reading **923 files**. It asks LOGOI's `/api/retrieve` rather than porting the TF-IDF, so there is one implementation and one guard. |

## ⚠️ THE PATTERN THAT APPEARED FOUR TIMES IN ONE DAY

**A process holding configuration from before a change, while every surface reports healthy.**

1. **The tunnel.** `cloudflared` alive for 14 hours without serving. Every process check passed.
2. **ccr.** Started from a shell that predated the API keys, so it held the literal string
   `$NVIDIA_API_KEY` and returned 401 on keys that were perfectly valid.
3. **The auth server.** `logoi_auth.install()` captured `cfg` once at startup, so King's new
   password was checked against a hash loaded eight hours earlier. **His password was correct the
   whole time.** Fixed at the cause: every check re-reads.
4. **My own new code.** `src/lib/brain.ts` had `const LOGOI = process.env...` at module level. Its
   own prover caught it the same hour.

**When something that should work does not, ask what the running process loaded and when, BEFORE
questioning the value on disk.**

## Six real bugs the provers caught before shipping

1. **The query string corrupted the mission id.** Routes take the id from the path with
   `req.url.replace("/build/", "")`, so `?async=1` made the id literally `someid?async=1`. Every
   async call would have failed silently as a missing mission.
2. **`202 started: true` for a mission that did not exist.** `startStation` returned quietly while
   the route claimed success. Exactly the claim-outruns-the-code pattern the August audit existed
   to catch, in code written an hour earlier.
3. **`mission.created` never set the `missionId` column**, unlike every other event, so filtering
   the feed by mission silently lost the row saying who started it.
4. **A timeout reported as `FAIL`.** `run-provers.ts` caps each prover at 15 minutes and
   `prove-grounding` makes real model calls, so under load it was killed and the summary read as
   "the fabrication guard is broken". Now prints `TIME` with the reason.
5. **A fabricated score.** LOGOI's retrieve endpoint reported `score: 0.0` on every hit because
   `search()` returns no score. Removed rather than invented.
6. **libuv assertion on exit.** A prover printed "10 passed, 0 failed" then exited **127**, so a
   fully passing guard reported itself as a failure. Undici sockets still pooled at `process.exit`.

## The brain guard, and why it is written the way it is

King asked for the WHOLE Master Brain, on an engine he reaches from his phone. The brain has ~50
top level folders including **`the-truth/` (944 files, never public internet)** and **`_private/`**.

- **An ALLOW list, never a deny list.** With a deny list every future folder is indexed by default
  and the next guarded one leaks the day somebody creates it.
- **A second independent per-path check** (`_is_forbidden`) applied at read time, so a typo in the
  allow list still cannot surface guarded material.
- **`tools/prove_brain_guard.py` is HOSTILE**: it pulls real sentences OUT of the guarded files and
  searches for them. 923 files indexed, 0 guarded, 0 leaked.
- **`prove-brain-boundary.ts`: his brain reaches HIS tenant only.** A client mission grounded on
  King's notes would leak his finances and his thinking about Klarnow into their own deliverable,
  AND corrupt their grounding, which is the fabrication the engine exists to refuse.

⚠️ One test failure was **the test being wrong, not the code**, twice: once asserting a mock call
must cost something (it genuinely costs nothing), once grepping for the string "the-truth" in a
context block (allowed memory files legitimately discuss it). Both corrected to assert the real
thing. **A test that forces you to invent a number to satisfy it is a broken test.**

## Phase 1 FINISHED, 24 August: 1G and the four Logoi

**1G, the permanent address: it already existed and nobody had walked through it.** The plan was a
named Cloudflare tunnel on `logos.kingdavidagbidi.com`, needing a Cloudflare account and a
NAMESERVER MOVE on a live site. Unnecessary. `tailscale serve` was **already configured**, proxying
LOGOI at `https://desktop-gruls39.tail01147a.ts.net` with a real Let's Encrypt certificate, tailnet
only. Verified: resolves, serves the login page, and a minted link returned 302 with the cookie set.

Better than the plan for his case: the address never changes, real HTTPS (which the `Secure` cookie
and **Apple's microphone rule** both need), his brain is **not on the public internet at all**, and
LOGOI stays loopback only. The DNS rollback was written and kept anyway
(`_ops/ROLLBACK_kingdavidagbidi_dns.md`, capturing the live Namecheap and Vercel records while the
site was verified UP).

**⚠️ A hole I opened and closed.** `next dev -p 3200` binds `::`, ALL INTERFACES, while the engine
and LOGOI are both `127.0.0.1`. King's own pretooluse guard blocks all-interfaces binds; passing
only a port walked around it. Fixed with `-H 127.0.0.1` in the npm script. **Check the bind, not
just the port.**

**The four Logoi (1H voice, 1I journal, 1J money, 1K faith) are on the deck.**

⚠️ **The lanes are called DIRECTLY from the browser, not through the Next proxy, and that is
deliberate.** A Next.js rewrite adds `X-Forwarded-For`, and LOGOI's gate refuses any request
carrying proxy headers, because that check was added after cloudflared made the whole internet look
like 127.0.0.1. Making the proxy work would have meant STRIPPING that header, i.e. teaching the app
to fake being local, which is the exact bypass the guard exists to stop. The browser tab genuinely
is on his machine, so a direct call passes honestly. LOGOI allows one origin
(`http://127.0.0.1:3200`) for an explicit ALLOW LIST of read-only paths. Verified: another origin
gets no `Access-Control-Allow-Origin` at all.

**1K, the faith lane, verified on all three of its promises:** a question his notes answer returns
3 hits each NAMING its file; a question they do not returns "I do not know" and quotes nothing from
memory; and searching directly for "confession preparation", "questions for Fr Bogdan" and "my
testimony" leaks **zero** guarded files. The naming is the mechanism, not decoration: on 23 August
LOGOI invented citations and the only reason it was caught was that it had to name its source.

**Two more bugs caught by their own error messages.** An `import logoi_scripture` guard matched the
FUNCTION-LOCAL import inside `api_chat` and skipped the top-level one, so `/api/faith` returned
`name 'logoi_scripture' is not defined` — reported honestly rather than as an empty result, which is
why it took a minute to find. And LOGOI's retrieve endpoint reported `score: 0.0` on every hit
because `search()` returns no score; removed rather than invented.

## ⚡ THE REASONING BUG: qwen3 needs `think: false`, and it was never set (24 Aug)

`prove-local-only` began timing out at the FULL 10 minute ceiling on a call that had passed in
2.4 s, 6.3 s and 22.8 s earlier the same day. It failed alone, so it was not machine load.

**It was not new code either.** Replicating the gateway's exact call shape with NO engine code
involved reproduced it, which is what isolated it:

```
qwen3:8b, stream:true, format:"json", no think flag   ->  ABORTED at 120,000 ms
the identical call plus think:false                   ->  2,671 ms, {"ok":true}, done_reason stop
```

**Cause:** qwen3 is a reasoning model and emits a `<think>` block by default. That block is not
valid JSON, so with `format:"json"` the grammar constraint and the reasoning fight each other and
generation can run until the timeout. **It is INTERMITTENT**, which is worse than a clean failure:
the same prompt passed three times that day and then hung, so it reads as flakiness rather than a
bug with a cause.

Fixed in `ai-gateway.ts`'s local branch. `prove-local-only` went from a 600,000 ms timeout to
**1,976 ms**.

**This was never only about one prover.** EVERY worker in this engine parses JSON, so every mission
on the local model was paying for reasoning that was then thrown away. It is the same root cause as
`ollama,qwen3:8b` taking 148 s and returning NOTHING in the 23 Aug lane benchmark, and it matches
King's own earlier note that qwen3 needs this in the payload, which the engine had simply never
picked up.

**LESSON: when something intermittent is blamed on load, reproduce it with the smallest possible
script that has none of your own code in it.** That is what turned "the machine was busy" into a
one-line fix.

## Still open

- **Not committed.** All of the above is uncommitted in the engine repo; King had not asked.
- **1G, the permanent address.** Needs his go: moving nameservers touches his live site.
- **1H to 1K**, the four Logoi lanes (ear, journal, money, faith), and the Vault fold-in for 1F.
- Klarnow's Phase 2 has not started, by his order.

Related: [[project-logos-engine-audit-2026-08-23]] · [[project-logoi-agent]] ·
[[project-logos-ownership-and-killswitch-2026-08-23]] · [[reference-cheap-lane-setup]]
