---
name: feedback-consensus-everything-rule
description: "CLAUDE.md Rule #17, every task (not just research) done on verified multi-source consensus + proven-pattern-first, scaled to stakes, with the maths shown, and King's yes gated on a consensus report + the goal"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: f8da157f-79bc-4185-8ad4-a157cdd51387
---

# Consensus on everything + proven-pattern-first (Rule #17)

**Standing decision (2026-06-27, King), built collaboratively during the content-engine audit.** Extends
Rule #16 ([[feedback-multi-source-consensus-research]]) from "research" to **every task**.

## The rule
For ANY task, planning, research, editing, judging, coding, tool-choice, design, finance, anything, do it the **best way** by triangulating MULTIPLE **independent, verified** sources/methods before acting.
- **Use [[../commands/find-skills]] for any non-trivial task, NOT just content.** It is the universal
  "do any task the best way" scout (there are tasks neither of us has hit yet that still need it).
- **Don't reinvent, model the proven winner / best practice for THAT domain.** The framework varies by
  project: content = **TSV** (Title·Script·Video) modelled on a proven viral winner, then landed via the
  storyboard pipeline ([[reference-visual-production-pipeline]]); code = established patterns; design = the
  proven reference method. **TSV is content-only, not universal.**
- **Scale depth to stakes:** final / irreversible / quality-critical = full multi-source consensus + an
  adversarial check; trivial mechanical steps = a quick sanity check (lean-spend, [[feedback-lean-spend-llama-routing]]).
- **King's "yes" is granted ONLY when the work (a) carries a consensus report AND (b) matches the goal**,   his, or the user's/client's (money/audience/followers, via `tools\goals.py`). Approval becomes objective,
  not a vibe.

## Why (the maths · always show it, don't just assert "consensus says…")
1. **Random error averages out ~1/√N.** Combining N *independent* estimates shrinks the error stddev by √N
   (4 sources ≈ half the error, 9 ≈ a third). Same reason ensembles beat any single model.
2. **Bias cancels.** A GitHub repo, a viral TikTok and a forum thread have different blind spots; combined,
   the idiosyncratic biases cancel and the real signal survives.
3. **Wisdom-of-crowds / Condorcet:** if each independent source is even slightly better than chance, the
   probability the *majority* is wrong falls toward 0 as N grows.
4. **The catch (also maths):** holds ONLY if sources are **independent and each verified to return real
   data.** Copycat/correlated sources are fake consensus and *amplify* a shared error. So: ≥2 independent
   platforms must return real data; prefer genuinely different methods (data + ear + crowd).

**One line:** one opinion can be confidently wrong; the place where independent methods agree is where the
truth usually is, and we show that maths every time.

## How to apply
- **DEFAULT REFLEX (King said make it automatic, 2026-06-27):** at the START of any task, FIRST flag it
  trivial or non-trivial. If non-trivial → proactively lead with `/find-skills` + the consensus plan + the
  goal BEFORE building, **without being asked** (state it so King sees it). If trivial → say so and just do
  it (lean-spend). The enforcement is that this lives in the **global `CLAUDE.md`** (loaded every session,
  synced to phone), so it's always-on, not a thing we have to remember.
- **Lean vs consensus balance (King, 2026-06-27):** free is the DEFAULT, not a hard cap. Spend is justified
  the moment it **materially improves the consensus or the output** (e.g. Apify to scrape REAL top-performing
  TikToks/Reels to model via TSV, VidIQ/TubeBuddy view data, a paid enhancer if free can't hit UGC quality).
  Never under-do a consensus to save pennies, and never spend blind: **flag the tool + cost + why → King
  approves (money gate, [[feedback-lean-spend-llama-routing]]) → logged.** Free only when free gives the same answer.
- **Recency check (King, 2026-06-27):** prefer **current-year** sources; use a prior year's only if it's
  still maintained/relevant. **Date-stamp findings** and scope searches to the current year so the consensus
  is up-to-date, not stale. (Tool landscapes move fast even when the *method* is timeless, e.g. the 2026
  faceless-edit leaders are Submagic/OpusClip/Captions.ai; the AI-video models are Veo 3.1/Kling 3.0/Seedance.)
- Print a short **"consensus + goal" header** on content-engine / find-skills outputs so King SEES it was
  done (enforced, not assumed), same lesson as the storyboard gate ([[feedback-confirm-spec-before-send]]).
- Born from the "ew wtf" video #1: the muffled-voice fix and the whole video engine are being re-decided by
  consensus + find-skills instead of hand-rolled guesses.
