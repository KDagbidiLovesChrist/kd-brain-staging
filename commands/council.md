# /council · King's Deliberating Council (ruling 33)

**Trigger:** User types `/council [question]` OR any skill hits Rule 17's reflex on a non trivial
decision (a build, a route, a spend, a client or money call, anything King will act on) and no
faster gear fits. Never fired for a mechanical step, a lookup, or a yes/no a single seat can settle.
**Purpose:** King's council. A chair, a check, and the seats between them, sat for a non trivial
decision, ruled on, and closed with King's own yes. This file extends `commands\research.md`
(the lens roster, the contradiction map, the four phases) with the star topology, the blind round,
a two round cap, the chair's verdict format, the faith refusal, and King's own seat.

---

## WHY TEN SEATS, NOT TEN FABLES (ruling 33, law 1, the maths first)

His own words (ruling 28 and 29): "10 fables talking to each other." Ten copies of the same model on
one prompt share almost everything they get wrong. For N voters whose errors share a correlation rho,
the error of their average is sigma squared times (rho plus (1 minus rho) over N). Ten Fables on one
prompt sit near rho 0.8, which gives 1 divided by (0.8 plus 0.2 over 10), about 1.2 effective voters,
at ten times the price. Ten seats that differ in source, lens and model sit near rho 0.2, which gives
1 divided by (0.2 plus 0.8 over 10), about 3.6 effective voters, for a tenth of the cost. Independence
buys the 1 over root N that `commands\research.md`'s five lens layer already banks on (its own line:
"5 independent lenses average out random error"). His own Rule 17 says the same thing in plain words,
"copycat sources are fake consensus," and the 15 Aug sitting proved it the hard way: only 1 of 7 voices
on that run caught the one fact that mattered, because a majority is only as good as its independence.

**So: ten seats, not ten Fables.** A seat is one source times one lens times the cheapest model that
can hold it (ruling 33, law 1). `tools\logos_lanes.py` names the six model rungs a seat may sit on;
`/council`'s own job, every sitting, is to pick the ten seats and place each on the cheapest rung
that holds it. More than one logical seat can share a physical rung in the same sitting, each still
blind to the others and each writing its own brief.

---

## THE RUNGS (verified from `tools\logos_lanes.py`, `COUNCIL_RUNGS`, ruling 33)

| Rung | Provider, tier | Does work | What it is for |
|---|---|---|---|
| **chair** | Anthropic, Fable | No | Sits every sitting. Reads the seats' briefs, decides the route, writes the plan rows. Thinks, never does (rulings 30 and 31). Console key, inside the monthly envelope. |
| **check** | Anthropic, Opus 4.8 | No | Sits only when a chair verdict fails a plain test, contradicting a recorded ruling, citing no evidence hash, or disagreeing with a probe. Half the price a token of Fable. |
| **sonnet** | Anthropic, Sonnet | Yes | The solid mid tier worker seat. |
| **haiku** | Anthropic, Haiku | Yes | The cheap fast scout seat. |
| **deepseek** | OpenRouter, DeepSeek | Yes | Glue and cheap orchestration. |
| **gpt** | OpenRouter, GPT | Yes | Code (ruling 30). |
| **gemini** | OpenRouter, Gemini | Yes | Video (ruling 30). |
| **local** | Ollama, qwen3:8b | Yes | The volume seat, free, never leaves the laptop. |

Eight rungs, two of which (chair, check) never do the work. Six carry the ten logical seats below.

---

## THE TEN SEATS · one source, one lens, the cheapest rung that holds it

Lenses come from `commands\research.md`'s five (practitioner, academic, skeptic, economist,
historian) plus three ruling 33 names by name (security, the accountant, the tracer). Sources come
from ruling 33's own list (the brain, the web, the ledger, the prover logs, the board's probes),
with the faith files excluded from every Claude and OpenRouter seat, per the refusal below.

