---
name: project-logos-commercial-model-2026-08-26
description: "King's deployment shapes, tier families and the 2x return pricing built on X as delivered quality, with the two exposures it surfaced"
metadata: 
  node_type: memory
  type: project
  originSessionId: 19b29a34-b90e-4522-a436-ab101179163d
  modified: 2026-08-26T10:13:57.460Z
---

# The commercial model of Logos, as King stated it on 2026-08-26

His words across one session, assembled. Nothing here is inferred beyond what he said, and the
two places where the maths surfaced a problem are marked as HIS RULING NEEDED rather than solved.

## What is actually being sold

**He hosts the engine.** Tiers go out through Klarnow for business purposes, and he also serves
businesses directly alongside that. In his words: *"i will be hosting the engine but we be doing
tiers through klarna for business purposes but i will also help business on the side aswell as
klarnow."*

**The client picks the cloud.** *"i will put my engine in whatever cloud they want and work in it
depending on pricing, or they can work on cloud and engine themselves per logos app and have
access to back."* So two deployment shapes, and the support cost is the same in both:

| shape | who carries infrastructure | who carries his time |
|---|---|---|
| he hosts, in their chosen cloud | him, billed on | him |
| they run it themselves via the Logos app | them | still him |

**The foundation prompt is never sold, at any tier, in any shape.** *"master prompt foundation
prompt can never be exposed to any party but me."* What a client receives is **their own master
prompt sitting on top of his**: *"they only get their own master prompt on top of mine to help
build their infrastructure."* The layer underneath is not part of the transaction. This is the
same boundary as [[project_logos_ownership_and_killswitch_2026-08-23]] and is not a new decision,
it is that decision applied to the product surface.

## Three families, each with its own tiers

*"we have business models, school economic models and personal models and each have tier systems
based off network, ec2 and prod."*

- **business** pays for outcomes, carries commercial risk
- **school and economic** pays from a fixed budget, values the audit trail, cannot absorb surprises
- **personal** pays for themselves, and the free local lane genuinely serves them

Tiers are **network, ec2, prod**, his own trade language, and they are **size, never
truthfulness**. The grounding gate, audit log, isolation and meter are identical in the cheapest
tier and the dearest. This restates the 24 Aug rule and is now enforced in `logos_pricing.py`
through a single shared `CEILING` per tier with no separate honesty setting anywhere.

## The pricing logic, and where X sits in it

*"i want 2x return for myself so we need logic to help calculate depending on data of clients
wanting to buy infrastructure"* and *"which will depend on their X = overall quality."*

Built as `tools/logos_pricing.py`. The structure:

```
cost to serve  =  infrastructure  +  model spend  +  HIS TIME
list price     =  cost to serve   x  2                        <- his floor
billed         =  list price      x  (q / ceiling)            <- what they actually got
```

**q is delivered quality as a fraction of X**, and it is never 1.0, because X is a limit and a
price claiming q = X would be claiming the ceiling had been touched. Ceilings: network 0.72,
ec2 0.86, prod 0.94.

**q is built from numbers the engine already records**: agreement across independent runs,
whether the grounding gate passed, and what share of claims traced to something real. Weighted
toward honesty on purpose, so a confident invented answer scores below an uncertain true one.

**The product idea this unlocks, and it is genuinely unusual: the client is billed for the
quality actually delivered, evidenced by the engine's own audit log.** An amber month bills less
than a green month and the client can read why rather than taking anybody's word. Almost nobody
sells this, because almost nobody can prove it. He can.

## THE TWO EXPOSURES THE MATHS SURFACED. Both need King's ruling.

### 1. A failed month currently bills ZERO while costing him a full month

If grounding fails, `q = 0`, so `billed = 0`. On a prod client that is **zero income against
1,115 euro of real cost, his time included**. The logic is philosophically right, work containing
an invented claim has no quality to sell, and it is financially unsurvivable as written.

The obvious middle is a **floor at cost**: he recovers what it cost to serve and forfeits the
margin. He keeps the honesty, the client sees the failure priced in, and he does not fund their
bad month out of his own. **Not implemented. His call, because it is his risk and his
relationship.**

### 2. His time is 65 to 78 percent of the cost at every tier, and it does not divide

| clients on one box | cost to serve | infrastructure each |
|---|---|---|
| 1 | 342.00 | 90.00 |
| 3 | 282.00 | 30.00 |
| 10 | 261.00 | 9.00 |

Ten clients on one box saves **24 percent**, not 90, because infrastructure divides and his
attention does not. **This is the single most important number in the model.** The business only
scales when the engine absorbs the support hours, which is a build decision, not a pricing one,
and it points straight back at the same unbuilt item: agents as records, so a client's own master
prompt can configure their behaviour without him editing TypeScript for them.

## What is estimate and what is measured

- **MEASURED**: model spend, from the meter that is already running.
- **ESTIMATE, marked in the code, not yet quoted**: every infrastructure figure. These must be
  replaced with real quotes before any of this is shown to a buyer.
- **HIS TO SET**: the hourly rate, defaulted to 60 euro and deliberately a variable. It is what
  he chooses to value an hour of his life at, not a market claim.

## Related

[[project_logos_os_whole_picture_2026-08-24]] . the tier rule and the generator versus output
distinction this pricing implements.
[[project_logos_ownership_and_killswitch_2026-08-23]] . the ownership position the prompt
boundary comes from.
[[feedback_wisdom_and_knowledge_division]] . why the pricing tool reports numbers and declines to
rule on them.
