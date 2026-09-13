---
name: project-voice-lane-2026-09-11
description: "King ruled a Gemini voice lane for an instant spoken reply (understanding only, 2 USD a month, only his spoken words, direct to Google). V1 (brain side) and V2 (engine side) built test-first; switched on and LIVE 17:04 (Gemini replied to the Buka brief in 3.9 s, 0.000228 USD) after two fixes (max_tokens 1000, thinking low); V3 is his own ears in Talk."
metadata: 
  node_type: memory
  type: project
  originSessionId: 2333f35b-611b-48ad-85ea-c72f5435ee93
  modified: 2026-09-11T16:05:13.292Z
---

# The voice lane: an instant spoken reply through Gemini (11 Sep 2026)

## Why
King, after R2: "3-7 mins is long I need instant listening and understanding and replies."
- **Listening is already instant.** Talk transcribes on the laptop (faster-whisper behind LOGOI
  `/api/listen`) and speaks a template "heard you" at once.
- **The slow part is the careful verdict.** qwen3:8b on this CPU reads about 3,700 tokens (his
  method plus notes plus the brief) at 10 to 30 tokens a second.
- **The real fix for speed** is the RTX 2070 backup node (LOGIC-C, "READY FOR PHASE 1" since
  27 Aug, 10 to 20x faster). The voice lane is the instant half.

## His rulings (11 Sep)
- **A Gemini lane for voice only.** Only his spoken words travel, direct to Google, never
  through OpenRouter. Never his method file and never his notes. His own tenant (kd-faceless)
  only, never client or medical tenants.
- **Understanding only.** It says back what it understood and never judges, so it cannot
  contradict the careful local verdict that follows.
- **Two US dollars a month**, and the lane stops there.
- **Codex builds the engine side** (his 10 Sep lane rule). Claude builds the brain side.

## Privacy facts, from Google's Gemini API terms (ai.google.dev/gemini-api/terms, read 11 Sep)
- **Encrypted in transit** (HTTPS), **not end to end**. Google reads it to answer it. The terms do
  not mention encryption at all.
- **Paid services:** prompts are not used to improve products, and are logged "for a limited
  period of time, solely for detecting and preventing violations" and for legal disclosures.
- **Unpaid services:** used to improve products, "human reviewers may read" them, and the terms
  say "Do not submit sensitive, confidential, or personal information."
- **EEA, UK and Switzerland:** the paid-services data terms apply even to unpaid quota. He is in
  Ireland.
- Data "may be stored transiently or cached in any country" where Google has facilities.
- **Billing, checked by King in AI Studio at 15:38 on 11 Sep:**
  - **PAID** ("Paid 1" tier, a prepaid billing account, one project "Gemini Project"), so the
    paid-services data terms apply.
  - **The credit balance is -EUR 0.44**, and a banner reads "A credit balance above $0 is required
    to resume service". **The Gemini API is paused until he tops up.**
  - EUR 25.00 was added on 9 Jun. Auto-reload is OFF, so the account stops when credit runs out:
    a second hard cap.
  - The monthly lines show -EUR 0.44 for each of Jul, Aug and Sep 1 to 11.
  - **V3 needs a top-up.** EUR 5 covers thousands of spoken briefs, and credit expires a year
    after purchase. His call.
  - **The "EUR 258" King remembered** was the Google Cloud free trial (US$300). The Cloud console
    Credits page (15:50) lists only "GCP Free Credit: Expired". It could never have paid for
    Gemini anyway: Google's Gemini billing docs say "Starting March 2026, Gemini API usage costs
    are specifically excluded from the $300 Google Cloud Free Trial program". Only the AI Studio
    prepay balance pays for Gemini.
- **Price:** `gemini-3.8-flash` 0.75 / 3.75 USD per million tokens, introductory until
  31 Dec 2026, then 1.50 / 7.50. A spoken brief costs well under a tenth of a cent.