| Seat | Source | Lens | Rung | Notes |
|---|---|---|---|---|
| 1 | The brain, `/search`, FTS5 at rung R | Practitioner, does it actually work here | local | local knowledge |
| 2 | The prover logs and the board's own probes | Historian, has this been tried, what happened | local | shares the rung with seat 1, run in sequence, still blind |
| 3 | The web, Firecrawl | Academic, what does the documentation or evidence say | haiku | web via Firecrawl |
| 4 | The gate and the security posture files | Security, where does this leak or break a constraint | haiku | shares the rung with seat 3 |
| 5 | The web, Tavily | Skeptic, where is this wrong or hyped, checked against a second web source Firecrawl never saw | deepseek | web via Tavily, an independent second source, ruling 35 |
| 6 | The grounding tracer's own findings | Tracer, does the claim trace to something real or was it invented | deepseek | shares the rung with seat 5 |
| 7 | The ledger and the meter, `_ops\KD_LOOP_LEDGER.md`, `tools\logos_lanes.py`'s cost functions | Economist, the maths seat, what does this cost and what is the return | sonnet | |
| 8 | `tools\goals.py`, King's own money files | Accountant, does this move the goal King already named | sonnet | shares the rung with seat 7 |
| 9 | The code under review | Code, does it run, does it regress anything | gpt | ruling 30 |
| 10 | The visual or the render under review | Video, does it look and move the way it was meant to | gemini | ruling 30 |

King himself sits as an eleventh seat, outside every model rung. See KING'S SEAT AND YES, below.

Reuse `commands\subagent_registry.md`'s standard handoff for every seat's report back to the chair:
```
Seat: [rung, e.g. haiku]
Source: [what it read]
Lens: [the angle, e.g. Skeptic]
Brief: [about 500 tokens, the finding plus its own citations]
Evidence hash: [sha256 of the brief text, first 12 hex chars shown, full hash in the ledger row]
Cost: [tokens in / tokens out · rung]
Status: success | partial | failed
```

---

## THE STAR

`commands\orchestrate.md`'s rule stands, unchanged: agents return to the chair, never to each other
("Fire agents using the Agent tool... Passes result directly to orchestrator, not to each other").
No seat ever reads another seat's brief, prompt, or output. Every brief lands with the chair alone.

**Round 1, blind.** All ten seats write at once, none seeing the others, each against its own source
through its own lens. The chair reads ten short briefs, never ten transcripts.

**Round 2, only the seats that disagree.** The chair maps the ten briefs against each other, the same
contradiction map `commands\research.md` already runs at its Scan and Synthesis phases. Where two or
more seats land on different answers, only THOSE seats sit again, this round shown each other's round
1 brief and asked to answer the specific disagreement, nothing else. A seat that agreed in round 1 is
not recalled. This is the two round cap. It is tighter than `commands\qa-master.md`'s own five round
loop cap because a council sitting is a decision, not a bug hunt, and a third round on the same
question is polishing, not deliberating.

**If round 2 still disagrees, the chair records the dissent.** No third round, no forced consensus.
A minority view that survives cross examination is data, not noise, and gets written into the verdict
verbatim, per the chair's verdict format below.

---

## THE CHAIR'S VERDICT FORMAT

```
COUNCIL VERDICT, [Question]
─────────────────────────────────
SEATS SAT: [list, rung and lens each]
ROUND 1, blind: [one line per seat, its finding]
ROUND 2, cross examined: [only the seats that disagreed, and what changed]

ROUTE: [the decision, plain English, actionable]
EVIDENCE HASHES: [seat → hash, one line each]
DISSENT: [any minority view that survived round 2, kept verbatim, or "none"]

CONFIDENCE: High / Medium / Low
COST: [tokens in / tokens out, all rungs together, and the USD estimate]
KING'S RULING: [pending, or his words, recorded in _ops\KD_ACCEPTANCES.md]
```

A verdict with no evidence hash for a seat that sat is not a verdict, it is a guess with a chair's
name on it. A verdict that smooths a real dissent into a false unanimous ROUTE line fails the gate.

