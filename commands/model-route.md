# /model-route · which model answers, from the one routing table
> **Trigger:** need to know which provider and model tier a lane or task routes to, and why
> **The table:** `tools/logos_policy.py` (the governor) with the data in `tools/logos_lanes.py`
> **Retired 3 Sep 2026 (King's ruling 10.3):** `tools/model_router.py` is now a thin shim over that table, kept so this command and its CLI keep working. `knowledge/MODEL_ROUTING_MATRIX_2026-08-30.md` is history.

---

## How to use

**Quick check (which provider and tier for this lane and task?):**
```bash
python tools/model_router.py <lane> <task>
```

**In a quota drought (go local where the lane allows it):**
```bash
python tools/model_router.py <lane> <task> --quota-drought
```

**From Python, the same answer the governor gives at run time:**
```python
import logos_policy
r = logos_policy.route_for("business", "code")     # Route(provider=openrouter, tier=gpt, ...)
s = logos_policy.seat_for("chair")                 # Route(provider=anthropic, tier=fable, does_work=False)
d, seats = logos_policy.council_for("your question")   # the governor decides the lane, then the rungs
```

---

## Lanes (one table, seven rows)

The governor's own four lanes and the three folded domains sit in the same table, `LANE_RULES`:

| Lane | Priority | Providers in order | Hard constraints |
|---|---|---|---|
| `faith` | local only | ollama `llama3.2:latest` | never leaves · no Claude rung · no OpenRouter (the 25 Aug ruling) |
| `cheap` | speed first | ollama `llama3.2:1b` | never leaves |
| `local` | quality first | ollama `qwen3:8b`, then `llama3.2:latest` | never leaves |
| `remote` | speed first | openrouter free tier, then nvidia NIM | the gate has the final say |
| `personal` | quality first | anthropic claude, then openrouter gemini, then openrouter gpt | none |
| `business` | speed first | openrouter gemini, then anthropic claude | none |
| `legal` | safety first | anthropic claude | Claude only · no OpenRouter · no local |

Providers are named where the call actually goes (`tools/logoi_envoy.py`): `anthropic` is the Console key direct, `openrouter` is the one key that carries GPT, Gemini, DeepSeek and the free tier, `nvidia` is NIM as a fallback, `ollama` is this laptop.

## Task rows (from the 30 Aug matrix, carried over)

### personal
- `reasoning` → claude, then gemini · `brainstorm` → claude, then gemini · `research` → claude, then gpt
- `vision` → gemini, then gpt (Claude lacks multimodal) · `writing` → claude, then gemini
- `theology` → redirects to the `faith` lane: local model only, never a Claude rung (the 30 Aug matrix said Claude; the governor's faith lane overrides it)

### business
- `code` → **gpt through openrouter**, then claude · `video` → **gemini through openrouter**, then claude
- `copywriting` → gemini, then claude · `data` → gemini, then gpt
- `grading` → claude, then gemini (Logos provers) · `customer_comms` → claude, then gpt

### legal
- `contracts`, `ip`, `compliance`, `tos` → claude, nothing else. The matrix's GPT fallback on compliance and tos is dropped: Claude only means Claude only. `--quota-drought` is ignored on this lane.

---

## The council rungs (ruling 33, 3 Sep 2026)

| Role | Provider | Tier | Does work | Sits |
|---|---|---|---|---|
| chair | anthropic | fable | no, thinks only | every sitting |
| check | anthropic | opus | no | only when a chair verdict fails a plain test |
| sonnet, haiku | anthropic | sonnet, haiku | yes | seats |
| deepseek, gpt (code), gemini (video) | openrouter | deepseek, gpt, gemini | yes | seats |
| local | ollama | qwen3:8b | yes | the volume, free |

Two ceilings, both refused past, the way the lane ceilings are: `SITTING_CEILING_TOKENS = 60000` per council decision, and `MONTHLY_ENVELOPE_USD = 20` for chair plus check on the Console key. `check_sitting()` and `check_envelope()` are the one way to ask.

---

## Output format (the CLI)

```
Domain:    business
Task:      code
Best:      gpt
Fallback:  claude
Rationale: Fastest, strong code; GPT for coding (ruling 30), through OpenRouter
Logged:    2026-09-03T12:00:00.000000Z
```

Decisions append to `~/.kd-brain/model_routing_log.jsonl`. With no arguments the CLI prints the lanes and the last 10 decisions.

---

## Never override
- Legal (Claude only, by the table's hard constraint)
- Faith and theology (local only, never a Claude rung, `tools/logos_policy.py` decide() rule 1)
- High stakes business (grading, customer comms) stays on Claude first

## Test
`tests/unit/test_logos_lanes.py`, in the real coverage gate: one test per rule, plus parity between this shim and the governor for every lane, task and drought flag.

---
**Last updated:** 2026-09-03 · folded into the governor per ruling 10.3 · first written 2026-08-30 by King David Agbidi
