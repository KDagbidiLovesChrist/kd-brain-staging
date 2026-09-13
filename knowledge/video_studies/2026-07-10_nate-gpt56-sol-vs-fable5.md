# Nate Herk · "I Tested GPT 5.6 Sol vs Fable 5. What You Need To Know."

- **Watched:** 2026-07-10 (Gemini deep-watch, confidence 5/5) + 3+ independent sources cross-checked.
- **Source:** https://www.youtube.com/watch?v=EthxaDswUFo (posted ~2026-07-09, Nate's newest)
- **Method (per /watch rule):** watched the actual video AND cross-read the benchmarks, one objective lesson.

---

## THE LESSON IN ONE LINE
GPT 5.6 Sol and Claude Fable 5 are roughly tied on raw intelligence, but Sol runs at about a third of the
cost, faster, and more reliably, so the win is not "which model" but "which job": Fable is the **manager**
(reason, judge, create the hero output), Sol is the **worker** (ship, execute, verify, at volume). Route by
task, do not pick one king.

## WHAT NATE ACTUALLY DID
Ran Fable 5 (in Claude Code) against GPT 5.6 Sol (in Codex) all day, same prompts:
- **3 agentic builds:** open world bike game, scroll stopping website, five viral visual elements.
- **130 stateless API calls** scored head to head ("the scoreboard").

**His results (primary):**
- Fable's creative builds looked better (more immersive 3D, more "wow"): the bike game and the "Ten Billion
  Years" site. Sol's builds shipped far faster and cheaper but had more visible bugs.
- API scoreboard: Sol won 24, Fable 3. Delivery rate Sol 100% vs Fable 78% (**Fable refused/timed out on
  29 of 130 calls**). Score WHEN Fable answered was near identical (Sol 0.982 vs Fable 0.966).
- His whiteboard: **Fable (manager)** = creativity, advising, knowledge work, video, pure capability.
  **Sol (worker)** = price, computer use, devil's advocate, finding bugs, verification, speed.
- His own honest caveat: the fair fight is Sol vs **Opus 4.8**, not Sol vs Fable (different tiers); and "feel
  on your real day to day work" beats benchmarks.

## INDEPENDENT CROSS-CHECK (the second read)
- **Artificial Analysis** (independent benchmark house): composite Intelligence Index at max effort =
  Fable 5 **60** vs Sol **59**, a statistical tie, at ~1/3 the cost. Sol **leads** the Coding Agent Index
  (~80). Caveat: AA runs Fable with an **Opus 4.8 fallback on ~8% of tasks** (mirrors Nate's refusal finding).
- **the-decoder / techtimes:** "Sol nearly matches Fable 5 on aggregated benchmarks at one-third the cost",
  plus "a benchmark problem" (the comparison is not perfectly like for like).
- **Verdict:** Nate's core thesis is confirmed by genuinely independent methods (his hands-on builds + AA's
  standardized benchmarks + tech journalism all point the same way). High confidence.

## PRICE OF ADMISSION (corrected, honest, per independent trackers July 2026)
Per-million-token API pricing (input / output):
- **GPT 5.6 Sol:** $5 / $30
- **Claude Fable 5:** $10 / $50  (the most expensive public tier; restored frontier)
- **Claude Opus 4.8:** $5 / $25
- **Claude Sonnet 5:** $2 / $10  (intro pricing through Aug 31, 2026)

⚠️ **Two numbers in the video are wrong / unreliable:**
1. The OpenRouter slide read as "Fable output $1/M, Sol $0.30/M". Real output is $50/M and $30/M (off by
   ~50 to 100x, a slide or read error). Use the real numbers above.
2. The per-project dollar tiles are internally inconsistent (a $58 output charge for 89K tokens implies
   ~$650/M, not ~$50/M). Trust the DIRECTION (Sol far cheaper), not the exact tiles.

## WHAT'S REAL vs HYPE
- **Real:** Sol is much cheaper, faster, more token efficient, and near tied on intelligence. Fable edges
  creative/design/judgment. Fable has a real reliability quirk in agentic harnesses (refusals/timeouts).
- **Hype/soft:** "Blows Fable out of the water" (the benchmark headline) is marketing, Nate's own hands on
  work walks it back. The "Fable is a whole tier above" claim is subjective (the data has them close).
  "Why 5.6 not 6" is pure speculation.

## WHAT IT MEANS FOR KD (money goal + lean spend, Rule #12)
This video is independent validation of the routing King already runs (Llama/worker vs Claude/manager). It
gives a cleaner frame for it:
- **Hero, sellable, creative output** (client 3D sites, the faceless video look, design King charges for):
  keep the **manager** class (Fable / Opus). Quality is the product, worth the spend.
- **Volume, mechanical, agentic loops** (scraping, research fan-out sub-agents, bulk drafts, bug/verify
  passes, the 24/7 engine): a **cheap fast worker** (Sol-class, or in Anthropic terms Sonnet 5 / Haiku)
  is the lean-spend choice, near-frontier quality at a fraction of the cost.
- **The pro move = combine them:** manager orchestrates cheap workers (Nate has a follow-up short on exactly
  this: "This Skill Combines GPT 5.6 + Fable 5"). Same shape as the WAT chain: Agent (manager) directs Tools
  (cheap workers).
- **Timing note King should know:** around Jul 7, 2026 Fable 5's unlimited/subscription access moved to
  usage-credits / per-token, and OpenAI timed GPT 5.6's public launch to that window. So the cost gap now
  bites more if King leans on Fable for high-volume work.

## WHAT TO DO
1. **Nothing to rebuild.** This confirms Rule #12 routing, it does not change the foundation.
2. **Sharpen the routing habit:** for high-volume/agentic KD work, default to the cheap worker tier and
   reserve the manager tier for hero creative + judgment. (Already how the brain is supposed to run.)
3. **Optional experiment (only if King wants):** wire Codex/Sol as the cheap "worker" for a bulk task and
   let Claude (manager) judge, to see the real cost drop on one of King's own pipelines before trusting it.
4. Not a money-maker on its own, it is a cost-discipline lesson. No spend required.
