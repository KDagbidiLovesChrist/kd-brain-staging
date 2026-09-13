# Nate Herk · "Stanford's Method Turns Claude Into a PhD-Level Research Team" (STORM skill)

- **Watched:** 2026-07-10 (Gemini deep-watch, confidence 5/5). Cross-check partial (redirected to the GPT
  5.6 video before full second-source pass, so treat the outside numbers below as Nate's claims, lightly
  checked, not a full consensus).
- **Source:** https://www.youtube.com/watch?v=Tj3018n5MVg
- **Why saved:** directly relevant to KD's `/research` + `deep-research` skills. King asked to keep it.

---

## THE LESSON IN ONE LINE
Do not use Claude as a search box with one prompt (it inherits your blind spots). Run the topic through
several named expert lenses, map where they disagree, verify every source, then synthesize. Nate packaged
Stanford's STORM idea into a free Claude skill `/storm-research` that does this automatically.

## THE METHOD (STORM, as Nate implements it)
Five expert lenses researched in parallel, then verified:
1. **Practitioner** · 2. **Academic** · 3. **Skeptic** · 4. **Economist** · 5. **Historian**.
"Each angle finds a hole the others miss. The gaps are the whole point" (1:02).

The skill chains 4 phases (skill.md + a report-template.html):
- **Phase 1 · Multi-perspective scan** (spins up the 5 lenses as sub-agents, each on Opus 4.8).
- **Phase 2 · Contradiction map** (where do the lenses disagree, evidence strength, unaddressed topics).
- **Phase 3 · Synthesis** (compile into a structured briefing).
- **Phase 4 · Adversarial peer review** (check bias, misrepresentation, verify citations: confirmed /
  corrected / demoted). ~6 more verification agents run here. Total ~10 to 12 agents.
Output = a clean, verified **HTML briefing**. (Phase 0 = scope the topic, asks clarifying questions if the
topic is too vague.)

## HEAD TO HEAD (Nate's own test)
- Same prompt to Claude's built-in `/deep-research` vs his `/storm-research`.
- Deep Research spun up 100+ agents, hit API rate limits, output a markdown file with many unconfirmed
  sources and open questions.
- STORM used ~12 agents, no rate limits, produced a verified HTML briefing, and even surfaced a "missing
  6th lens" (nobody sat in the customer / frontline employee seat).
- He had an independent model (Codex) judge both: Codex preferred the STORM briefing on evidence quality,
  source diversity, thesis, actionability, risk control, and usefulness for content.

## KEY CLAIMS (Nate's words, honesty flags)
- "STORM produced articles **25% more organized** than the next best method" (0:04). This is from the real
  Stanford STORM paper (peer-reviewed), NOT demonstrated in the video. Treat as an external cited claim.
- "**100% cheaper** and faster" than Deep Research (4:09): supported by far fewer agents + tokens, but he
  never shows actual currency figures, so read it as "much cheaper," not a precise number.
- "Know more in 5 minutes than people who spent days reading" (0:06): bold, unverifiable, marketing.
- Sub-agents vs Agent Teams (8:40): sub-agents "report back only, never talk to each other"; agent teams
  "argue, disagree, hand you one consensus" but are "much more expensive." STORM uses sub-agents.
- His honest caveat (11:18): the specific skill "might not be best for everybody," but the PRINCIPLES
  (multiple perspectives + contradiction map + verification) are broadly right. "Borrow expertise you don't
  have."

## WHAT IT MEANS FOR KD
This is the SAME engine King's brain already preaches: Rule #17 (consensus, multiple independent verified
sources, model the winner) and the existing `/research` + `deep-research` skills that fan out and
adversarially verify. Nate's contribution is a clean, named 5-lens template + an HTML report format.
- **Confirms** the brain's research philosophy, does not conflict with it.
- **Upgrade to steal:** the 5 named lenses (practitioner / academic / skeptic / economist / historian) +
  the explicit **contradiction map** step + the **confirmed/corrected/demoted** source tags. Fold these
  into `/research` or `deep-research` as a preset persona pack + a source-verdict tag, cheap, high value.
- **Cost note:** run the 5 lenses on a cheap worker tier (Sonnet 5 / Haiku), reserve the manager tier for
  the final synthesis + peer review. (See the manager/worker lesson:
  [2026-07-10_nate-gpt56-sol-vs-fable5.md](2026-07-10_nate-gpt56-sol-vs-fable5.md).)

## WHAT TO DO
1. Optional, cheap: add a "5-lens + contradiction map + source-verdict tags" preset to `/research` /
   `deep-research`. Do not build a whole new skill, King already has the fan-out engine.
2. The free skill is in Nate's AIS community (Classroom → All YouTube Resources) if King wants the exact
   skill.md + report-template.html to copy the prompt wording.
3. Not a direct money-maker; it is a research-quality upgrade that makes every other output sharper.
