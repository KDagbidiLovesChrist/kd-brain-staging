# LOGOS OS · the whole picture, said by King and written down

**2026-08-24.** King spent a long session saying what Logos actually is, end to end, and asked
for it to be added up into one picture and put in his brain. This is that record. His decisions
are marked as his. Anything that is Claude's reading is labelled as such.

---

## What Logos is, in one line

**One engine that does work and can prove it.**

The intelligence is rented and anyone can rent the same model. What is King's is the governance
wrapped around it: it will not invent facts, it records who acted, it meters what the work cost,
it keeps every client's data away from every other client's, and it can be switched off. That is
what turns a clever chatbot into something a business can safely put in front of its own
customers, and it is the only reason there is anything to sell.

## The three pieces

| Piece | What it is |
|---|---|
| **KD's brain** | Memory and law. 923 files. Who he is, what he decided, the rules |
| **The Logos engine** | Hands and evidence. It does the work and leaves proof |
| **The Logoi** | The doors he talks through: voice, journal, money, faith |

**The link runs one way only, and this is the gap that defines the next build.** The engine can
read the brain. The brain cannot fire a mission. Nothing in `commands/` or `tools/` calls the
engine. Closing that loop is what King means by "put the engine in KD's brain": every `/command`
becomes a recorded, grounded, metered mission instead of work that dies with the chat session.
That is the WAT framework finally getting a runtime.

## His instance

