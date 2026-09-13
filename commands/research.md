# /research · Multi-Agent Consensus Research

**Trigger:** User types `/research [question]` or `/dig [question]` OR says "research X", "dig into X", "find the best way to X", "what do we know about X"
**Purpose:** Get the best possible answer by running 3 agents simultaneously across web, internal knowledge, and AIS resources, then synthesising to consensus

---

## WHY 3 AGENTS

One source = one opinion. Three sources = verified truth.
The consensus pattern eliminates guessing and catches blind spots.

---

## THE 3-AGENT SETUP

| Agent | Source | What it finds |
|-------|--------|--------------|
| Agent 1 | Web (Brave Search / WebSearch) | Current best practice, tutorials, tools |
| Agent 2 | Internal RAG (knowledge\ folder) | What we've already learned and proven |
| Agent 3 | AIS database (ais_all_learnings.md + YouTube) | Nate Herk's tested approach |

All 3 run at the same time. Takes the same time as one search.

---

## CONSENSUS RULE

| Result | What it means | Action |
|--------|--------------|--------|
| 2 of 3 agree | Strong signal | Use that answer |
| All 3 agree | Confirmed truth | Use it with confidence |
| All 3 conflict | Genuine uncertainty | Flag to King David · present all 3 options |
| 1 outlier | Likely noise | Use majority, note the outlier |

---

## SCALE TO STAKES · pick the gear FIRST (Rule #17, lean spend Rule #12)

Flag the question before you run anything:
- **Quick gear (trivial):** a lookup, a price, a yes/no. Run the 3-agent consensus above and stop. Do not spin up a fleet for a one-liner.
- **Deep gear (non-trivial):** a decision, a build, a client or money answer, anything King will act on. Run the STORM 5-lens layer below ON TOP of the 3 sources.

---

## THE STORM DEEP LAYER · 5 expert lenses (non-trivial only)

Modelled on Stanford's STORM method (from Nate Herk, watched 2026-07-10, saved at `../knowledge/video_studies/2026-07-10_nate-storm-research-skill.md`). The 3 agents above find SOURCES; these 5 lenses interrogate the topic from angles one prompt misses. "Each angle finds a hole the others miss. The gaps are the whole point."

**Why it works (the maths, Rule #17):** 5 independent lenses average out random error (~1/√N) and their biases cancel, so a claim all 5 survive is far likelier true than one prompt's guess.

| Lens | Sits in the seat of | Asks |
|------|--------------------|------|
| Practitioner | the person doing it daily | Does this actually work? What breaks in the real world? |
| Academic | the researcher | What does the evidence or theory actually say? |
| Skeptic | the critic | Where is this wrong, hyped, or survivorship bias? |
| Economist | the money | What does it cost? What is the ROI and the incentive? |
| Historian | the long view | Has this been tried before? What happened? |

Swap a lens for a domain fit when it helps (a "Customer" or "Frontline" lens for a business call, a "Fr Bogdan / theology" lens for a faith question), and name the swap.

### The 4 phases
1. **Scan** · spin up the 5 lenses in PARALLEL as sub-agents (use the `scout` or `general-purpose` agent type on the CHEAP worker tier, Sonnet 5 / Haiku / local, to keep it lean, see `../knowledge/video_studies/2026-07-10_nate-gpt56-sol-vs-fable5.md`). Each lens returns its findings plus its own sources.
2. **Contradiction map** · lay the 5 side by side. Where do they disagree? How strong is each side's evidence? What did NONE of them cover (the missing lens)?
3. **Synthesis** · the manager tier (Opus / Fable, the model running this session) writes ONE briefing from all 5 plus the contradiction map, weighted to the goal.
4. **Peer review** · one adversarial pass over the briefing: catch bias, misread claims, and VERIFY every load-bearing source. Drop anything that fails.

### Source verdicts (always show them in deep mode)
Every load-bearing claim carries a tag: ✅ **confirmed** (checked, it holds) · ✏️ **corrected** (was wrong, fixed) · ⬇️ **demoted** (weak or unverifiable, downranked). An unverified claim is not consensus, it is a guess.

---

## GOAL LENS (when the question has a goal · King's standing rule)

If the question serves a goal (money/monetization · followers · audience · traffic · engagement), say it up front and **weight the consensus toward that goal**, the best answer is the one that moves the goal, not just the most-cited one. State the goal in the result and rank options by goal-fit. Multiple goals are normal (rank them, main first); the shared definitions live in `tools\goals.py` so "monetization" means the same thing here as in the content engine.

---

## OUTPUT FORMAT

```
RESEARCH RESULT, [Question]
─────────────────────────────────
Web says:      [1-2 sentences, best current approach]
Internal says: [1-2 sentences, what we already know]
AIS says:      [1-2 sentences, Nate's tested approach]

CONSENSUS: [The answer, plain English, actionable]
CONFIDENCE: High / Medium / Low

RECOMMENDED ACTION:
→ [Exact next step based on the answer]

SOURCES:
• [Key URL or file reference if relevant]
```

### Deep gear output (STORM, non-trivial) · use instead of the block above

```
RESEARCH BRIEFING (deep), [Question]    GOAL: [goal]
─────────────────────────────────
5 LENSES:
  Practitioner: [1 line]     Academic:  [1 line]
  Skeptic:      [1 line]     Economist: [1 line]
  Historian:    [1 line]

CONTRADICTION MAP:
• [where the lenses disagree] → [which side has the stronger evidence]
• MISSING LENS: [what none of them covered]

CONSENSUS: [the one answer, plain English, weighted to the goal]
CONFIDENCE: High / Medium / Low

SOURCE VERDICTS:
✅ confirmed: [claim + where it was checked]
✏️ corrected: [claim, as fixed]
⬇️ demoted:   [weak claim, why it was downranked]

RECOMMENDED ACTION:
→ [exact next step]
```

---

## WHEN INTERNAL KNOWLEDGE IS MISSING

If Agent 2 (internal RAG) finds nothing relevant, that's useful information too.
Note: "No internal knowledge on this yet, web and AIS are the basis."
After answering, add the new knowledge to knowledge\patterns.md.

---

## EXAMPLE USES

- `/research best way to cold email a plumber in Ireland`
- `/research how to set up Perplexity API`
- `/research Obsidian Local REST API plugin setup`
- `/research pricing for lead gen services in Ireland`
- `/research how other people are using Hermes with Claude Code`
- `/research (deep) should KD run high-volume tasks on a cheap worker model or on Fable` · triggers the 5-lens layer


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
