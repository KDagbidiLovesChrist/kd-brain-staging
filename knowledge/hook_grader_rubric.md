# Hook Grader Rubric · the single source of truth (used by `tools\hook_grader.py` + the agent)

A hook is the first line said + the on-screen text + the Title. 71% of viewers leave in 3 seconds, so
the hook is the whole ballgame. This rubric scores any hook 0, 100 so we keep only A-grade hooks.
Grounded in `/content-engine` HOOK BUILDER + `reference_faceless_video_results_consensus.md`.

## Score = 100 across 6 dimensions
| # | Dimension | Pts | What earns it |
|---|---|---|---|
| 1 | **Curiosity / open loop** | 25 | Opens a question or gap the viewer MUST close ("nobody tells you…", "the real reason…", "what happens when…", "once you see this…"). |
| 2 | **Specificity** | 20 | A number/%, a concrete noun, or a named concept · not vague ("3 hooks", "80% leave", "the 2-second rule"). |
| 3 | **Stakes (pain or payoff)** | 20 | A clear cost-of-ignoring or reward ("you're losing…", "the mistake that…", "…in 7 days", "without ever…"). |
| 4 | **Brevity & punch** | 15 | First line ≤ ~12 words, value front-loaded in the first 3 words. Long/throat-clearing loses points. |
| 5 | **Audience framing ("you")** | 10 | Speaks directly to the viewer ("you/your"), not "I/we/today I". |
| 6 | **Proven type match** | 10 | Matches a known winning pattern (below). |

**Deductions (capped):** weak/generic openers, "in this video", "hey guys", "today I want to talk about",
"welcome back", "let me show you", and hedging ("maybe", "kind of", "I think"). Each −8 (max −24).

**Grades:** A ≥ 85 · B 70, 84 · C 55, 69 · D 40, 54 · F < 40. **Keep A only; rewrite the rest.**

## Proven hook types (name the type when grading)
- **Open Loop / curiosity**, name a concept + "once you see it you can't unsee it."
- **Expectations vs Reality**, "Everyone thinks X needs A,B,C. The best ones delete two of those."
- **Pain + number**, "You're losing 80% of viewers in the first 3 seconds, and it's this one mistake."
- **Contrarian**, "Stop doing X. It's costing you."
- **Results-first**, "This took a faceless page from 0 to 50k in 30 days."
- **Frame branding**, name the concept so it sticks and you can repeat it ("the 2-second rule").
- **Unexpected analogy** *(faceless AI-tools, 2026-07-10 study)*, map the tool to a familiar/fun concept ("the Sims for managing AI agents", "Duolingo for your LLM"). The surprise + relatability stops the scroll; back it with a matching visual/sound.
- **Leak / secret / exclusive**, frame the value as insider or forbidden knowledge ("they leaked the entire system prompt", "the setting they don't want you to find"), backed by quick visual proof.
- **Speed-value promise**, a big outcome in a tiny, specific time ("second brain set up in 30 seconds", "X in under a minute"). Compresses the perceived effort/complexity.

## How the agent uses it
After the tool scores a hook, Claude does the judgment pass: confirm the type, name the single biggest
weakness, and write **2 stronger rewrites** that raise the lowest-scoring dimensions. Always "say + show +
write" the final hook.
