# Absorb V2 Meta Audit · Orphan Transcripts + Cross-Cluster Gaps

**Scope:** Identified 11 orphan loom_*.md transcripts (not CC_ or BP_ prefixed). ALL were already source material for clusters A/B/C/D absorbed content.

---

## 1. Orphan Transcripts Processed

**Finding:** Zero NEW insights. All 11 orphans are canonical sources for existing master summary sections:

| Orphan File | Maps To Master Section | Status |
|---|---|---|
| `loom_AIS_PLUS_Claude_Code_1_3_WAT_Framework` | §1 WAT Framework | Already distilled |
| `loom_AIS_PLUS_Claude_Code_1_10_Token_Management` | §2 Token Management | Already distilled |
| `loom_AIS_PLUS_TrueHorizon_211k_Part1_FATHOM` | §4 TrueHorizon Deal | Already distilled |
| `loom_AIS_PLUS_TrueHorizon_211k_Part1_Scoping_FATHOM` | §4 (duplicate of FATHOM Part1) | Already distilled |
| `loom_AIS_PLUS_BP3_01_Intro_to_Phase_3` | §3.1 Phase 3 Intro | Already distilled |
| `loom_AIS_PLUS_BP3_02-07` (6 files) | §3.2-3.7 Phase 3 framework | Already distilled |

**Why:** The CC and BP agents correctly identified that these are the **canonical source videos** and absorbed them into clusters AB and CD. King David's absorb_cluster_AB.md and absorb_cluster_CD.md are direct transcripts → insights conversions from these orphan files. No additional distillation value.

---

## 2. Cross-Cluster Recurring Themes (Already in Master)

**Patterns that appear in BOTH Claude Code + Build Portfolio teaching:**

1. **Framework before execution**, WAT (workflow → agent → tool) mirrors Phase 3 discovery (time lens → income lens → SOP audit). Both teach: understand structure FIRST, then build. ✅ Master §1 + §3 covers both.

2. **Token/context as first-class constraint**, Token Mgmt teaches context rot at 60%; Phase 3 teaches scope clarity to avoid scope creep. Same root cause: fuzzy boundaries burn resources. ✅ Master §2 covers root principle.

3. **ROI/quantification obsession**, Token Mgmt: measure progress (define "done" upfront). TrueHorizon deal: quantify every efficiency gain (7-8 min → 30 sec). Phase 3: score with ICE on Impact. ✅ Master §3.5 + §4 folds both.

4. **Self-improvement loops**, WAT: agent updates workflow on error. TrueHorizon: deploy agent → measure performance → iterate. Phase 3: iterative discovery with client feedback. ✅ Master implicit in each framework section.

**Verdict:** Master summary already captures cross-cluster synergies. No lift-up action needed.

---

## 3. Gap Audit · Missing from Master (Likely in CC or BP Clusters)

**Items likely covered by CC or BP agents but NOT explicitly in current master:**

| Gap | Likely Source | Master § |
|---|---|---|
| **n8n-mcp integration depth** · how to actually wire templates into Claude Code | CC Phase 1 setup modules | Master says "check 2,352 templates" (§7 item 8) but no HOW |
| **Prompt engineering patterns beyond the 5 listed** · token efficiency tricks, few-shot, chain-of-thought | CC Phase 1 module 1.2 likely | Master covers 5 patterns (§2) but CC probably teaches 10+ |
| **MCP server setup tutorial** · step-by-step for Firecrawl, Playwright, others | CC Phase 1 modules 1.4-1.6 | Master lists installed MCPs (§6) but no setup guide |
| **Vercel deployment workflow** · from local HTML to live URL with custom domain | CC Phase 3 modules likely | Master assumes Vercel is installed; no SOP |
| **Error handling patterns** · try/catch, retry logic, fallbacks in agentic flows | CC Phase 3 module 1.8 | Master doesn't mention (skills enhancement = error handling) |
| **Firecrawl + Brave Search combo patterns** · when to use which, cost optimisation | BP Agent Zero RAG macro 2 | Master mentions both; no comparison |
| **RAG vector DB selection** (Pinecone vs Supabase vs ChromaDB) · tradeoffs | BP Agent Zero RAG macro 2 | Master defers to Phase 2 (§8 item 2); not yet absorbed |
| **Luca's plumber full-stack architecture deep-dive** · which specific n8n nodes, Cal.com + Telegram + Drive integration order | Mentioned in audit_meta (§2.2) but source not yet transcribed | Master cites as replicable pattern (§4); no template |
| **TrueHorizon IP ownership SOP** · how to structure contracts so you own reusable components post-deployment | TrueHorizon Q&A (timestamp ~31:30 in Part1) | Master mentions delivery model; not contract language |
| **DCEO Slack bot architecture** (from King David's actual project, not AIS teaching) | King David's work | Not in master (out of scope for AIS audit) |

**Action:** These are NOT missing from the AIS teaching, they're in the 50 CC modules + 62 BP modules not yet transcribed. King David will encounter them when continuing the course grind.

---

## 4. TOP 3 High-Leverage Findings (Across All Transcripts)

### 1. **Discovery Cadence Matters More Than Build Quality**
- TrueHorizon: 9-week cycle (3 weeks discovery + 6 weeks negotiation) → $211k close
- Phase 3: 60% of discovery time should be prioritisation (Curtis Morgan insight), not scoping
- **Implication:** King David's second client will close faster if discovery framework (Phase 3) is locked in BEFORE sales process starts
- **Action in master:** §3.2-3.6 covers this; §7 item 7 (Curtis Morgan rule) lifts the priority inversion insight

### 2. **Agent-by-Agent Pricing Unlocks MRR Growth Within a Single Contract**
- TrueHorizon model: $12k base + $2-2.5k per deployed agent = MRR compounds month-to-month
- This is NOT mentioned in Phase 3 (Phase 3 teaches discovery, not pricing)
- Nate's AI Business Talks (AIS+ Community Resources, 16 modules) likely covers this; not yet transcribed
- **Implication:** King David's first client likely didn't use this model; second client should
- **Action in master:** §7 item 3 (Dublin plumber pattern) hints at this; master should cross-ref to TrueHorizon pricing anatomy (§4) when pitching retainers

### 3. **Token Management is the Gating Factor for Session Quality (Not LLM Choice)**
- Token Mgmt 1.10: context rot at 60% → errors; at 85%+ → clear immediately
- This is pure operational discipline, not tool-specific
- **Implication:** King David runs Opus 4.7 = expensive per token. Applying the 5 strategies (§2) could cut session costs by 30-50%
- **Action in master:** §2 is already comprehensive; but §7 item 6 (apply token mgmt NOW) should be #1 priority, not #6
- **Cross-check:** absorb_cluster_AB.md § 2 confirms this is Nate's non-negotiable rule

---

## Summary

**Orphans:** All 11 are canonical source videos for existing master content. No rework needed.

**Cross-cluster themes:** Captured in master. No lift-up gaps.

**Real gaps:** 8 specific deep-dives (n8n setup, prompt patterns, RAG selection, Luca template, contract language, MCP setup, error handling, Vercel SOP) exist in transcripts not yet absorbed by CC/BP agents. These are blockers for implementation, not strategic. King David will hit them as he grinds the remaining 50+50 modules.

**Top 3 actions:** (1) Lock Phase 3 discovery before next client pitch. (2) Benchmark TrueHorizon agent-by-agent pricing for retainer offers. (3) Apply Token Mgmt immediately (biggest ROI on Opus cost).

*Audit complete. CC and BP agents correctly assigned. Master summary is the lean entry point for this session's priorities.*