**Never on a network, and already true.** Verified 2026-08-24: `:3000` (engine), `:3100`
(Klarnow's instance), `:3200` (the UI) are all bound to `127.0.0.1`. Only LOGOI on `:5056` is
reachable, tailnet only, through `tailscale serve`. His brain, his Logoi, his laptop, his private
GitHub. Nobody else ever runs his instance.

King, this session: *"for my own logos engine i will not connect to network."*

## Klarnow

- A **carbon copy on their own VPS**, both sides updating it. He accepts this means **no switch he
  can press**. What is on their machine is theirs, including if the deal ends.
- Their brain, their business goals, **their own agents**. His Logoi stay his.
- **Both sets of his skills go over, adapted for their business:** the 111 brain commands and the
  four engine workers. This deliberately reverses his 2026-08-23 decision that the four workers
  stay his. He was told it reverses it and chose it anyway.
- Ten percent of what they make with it. Already drafted as a contract debt on gross with an audit
  right (term sheet Term 3). **Not to be re-litigated.**
- **Reporting they fill in**, so their sales sit beside what the engine actually ran. The meter
  counts engine work, not their sales, and on their VPS it never could.
- They **use it themselves and also resell it** as a cloud service to their own customers, so they
  carry the hosting and the data protection duties for those customers, not King.

## The public

Open source, **released from Klarnow World rather than from his instance**, after enough data is
gathered. Tiers by model power and subscriptions. Logos OS as everyone's assistant. Businesses
first, public later.

## The money shape

**Tier on power, never on truthfulness.** The grounding gate, the audit log, the isolation and the
meter go in every tier including the cheapest, because selling a tier that is allowed to invent
facts about someone's business would be selling harm.

| Tier | Underneath | Costs him | They feel |
|---|---|---|---|
| Entry | Local model on his machine | Electricity | ~3 words a second |
| Middle | Fast hosted cheap model | Very little | ~2 second answers |
| Top | The strongest models | Real money per call | Best quality, and the meter is why he does not lose money |

He has measured numbers for the first two on his own laptop, so the difference can be proved to a
buyer rather than described.

## The output versus the generator

Two different things can be sold: **a brain built for a client**, or **the prompt that makes
brains**. King's decision: **it depends on the tier.** Lower tiers receive a brain. The top tier
pays substantially more and receives the generator too, priced to reflect that they never need him
again.

The generators are real files: `_ops/LOGOS_0_KING_PROMPT.md` (36KB),
`_ops/LOGOS_MASTER_PROMPT.md`, `commands/master_prompt.md` (11KB), `_ops/KING_OS_BREAKDOWN.md`,
`memory/reference_wat_framework.md`.

**Attribution protects the claim rather than weakening it.** The WAT framework is Nate Herk's,
taught in his AIS+ course, and King's own CLAUDE.md already says to credit him when pitching. His
own: the prompts he wrote, the build, and "Logic" as the name for the skill layer. Selling an
implementation while crediting the framework is normal and defensible. The only thing he must
never say is that he invented WAT, and he never does.

**Demand, honestly.** Asked who wants their own brain built, his answer was **Klarnow and their
clients**, not separate outside demand. It lives inside the Klarnow negotiation and is not an
independent money door.

## His own commercial terms, verbatim from the 22 August email

Recorded because they are his standing position and they are not written anywhere else. Spelling
untouched. The personal half of that email is guarded in `_private/king_own_words_2026-08-22.md`;
this is the business half, which is not sensitive.

- **An NDA before anything is shown.** *"All parties interested must sign an upfront nda deal that
  by seeing presentation alone you must abide . Rules and terms negotiable per each client
  involved."*
- **Five year terms first.** *"5 year deal contracts will be sign first where each company has to
  work and after 5 faitiful years with metrics to help keep king a float. So essentially the more
  the give king the make 50% back."* At the end of five faithful years they are entitled to a
  share of profits and are free to walk away.
- **The share ladder.** *"King0:client 0 / King4:client 8 can give king more if he wants to
  essentially scale this will look good."*
- **What he keeps even when he takes less.** *"he doesn't care if he makes less as he has none
  people can try abuse deal where he doesn't make a lot but image rights and idea rights are his"*
  and *"The image and rights to use and license this idea is 100% and that's a trademark. Sole
  trader."*
- **The three grounds that never bend.** *"Moral-ethics and legal on these 3 grounds should never
  intercede for 50/50 X/x you work hard you get the benefits."*
- **Client secrets stay the client's.** *"Clients secrets will be only privacy to them via firewall
  and also secrets will be owned by client involved with HS with yubi key sticks and vpn and
  whatever else is needed to protect from attackers."*
- **GDPR by censoring at the boundary.** *"Any where where there is sentive data violating GDPR
  will be sensored."*
- **Ireland first.** *"We will use the Irish constitution to help legally own his idea and
  implement it in school and help Irish economy with machine learning courses and just ultimately
  make Ireland first then whatever next."*

**Claude's note, marked as interpretation:** several of these are already built rather than
aspirational. Per-client secrets behind a boundary is the tenancy and client-key work that is
committed and proven. Censoring at the boundary is `brain_retrieval.py`'s `FORBIDDEN_DIRS` plus
`logoi_gate.py`. The engine already implements his stated commercial safeguards; what is not built
is the paperwork around them.

## The other lanes

King calls the whole system **LLLM**, and had already defined it on 2026-08-21 as for research,
educational and medical purposes, *"100% the philosophy based off King's degree in biomed and his
job"*. This session he added the destination: **his own work and school, and building data centres
in Nigeria**, where the model identifies sites, maps them and structures them. He says his plan
and Goodness's align there.

**THE CONVERGENCE, and it is the most useful thing in this file.** Three things he wants are the
same build:

1. The 3D living world for Logos OS
2. Klarnow's World UI (MapLibre, deck.gl, districts and buildings)
3. Data centre mapping in Nigeria

All three are **a spatial view over live data with state-driven rendering**. And the third is not
a blank page: `_datacentre/` already holds `BRAIN_DCIM.html` and `BRAIN_ONELINE.html` at 868KB
each, plus `BRAIN_RACKS_3D`, `BRAIN_MAP_2D`, `BRAIN_GRAPH` and `BRAIN_REGISTER`. Seven three.js
r160 scenes exist elsewhere in `_ops/`.

**Why the engine and not a chatbot for the data centre lane:** a site assessment that invents a
figure about power capacity or fibre routing is dangerous in a way a marketing caption is not. The
grounding gate is the argument, and it is already built and proven.

## Two constraints to keep raised

- **Medical.** A local model is a legitimate reading and structuring aid for his own study. Never
  a diagnostic authority. Any real person's health data is GDPR special category data with its own
  duties, and running locally helps without removing them.
- **Employment.** The Amazon agreement has been read: no non-compete, and Clause 1 carves out
  inventions *unrelated to Amazon's business*. Klarnow is marketing automation and plausibly
  unrelated. **Data centres are Amazon's actual industry**, so the two ventures do not sit in the
  same place under that clause. Recorded as a fact, not a recommendation. King closed the
  solicitor question on 2026-08-23 and it is not being re-opened.

## The UI, decided this session

Full 3D **living world**, the four Logoi as **places rather than tabs**, Vault navy and gold, the
same on phone and laptop, answers appearing instantly, and he can see it working. He was shown
that full 3D pulls against phone-first and chose impressive anyway, knowing the cost.

**A new requirement not previously captured:** he wants **n8n on the back end so he can see the
flow as nodes**. He asked to be shown a flow view and the existing progress view side by side and
to choose.

**Design from three sources, not a blank page.** Goodness's `04-world-vision.md` and
`05-technical-architecture.md` are a genuinely good specification: six Districts, five Building
states, one pure `renderState(building) -> visualProps` so there is exactly one place where state
becomes appearance, four named atmospheres, and the truth rule that a Building shows `live` only
when the underlying system genuinely is. **Klarnow's four layers (Brain, World, Life, Workers) map
almost exactly onto King's four Logoi**, which is why one design can serve both.

## The one unbuilt thing that unlocks three goals

**The agents are printed inside the machine**, as TypeScript in `src/lib/workers/`. Three separate
things King wants all require them to be records instead:

1. Give Klarnow a copy **without** his personal material
2. Give them their **own adapted** agents while he keeps his
3. **Open source** the engine later

None are possible while the prompts are compiled in. His own plan already calls this the most
important line in it, and `ai-gateway.ts:34` already refuses to persist a system prompt and stores
a `sha256` instead, for exactly this reason. Making agents records finishes the job that comment
starts.

## The order King set

> *"Lets finish engine and everything for myself first once i see how everything is i will know
> what to say and do next."*

His own system first. Verify it, fix it, make it permanent. Then close the loop. Then the living
world. Then Klarnow, then the public. **Nothing Klarnow-facing gets built or sent until he has
used his own system**, including the message to them, because he cannot know what to say about a
thing he has not seen working.

## The conference, resolved

Goodness's `04-world-vision.md` names **26 August 2026** as the conference MVP date, with seven
acceptance criteria. King confirmed on 2026-08-24: **still on, and not his responsibility.**
Recorded so the brain stops carrying it as an unknown, and because what they demo shapes what they
ask him for afterwards.

## Cross references

`_ops/LOGOS_0_MATHS.md` section 4 (his maths, filled from his own email this night) ·
`_private/king_own_words_2026-08-22.md` (GUARDED, why the system exists) ·
[[project-logos-engine-build-2026-08-23]] · [[project-logos-ownership-and-killswitch-2026-08-23]] ·
[[project-klarnow-world-brain-2026-08-17]] · `memory/feedback_coordination_on_point.md` ·
`knowledge/klarnow/engineering_pack/markdown-source/04-world-vision.md`
