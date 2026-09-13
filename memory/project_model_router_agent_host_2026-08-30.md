---
name: project_model_router_agent_host_2026-08-30
description: "A session the brain never recorded: on 30 Aug 19:03 an 'Agent Host' commit put a model routing command, matrix, router and skill dependency audit into the OneDrive copy of the brain only. Rescued into .claude on 2 Sep; its domain rules fold into the governor lanes by King's ruling."
metadata: 
  node_type: memory
  type: project
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-03T05:28:16.877Z
---

# The model router session, 30 Aug 2026, found and rescued 2 Sep

**What happened.** Commit `51261d3d` "Agent Host changes for main", author KDagbidiLovesChrist, 30 Aug 2026 19:03, landed in `C:\Users\Dell\OneDrive\Documents\GitHub\kd-brain`, a second clone of the brain that lived inside OneDrive from 29 Aug 00:26. It never reached `.claude` or GitHub, and no memory file, handoff or ledger row mentioned it. Found on 2 Sep while measuring why the drive mirror's ledger had split; cherry-picked into `.claude` main the same evening, hashes checked against the copy.

**The four files (630 lines):**
- `commands\model-route.md`: the `/model-route` command, usage, three domains (personal, business, legal), task types, four scenarios, override rules; its `/aide` integration marked pending.
- `knowledge\MODEL_ROUTING_MATRIX_2026-08-30.md`: eleven metrics scored 1 to 10 for Claude, Gemini and GPT; aggregate Claude 82/110, Gemini 76, GPT 76; routing rules per domain; a six step priority (domain override, capability fit, safety, cost and speed, fallback chain, Ollama on a quota hit). Cost is a score, not a price. OpenRouter is not named.
- `tools\model_router.py`: `Domain`, `Model` enums, a `ROUTING_TABLE` dict, `ModelRouter.route()` as a single lookup with `force_local` short circuiting to Ollama qwen3:8b, every decision appended to `~\.kd-brain\model_routing_log.jsonl` (3 rows exist, all 30 Aug 03:47, a smoke test).
- `tools\audit_skill_dependencies.py`: scans `skills\*\SKILL.md` for keywords and buckets each skill by what it needs, printed free first (CLI or Python, Playwright, text only, Ollama, Claude, needs an API key).

**Why it matters.** It was a fourth routing vocabulary in one house (the engine speaks Ollama and Anthropic; LOGOI speaks OpenRouter and NVIDIA; the brain's tools speak a dozen providers; this spoke Claude, Gemini, GPT). **King's ruling, 2 Sep (plan `hi-velvety-possum.md` §0b, ruling 10.3):** the governor's lanes in `tools\logos_policy.py` are the one routing table; this matrix's domain rules (legal = Claude only, personal quality first, business speed first) fold in as lane rules; its separate vocabulary retires once the rules are carried over. The dependency audit stays useful as is.

## DONE 3 Sep 2026: the fold, plus the council rungs (ruling 33)

The fold landed as `tools\logos_lanes.py` (new): seven lanes as one table (faith, cheap, local, remote,
personal, business, legal, each with a provider order and hard constraints; Legal is Claude only, no
OpenRouter, no local), imported and re-exported by `tools\logos_policy.py` so the governor stays under
its own 500-line rule. Built in the same change: `COUNCIL_RUNGS`, King's 3 Sep council design (chair =
Claude Fable, thinks only; check = Claude Opus, only on a failed verdict; eight seats), a per-sitting
token ceiling and a monthly spend envelope. `tools\model_router.py` is now a thin shim delegating to the
one table, kept for `commands\model-route.md`'s sake. `agents\qa-verifier.md` gained `model: opus` (the
refuter must never share the builder's model); `commands\subagent_registry.md` gained a `Cost:` line in
the standard handoff. 159 tests, all passing; the full gate at 67.11%.

**Two contradictions found and left for King, not guessed at:**
1. The old matrix routed theology to Claude; the 25 Aug faith ruling keeps it local, no Claude, ever.
   Code follows the newer ruling. Worth King confirming the matrix's line is simply dead.
2. The old matrix gave legal work a GPT fallback in one place while ruling Claude-only in another,
   contradicting itself. Code follows Claude-only, per ruling 10.3.

**Why:** a commit that exists in one clone only is a commit that can vanish with the clone; the OneDrive copy is being deleted on King's ruling once its unique content is rescued.
**How to apply:** never run brain tools from a second checkout; `drive_mirror.py` pins `BRAIN` to `.claude` from 2 Sep and a test guards it. Related: [[project_kd_robot_three_nodes_2026-08-29]], [[reference_orchestrator_model_scout_2026-08-29]], [[project_lllm_logic_layer_2026-08-25]].
