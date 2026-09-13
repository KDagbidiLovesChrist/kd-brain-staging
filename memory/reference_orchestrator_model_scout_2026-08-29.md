---
name: reference_orchestrator_model_scout_2026-08-29
description: "Scout sweep (29 Aug 2026) of models fit to be a main orchestrator agent and an education engine: DeepSeek V4-Flash, Llama 3.1 70B, Qwen QwQ-32B, Llama 3.1 8B, Mistral Large, with cost, reasoning, safety, immersion, and the sources"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 7fc8a4b4-550d-4060-9c39-02cf8febbd51
  modified: 2026-08-29T06:32:11.678Z
---

# Orchestrator and education models, scouted 29 Aug 2026

King's ask: *"find good engine models that are immersive like claude and safe to be main orchestra agents"*, for the KD Robot infrastructure and the education lane (the faceless curate pipeline, the Book of Creation). One scout agent, 14 tool calls, sources below. **Grade S** (a sweep with cited numbers, not yet re-verified by an independent second pass; prices are as of the day and must be re-checked before any spend, Rule 12).

| Model | Cost | Reasoning vs Claude | Safety | Orchestration fit | Immersion | Education |
|---|---|---|---|---|---|---|
| **DeepSeek V4-Flash** (cloud) | $0.14 in / $0.28 out per M tokens (Claude Sonnet $2 / $10, about 14x cheaper) | 8.5/10 (97.3% MATH-500, transparent chain of thought) | about 10% unsafe tier; refusals rose after safety RL | excellent: reasoning runs before action, so an approval gate sees the why | very good | excellent (teachable reasoning steps) |
| **Llama 3.1 70B** (local, open weights) | one-off GPU (two RTX 3090s, Q4_K_M, 38 to 40 GB VRAM); zero ongoing | 7/10 (88.6% MMLU, 89% HumanEval) | highest refusal rate, about 94% safe, fully auditable | very good (LangGraph plus approval gates in production, May 2026) | excellent (no latency, no key) | best in class (open weights, fine-tunable, a 405B teacher exists) |
| **Qwen QwQ-32B** (local or API) | free local; API about $0.19 in / $1.13 out | 8/10 (reasoning specialist) | good (35-hour autonomous runs, 1000+ tool calls, no fabrication spikes on governance tasks) | best for long multi-step education workflows | very good | excellent |
| **Llama 3.1 8B** (local, 8 GB VRAM) | free | 6.5/10 (73% MMLU) | good, about 94% safe | good | good | excellent for student machines |
| **Mistral Large 2512** (cloud) | roughly $0.45 to 0.60 in / $1.80 to 2.40 out (estimate) | 7/10 | mixed: 4.5% hallucination (Vectara) but 61.2% fabrication on governance tasks | good (262K context) | good | decent |

**Consensus pick for this brain:** DeepSeek V4-Flash for cheap orchestration and approval reasoning; Llama 3.1 70B local for research, curation and fact grounding; QwQ-32B where one agent must hold state for hours. Claude stays the orchestrator of the brain itself (this session is his Jarvis, 25 Aug ruling). Safety varies by task more than by model: Claude is strongest on jailbreaks (about 77% refusal on direct attacks); Mistral is the one to keep away from fact-heavy governance work.

**Caveat on hardware:** Llama 70B at Q4 needs about 40 GB of VRAM. The friend's RTX 2070 has 8 GB and King's laptop has no GPU, so 70B is a LOGIC-B or future-box option, not a day-one one; 8B and a quantised QwQ-32B are what fit today.

**Sources the scout cited (as reported, not re-fetched):** coworker.ai DeepSeek API pricing 2026 · sitepoint DeepSeek R1 vs Claude Code showdown 2026 · arxiv 2603.10012 (refusal rates) · sitepoint VRAM for 70B models 2026 · ucstrategies Llama 3.1 70B self-hosted guide 2026 · promptquorum autonomous local agents (May 2026) · medium (iamdgarcia) Llama 3.1 open weights · datacamp Qwen3.7-Max · layer3labs Qwen pricing · arxiv 2604.02947 (agent safety benchmarks) · github vectara hallucination leaderboard · arxiv 2606.26099 (governance benchmarks) · spheron LLM API pricing comparison 2026.

Related: [[project_faceless_content_engine]] · [[project_kd_robot_three_nodes_2026-08-29]] · [[feedback_multi_source_consensus_research]] (this is one sweep; a spend decision needs the second independent pass).
