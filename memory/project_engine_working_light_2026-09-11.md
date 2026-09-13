---
name: project-engine-working-light-2026-09-11
description: "R5.2 done 11 Sep: the engine's WORKING light in tools/logos_health.py now means a real model answered (a gateway.response, not mock, not a prove-* tenant). Refusals and voice replies no longer turn it green, and its minutes were an hour out all summer (fixed)."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T16:51:52.557Z
---

# The engine's WORKING light tells the truth (R5.2, 11 Sep 2026)

**Why:** `tools/logos_health.py` said the engine was WORKING if the newest audit event of ANY kind
was recent. A refusal is an event, so at 04:45 on 11 Sep it read "fresh" while the engine could
answer nothing. Live at 17:45 it said "working yes, last audit event 100 min ago".

**Two defects found, both proven on live data:**
1. **Any event counted.** The 17:45 "work" was a voice reply (not the engine's own work). The live
   log also held 9 FAKE answers from provers (`mock`, `env-chose-me`, `ollama:table-chose-me`),
   all in the `prove-local-concurrency` tenant; real answers are the 4 in `kd-faceless`.
2. **The minutes were an hour out all summer.** It read SQLite's UTC time with `mktime` minus
   `time.timezone`; on this laptop `time.timezone` is 0 while Ireland is on summer time. Measured:
   101 min by the old method, 41 by `calendar.timegm` (the truth).

**Fixed (brain, this commit):** `_utc_epoch` (timegm), `_engine_last_answer` (newest
`gateway.response` that is not mock and not in a `prove-*` tenant, plus the newest event of any
kind), `engine_working` (pure: None when no log, False when no real answer in 24 h, and the evidence
names what DID happen, so a refusal reads as a refusal). `check()` wired to it.

**Proof:** `tests/unit/test_logos_health.py` red 9 of 9, green 9 of 9 (refusal, spend refusal and
voice reply are not answers; mock and prover answers ignored; UTC in summer; no log is unknown; the
wiring through `check()`). Added to `tests/real_coverage_gate.sh` in the same commit: 1,239 passed,
67.78% (floor 50). Live after: "last real model answer 173 min ago" (the Buka brief, 14:55).

**Known, left:** the table trims WHY to 44 characters; when the light is NO the "NEEDS ATTENTION"
line prints the full reason. The prove-* rule depends on provers keeping that naming until R5.3
stops them writing into the live DB at all.
