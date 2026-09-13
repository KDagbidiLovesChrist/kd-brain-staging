---
name: reference-consultation-system
description: "The /consult skill, reusable, steerable, no-guessing client consultation engine (SPIN, Mom Test, Sandler Pain Funnel, 5 Whys, JTBD) that feeds the WAT build"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4f92d099-e2b6-4891-835d-78bd36071636
---

# /consult · Deep Steerable Consultation System (built 2026-06-22)

King wanted a REUSABLE consultation template, not one-off questions, "no guessing", spanning hours/
days, "steerability at its finest", feeding the WAT build. Built it grounded in proven frameworks
(research: `knowledge\consultation_frameworks_research_2026-06-22.md`).

## Files
- **`commands\consult.md`**, the skill. Trigger `/consult <client/project>`.
- **`commands\consult_question_banks.md`**, deep question banks per project type (website/course site,
  faceless AI channel, social/content mgmt, AI automation) + the no-guessing probe cheat-sheet.
- **`commands\consult_living_spec_template.md`**, copy into each project as `CONSULT_SPEC.md`.

## The method (what makes it work)
- **Session loop** (BABOK): Prepare (read LOCKED, pull OPEN items) → Conduct → Confirm. Runs across many sessions.
- **Take the expert role(s)** the job needs before asking.
- **12 question layers** in order: vision → who → what → why → their picture/look → features/scope →
  content → tech → funnel → constraints → edge cases → success metrics.
- **Deep-probe rule (no guessing):** every vague answer gets drilled, 5 Whys (they give a solution),
  anchor-with-examples (vague word like "premium" → "show me sites you love"), Sandler **Pain Funnel**
  (a pain → 8 nested Qs to a quantified cost), **Mom Test** (hype → ask about PAST actions + spend, not
  future promises). Rule: if a builder couldn't build the right thing from the answer, keep probing.
- **Playback rule:** read it back, get an explicit "yes that's right" before tagging LOCKED. Silence ≠ yes.
- **Steerability engine = the living spec:** every requirement tagged 🟢LOCKED / 🔴OPEN / 🟡NEEDS-FOLLOW-UP
  / ⚫ASSUMPTION. Only LOCKED rows go into the build prompt. King always drills the gaps.
- **The Mom Test (King asked):** people lie to be nice; ask about their life + past behaviour, not your
  idea or hypotheticals. A meeting succeeds only on real commitment (Time → Reputation → Money), never a
  compliment. ("I'd love it" = worthless; "here's a deposit" = everything.)

## First use = Olly (the Olly consultation/playbook follow this method). Reuse for every client.