## V1, the brain side (Claude): DONE and live, 11 Sep
- **`tools/logos_lanes.py`**
  - `GEMINI_DIRECT = "gemini"` matches the existing direct endpoint in
    `openrouter_call.PROVIDER_ENDPOINTS`; `GEMINI_FLASH = "gemini-3.8-flash"`.
  - Lane `voice`: `[(gemini, gemini-3.8-flash)]`, `speed_first`, constraints `no_openrouter`,
    `no_local` (so the engine's expandChain appends no slow local rung) and `gate_first`.
  - `VOICE_SYSTEM_PROMPT` (the ONE instruction that travels), `VOICE_MONTHLY_USD = 2.0`,
    `VOICE_MAX_TOKENS = 120`, `check_voice_month()`.
  - A `voice` block in `as_dict()`. The existing `ceilings` shape is untouched.
- **`tools/logoi_gate.py`:** `check_voice(text, system_prompt)` accepts ONLY the voice
  instruction (even when LOGOI has other prompts registered), then runs every existing gate rule.
- **`tools/ollama_gui.py`:** `POST /api/gate/voice`, loopback only; `{text, system_prompt}` in,
  `{allowed, reason}` out.
- **`_ops/logos_lanes.json`** regenerated: lanes now include `voice`, and the direct `gemini`
  endpoint is present.

**Proof:**
- `tests/unit/test_voice_lane.py`, 14 tests: RED 14 of 14 before the code, GREEN 14 of 14 after.
- With `test_logos_lanes.py` (152) and the two gate test files: 219 passed.
- The coverage gate: 1,230 passed, 68.5% (floor 50). The new file was added to
  `tests/real_coverage_gate.sh` in the same commit.
- **Live, after a LOGOI restart:**

  | Case | Result |
  |---|---|
  | the Buka brief | allowed |
  | "cap table" | refused, "stays on this machine" |
  | a wrong instruction | refused |
  | a proxied request | refused 401 by LOGOI's login gate, before reaching the door |

  The door's own 403 branch, for a logged-in remote caller, was not exercised live.

## Found, not fixed
- **`tools/logos_lanes.py` is 611 lines**, over the 500 limit. It was about 565 before V1 added
  46. Splitting it is its own job.
- **The engine does not set `LOGOS_LANES_JSON`**, so today it never reads the lanes table. V2 needs
  that one non-secret line in `engine/.env`.
- **The 15:30 auto-sync swept three V1 files** into `8944c784` before the real commit, the known
  habit.

## V2, the engine side: DONE by Codex, verified and live, 11 Sep 16:21
**Brief:** `_ops/briefs/CODEX_voice_lane_v2_2026-09-11.md`. At King's "you hand it to codex",
Claude launched it unattended: `codex exec --approve-for-me -C engine`, with his `gpt-6-astra`
at effort `high` unchanged. The brief was amended to stop at the local commit, with Claude doing
the push and the restart.

- **Engine `52beb16`, "Add gated voice acknowledgements with isolated proofs"** (11 files, +649).
  - Adds `src/lib/voice.ts`, the `/voice/reply` route, the `Talk.tsx` hook,
    `spentThisMonthForLane`, a deck proxy line, `logoiOrigin` exported, and the voice type.
  - **RED:** `voice.ts` missing. **GREEN:** `prove-voice-lane` 24 of 24, including the leak test
    (exactly the system prompt plus the transcript, no method, no notes), zero Google requests in
    every refusal case, and a hard cap `min(2, monthly_usd)`.
  - `prove-voice-route` 11 of 11 (auth, CSRF, client scope, malformed, unknown tenant, switch
    off). The regressions pass. `tsc` is clean.
- **Claude's review found one defect:** `prove-voice-route` refused to run outside Codex's
  isolated runner, so the engine's normal `npm test` showed a false FAIL (1 of 2). King ruled that
  Codex fixes it.
- **Engine `c127ddd`:** when started directly, the route prover hands itself to the runner with a
  minimal environment and a loop guard. Red 1 of 2, then green 2 of 2, re-run by Claude through
  `run-provers`, and 2 of 2 again.
- **Pushed** to the engine remote (`0 0`). **The engine was restarted** through
  `KD_Engine_AtLogon` at 16:20:54, with the deck untouched.
- **The live check with the switch OFF:** the real `POST /voice/reply` with the Buka brief returned
  HTTP 200 in 50 ms, `source: fallback`, "Your brief is with the engine.".
  - The live ledger stayed at 4 lines with 0 voice rows. The live audit stayed at 142 rows with 0
    voice rows. Nothing reached Google.
  - The live DB and ledger were also unchanged across every prover Claude re-ran.

## V2 design, as briefed (kept for reference)
A separate voice route that:
- sends only the transcript, **never** through `callAI` (whose `withMethod` adds his method to
  every call) and never with brain retrieval;
- asks LOGOI `/api/gate/voice` first and fails closed;
- calls the `voice` lane's rung through `model-providers.ts` with the exported instruction and
  max_tokens;
- enforces 2 USD a month against the spend ledger;
- is for kd-faceless only;
- speaks the reply where Talk plays `acknowledge()` today (`Talk.tsx:203-205`), falling back to
  that line on any failure.

It must be proven test-first with a fake Google server, plus a leak test that the method file and
notes are never in the outgoing body.

## Switched on, then two live faults found and fixed (11 Sep, 16:30 to 17:04)
King topped up Gemini and said "Yes, switch on": `LOGOS_VOICE_APPROVED=1` in `engine/.env`.
- **Fault 1, "provider truncated".** Gemini 3 counts its hidden thinking inside max_tokens, so
  120 was used up before any words. A direct probe at 1000 finished "stop" in 2.5 s (99 in, 39
  out). King: "Yes, do both". Brain `1ef06fd7` set `VOICE_MAX_TOKENS = 1000` (test asserts 1000);
  Codex wrote the engine half (ceiling 1000, `reasoningEffort` on the voice call only) but hit its
  ChatGPT plan limit (back 19:27) before committing. King: "Claude finishes it now". Claude ran red
  (fix parked: the 1000 happy path failed "voice configuration missing or invalid") and green
  (27 of 27, 2 of 2, tsc clean). Engine `b8c625e`, pushed.
- **Fault 2, "provider bad_request".** Google's own 400: "Thinking level MINIMAL is not supported
  for this model." Claude's brief had said minimal was allowed (from Google's general docs); wrong
  for gemini-3.8-flash. Probed once each: minimal 400, **low OK 1.9 s**, not sent OK 3.1 s. Red
  (prover expects "low", failed), green (27 of 27, 2 of 2, tsc clean). Engine `e7f9c10`, pushed.
- **LIVE, engine restarted 17:04:29:** the real `POST /voice/reply` with the Buka brief returned
  HTTP 200 in 3.9 s, `source: gemini`: "This is for The Buka, a Nigerian restaurant in Dublin,
  that wants to help more local customers discover them online. I am thinking it through properly
  now, ..." Ledger 4 to 5 lines, one voice row (gemini-3.8-flash, 99 in, 41 out, 0.000228 USD,
  priced). Audit one `voice.reply` row, metadata only (model, tokens, 3827 ms), no words.
- **Lesson:** a vendor's general docs are not the model's truth; probe the exact model once before
  briefing a parameter.

## V3 (King)
Speak a brief in Talk (pick kd-faceless) and hear the reply within seconds. The engine side is
proven live; only his own ears remain.
