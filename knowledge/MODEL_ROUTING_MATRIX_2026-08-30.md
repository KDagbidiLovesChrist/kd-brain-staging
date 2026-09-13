# Model Routing Matrix · 11-Metric Scoring
> **HISTORY, NOT LIVE.** Folded into `tools/logos_policy.py` (data in `tools/logos_lanes.py`) on 3 Sep 2026 per King's ruling 10.3; the governor's lanes are the one routing table. Read `commands/model-route.md` for the live rules. This file is kept as the record of how the 30 Aug scores were reached.
> **Purpose:** Decision protocol for routing tasks (Personal/Business/Legal) to Claude, Gemini, or GPT
> **Created:** 2026-08-30 · **Owner:** King David Agbidi

---

## 1. The 11 Metrics (1-10 scale, 10=best)

| Metric | Claude | Gemini | GPT | Notes |
|--------|--------|--------|-----|-------|
| **1. Cost/Token** | 6 | 9 | 7 | Gemini free tier available; Claude mid-range; GPT premium |
| **2. Speed/Latency** | 6 | 9 | 7 | Gemini fastest; Claude medium; GPT medium-fast |
| **3. Quality/Accuracy** | 10 | 7 | 8 | Claude best reasoning; GPT strong code; Gemini good gen |
| **4. Data Safety** | 8 | 5 | 6 | Claude best (no training by default); others have concerns |
| **5. Capability Fit** | 7 | 9 | 9 | Gemini/GPT excel at multimodal; Claude reasoning |
| **6. Quota/Rate Limits** | 7 | 9 | 7 | Gemini high free tier; Claude tier-dependent; GPT tier-dep |
| **7. Consistency** | 9 | 6 | 8 | Claude most predictable; GPT solid; Gemini variable |
| **8. Brain Integration** | 10 | 5 | 7 | Claude native to this brain; GPT tools existing; Gemini new |
| **9. Customization** | 10 | 6 | 8 | Claude system prompts best; GPT good; Gemini weaker |
| **10. Guardrails (Faith)** | 9 | 5 | 4 | Claude respectful of worldview; Gemini filters; GPT corporate |
| **11. Context Window** | 8 | 10 | 9 | Gemini 1M+; GPT 128k+; Claude 200k (Sonnet) / 100k (Haiku) |

---

## 2. Aggregate Scores by Model

| Model | Total | Avg | Strength | Weakness |
|-------|-------|-----|----------|----------|
| **Claude** | 82/110 | 7.5 | Quality, safety, faith, integration, consistency | Cost, speed, context window |
| **Gemini** | 76/110 | 6.9 | Cost, speed, capability, context window | Consistency, safety, guardrails |
| **GPT** | 76/110 | 6.9 | Quality, capability, consistency, context | Cost, guardrails, safety |

---

## 3. Routing Rules by Domain + Task Type

### 🔵 PERSONAL (Brain, Faith, Research)
Goal: **Quality + safety + guardrails**. Budget: unlimited (King's own work).

| Task Type | Best | Fallback | Rationale |
|-----------|------|----------|-----------|
| Reasoning / problem-solving | **Claude** | Gemini | Quality #1, guardrails essential |
| Brainstorm / ideation | **Claude** | Gemini | Consistency matters |
| Faith / theology study | **Claude** | (skip others) | Worldview alignment critical |
| Research synthesis | **Claude** | GPT | Accuracy over speed |
| Vision analysis (rare) | **Gemini** | GPT | Claude lacks multimodal |
| Writing / reflection | **Claude** | Gemini | Tone control, consistency |

**Personal Rule: Claude first. Cost is not the constraint.**

---

### 💼 BUSINESS (Klarnow, Logos, Content, Money)
Goal: **Speed + cost + capability**. Budget: watch spend, but invest if ROI.

| Task Type | Best | Fallback | Rationale |
|-----------|------|----------|-----------|
| Code generation | **GPT** | Claude | Fastest, strong code |
| Copywriting / sales | **Gemini** | Claude | Fast iterations, cheap |
| Data processing | **Gemini** | GPT | Speed matters, cost-effective |
| Mission grading (Logos) | **Claude** | Gemini | Quality/consistency critical |
| Video analysis | **Gemini** | Claude | Capability fit |
| Customer comms (legal-ish) | **Claude** | GPT | Safety margin needed |

**Business Rule: Gemini first for speed/cost. Claude for high-stakes (grading, contracts).**

---

### ⚖️ LEGAL (IP, Contracts, Compliance)
Goal: **Safety + accuracy + guardrails**. Budget: pay for quality.

| Task Type | Best | Fallback | Rationale |
|-----------|------|----------|-----------|
| Contract review | **Claude** | (avoid Gemini/GPT) | Accuracy non-negotiable, guardrails |
| IP / patent text | **Claude** | (avoid) | Legal precision required |
| Compliance research | **Claude** | GPT | Safety margin essential |
| Terms of service analysis | **Claude** | GPT | Gotchas matter |

**Legal Rule: Claude only. No shortcuts. Safety > cost.**

---

## 4. Priority Hierarchy

When choosing a model, apply **in order:**

1. **Domain override** (Legal always → Claude, no exception)
2. **Capability fit** (If only one model can do it, use that)
3. **Safety first** (If risk involved, escalate to Claude)
4. **Cost / speed** (Personal = quality first; Business = balance; Legal = safety first)
5. **Fallback chain** (If primary unavailable, use secondary)
6. **Ollama local** (If quota hit and task is reasoning, use qwen3:8b)

---

## 5. Real-World Routing Examples

**Example 1: "Write a landing page for Klarnow"**
- Domain: Business
- Task: Copywriting
- Route: **Gemini** (fast, cheap, good enough for copy)
- Fallback: Claude (if Gemini output poor)

**Example 2: "Review the IP agreement for Logos"**
- Domain: Legal
- Task: Contract review
- Route: **Claude** (non-negotiable)
- Fallback: None (escalate to lawyer if Claude unavailable)

**Example 3: "Help me think through the kenosis descent in Theosis"**
- Domain: Personal
- Task: Theology reasoning
- Route: **Claude** (faith + quality)
- Fallback: None (theology not outsourced)

**Example 4: "Analyze this customer video for Klarnow"**
- Domain: Business
- Task: Video analysis
- Route: **Gemini** (capability fit + cost)
- Fallback: Claude (if Gemini can't process)

**Example 5: "I'm out of Claude quota, need to brainstorm product ideas"**
- Domain: Personal
- Task: Ideation
- Route: **Ollama qwen3:8b** (local, free)
- Fallback: Gemini (free tier)

---

## 6. Integration Points

**Where this lives:**
- **Reference file** (this file): `knowledge/MODEL_ROUTING_MATRIX_2026-08-30.md`
- **Router tool** (TBD): `tools/model_router.py` (scores task → best model)
- **Aide integration** (TBD): `/aide` checks domain + task, suggests best model
- **Session log** (TBD): `memory/MODEL_ROUTING_LOG_2026-08-30.md` (track spend per model)

---

## 7. Update Log

| Date | Change | Owner |
|------|--------|-------|
| 2026-08-30 | Initial matrix created (11 metrics, 3 models) | Claude |
| 2026-09-03 | Domain rules folded into `tools/logos_policy.py` (data in `tools/logos_lanes.py`) per King's ruling 10.3; this file is history | Claude |