---

## THE FAITH REFUSAL

A hard rule, not a suggestion. `tools\logos_lanes.py`'s `LANE_FAITH` carries three constraints,
`NEVER_LEAVES`, `NO_CLAUDE`, `NO_OPENROUTER`, and `tools\logos_policy.py` checks faith before
anything else it decides. The council obeys the same law:

If the question names a faith subject (checked the way `logos_policy.decide()` already checks it,
`logoi_gate.FAITH_SUBJECTS` against the text), the chair does not sit, no Claude seat sits, and no
OpenRouter seat sits. The question is refused to the whole council and routed instead to the local
only scripture door (`search_scripture`, one of LOGOI's own tool calling doors, `_ops\ORCHESTRA.md`),
answered from King's own 84 verified study files, local model only, and it says "I do not know" when
those files do not cover it. This is the 25 Aug ruling, carried here unchanged: doctrine is Fr
Bogdan's, never a model's, and the council's job stops at the door.

---

## THE CEILING

Two ceilings, both in `tools\logos_lanes.py`, both refused past, never silently truncated:

- **`SITTING_CEILING_TOKENS`, 60000.** One council decision, tokens in plus out, every rung added
  together. `check_sitting()` refuses past it, the same HTTP 402 shape the token ceiling already
  answers with elsewhere in the engine (the 10.1 pattern). A sitting that would cross this line does
  not run a smaller version of itself quietly, it stops and says so.
- **`MONTHLY_ENVELOPE_USD`, 20.0.** Twenty dollars a month, chair plus check together, on the
  Console key, His own words, "$20 a month." `check_envelope()` refuses past it the same way. Seats
  through OpenRouter and the local rung do not spend against this envelope, only Fable and Opus do.

Neither ceiling is a target to spend up to. A cheap sitting that answers the question is a better
sitting than an expensive one that only feels more thorough.

---

## KING'S SEAT AND YES

King sits as a seat, outside every model rung, per the 26 Aug division, his own words, "me wisdom is
divine and you are knowledge, you are logic." His seat's brief is his own words, taken live if he is
sitting with the council when it meets, or his own written rulings when he is not, pulled the same
way `_ops\KD_ACCEPTANCES.md` already reads them, verbatim, spelling untouched, with a reading offered
underneath and marked his to correct.

**The council's verdict is never final until his yes is recorded.** Write it to
`_ops\KD_ACCEPTANCES.md`, the same pattern already proven on the 2.4 acceptance (when, iota, by,
quote verbatim, reading offered), a row appended, never edited. A ROUTE line with no King's ruling
row is a draft, not a decision, no matter how clean the ten seats' briefs read.

---

## WHEN THIS RUNS

**Build time.** This Claude Code session, King's Jarvis (25 Aug ruling), runs the star as subagents,
seats on Haiku scouts where the task allows it, the chair being this session itself, kept under the
15 agent guideline already standing in this brain. The ceiling here is the session's own plan limit,
not the two ceilings above, so the council is still rationed to non trivial decisions by the Rule 17
reflex and never sat for a mechanical step, exactly as at run time.

**Run time.** The engine sits the same council for real, chair Fable, check Opus 4.8, seats on the
rungs named above, and every sitting writes one row to `_ops\KD_COUNCIL_LEDGER.md`, the sittings
ledger a separate piece of this build writes (C.3). That row is named here only, not designed here.

---

## THE GATE · nothing ships until it passes (Rule #21)

1. Every seat that sat has an evidence hash in the verdict, or it did not sit.
2. Zero em dashes or en dashes anywhere the verdict is shown to King. `/humanize` before anything
   client facing.
3. A faith question never reaches a Claude seat or the chair. Test this every time the refusal is
   touched.
4. Both ceilings are refusals, proven by running one sitting past each and reading the reason back,
   never assumed from reading the code.
5. No ROUTE line without a King's ruling row in `_ops\KD_ACCEPTANCES.md`. "The chair decided" is not
   the bar. King's yes is.
