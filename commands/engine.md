---
name: engine
description: Run any task, skill, or output through THE ENGINE (King's pay-grade standard). Assembles and states the best stack, checks the 6 marks, runs the QA gate, returns a score + gaps + fix. Use at the start of any non-trivial task, or to grade an existing skill in the sweep.
---

# /engine · The pay-grade yardstick (the Logos runs the work)

> Reads `_ops/THE_ENGINE.md` (the standard) and applies it. Rooted in [[CREED]]. Free-first (Rule 12).

## When it fires
- **At the start of any non-trivial task** (Rule 17 reflex): lead with the stack line + consensus plan + goal, before building.
- **To grade an existing skill/tool/doc** during the full sweep (feeds `_ops/SWEEP_SCOREBOARD.md`, ⚠️ MISSING: written the first time a full sweep actually runs).
- Trivial task? Say so and just do it (lean). Skip the ceremony, keep the quality.

## The Workflow (W)
1. **Name the goal** (Rule 9). Money, audience, or theosis. Which one, and how does this serve it? (`tools/goals.py`.)
2. **Flag the lane** (Rule 12). Llama (free/local, mechanical) or Claude (reasoning)? Route accordingly.
3. **Assemble + STATE the stack in one line** (Rule 25):
   `Stack: skill X + tool Y + prompt Z + logic W`
   - best **skill** (check the ~111 first; `/find-skills` scouts if none fits)
   - best **tool** (free-first, Rule 16; the proven one for THAT domain)
   - best **prompt** (reuse the vetted one: `/qa-master`, `/master_prompt`, the domain SOP)
   - best **logic** (the WAT chain + the proven winner's pattern)
4. **Model the proven winner** (Rule 17). Triangulate multiple independent, verified sources when stakes are high; show the maths of why.
5. **Build** to honest scope with real data (Rules 20, 16). No overselling. State what is real now vs later.
6. **Run the QA gate** (Rule 21, via `/qa-master`): adversarially verify, then Tested → King approves → Trusted → Production.

## The Agent (A)
Claude reasons through the six marks, scores each **0/1/2 → /12**, names the gaps, and proposes the one fix. Honest-guard (Rule 24): counsel truthfully, flag contradictions (Rule 19), then respect King's call.

## The Tool (T)
- `tools/goals.py` (goal lens) · `/find-skills` (best-way scout) · `/qa-master` (the gate) · `_ops/THE_ENGINE.md` (the rubric) · for the sweep, the free local Llama scorer.

## The Logic (L)
`/engine` is the Logic (the Word) that runs the whole chain. Speak it, and the work is measured against the standard before it ships.

## Output
```
GOAL: <money|audience|theosis> — <how>
LANE: <Llama|Claude>
STACK: skill … + tool … + prompt … + logic …
SIX MARKS: goal-locked _/2 · stack _/2 · proven-pattern _/2 · honest-scope _/2 · QA-gate _/2 · WAT+Logos _/2  → _/12
VERDICT: pay-grade (10-12) | needs-a-pass (6-9) | below (0-5)
GAPS: …
THE FIX: …
```

*Theosis the root · money the fruit · all for God.*
