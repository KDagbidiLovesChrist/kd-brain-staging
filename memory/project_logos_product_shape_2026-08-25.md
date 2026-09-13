---
name: logos-product-shape-2026-08-25
description: The four products King specified out of one engine, who sees what, and what each one still needs
metadata:
  type: project
---

**2026-08-25, said across a long session.** King specified what Logos actually sells. It is four
products out of one engine, not one product with tiers, and they have opposite jobs.

## The four

**1. BUSINESSES, strictly business use.** His words: *"most companies have agents and ai systems
and data and bedrock like aws. this engine should simply connect and do the rest."* So for a
business Logos is **not** the intelligence. It is the layer that connects to what they already
run and makes it provable, governed, metered and isolated. They keep Bedrock, their own agents,
their own data. Logos governs it.

**2. INDIVIDUALS AND INFLUENCERS.** The opposite job. His words: *"you a youtber that edits
videos and all that, this will do it for you, help you manage business and personal how i do."*
They have no existing stack, so Logos **does the work**, the way it does for him. He has test
people in mind already, to help them build their world, structure their life and goals, and plan
everything.

**3. LOGOS CODE, open sourced.** His words: *"a logos code version where people can do what i do
with you claude code, open sourcing it."*

**⚠️ THE CORRECTION THAT MAKES THIS EASIER: he cannot open source Claude Code, and does not need
to.** Claude Code is Anthropic's CLI. Almost nothing he values about how he works is Claude Code
itself; it is the layer he built around it, and that layer is entirely his AND is provider
neutral. His gate does not care whether the model is Claude, NVIDIA or local.

    RELEASABLE: the brain structure, WAT commands and tools, logoi_gate.py, logos_policy.py,
                the ccr custom router, the memory and handoff loop, the audit and grounding
                discipline
    NEVER:      his _ops master prompts, anything client specific, the-truth/, _private/, legal/

That is **open core**: give away the frame, sell the brain that goes in it, the generator that
makes brains, the hosted service and the 3D world. **And it is honest rather than a sales trick,
because his own measurement proves it:** a thin brief made the engine invent *"people who buy
hooks for faceless characters in games"*; his full brief passed grounding. An empty frame does
nothing useful, which is a fact and not a limitation he invented.

**4. THE 3D WORLD, and clients see nothing else.** His words: *"they will only deal with
immersive and impressive 3d front end for clients."* Half enforced already: `prove-client-keys`
shows a client key gets 401 on the operator console and the refusal does not leak another
client's name. They structurally cannot reach the back office. **What does not exist is the
front they DO see.**

## Who sees what, which is already built

    the engine        :3000   nothing human, just the machine
    the deck          :3200   HIM, the operator. clients get 401
    LOGOI vault       :5056   him, his personal door
    a client's view   API only, JSON, no interface exists
    the 3D world      does not exist. THIS IS THE MISSING HALF OF THE PRODUCT

## Deployment and hardware, settled

**GPU is only needed where the thinking happens, not where the code runs.** The engine is a small
web server plus SQLite and runs on the cheapest VPS. Klarnow's clients will be on rented models,
so their VPS can be cheap rather than powerful; the GPU is the provider's capital expense and
arrives as tokens instead. **The one exception: any tier promising "nothing leaves your machine"
must run local models, so that tier needs a GPU and should be priced for it.** That top tier is
also the hardest for a competitor to match.

## Revenue and the loop King stated

Clients pay for their own storage; profit is reinvested into infrastructure; **the destination is
building data centres**, mapped and planned by the same engine. `_datacentre/BRAIN_RACKS_3D.html`
already has **42 three.js references**, so the 3D world is not a blank page.

Onboarding is **an interview, not a signup link**, and `/consult` already exists and already
hands its living spec off as the WAT build prompt.

## What is genuinely missing

- **The 3D front end.** The missing half of the product.
- **Self-serve signup and tiers.** Tenants are hand-seeded in `prisma/seed.ts` today.
- **ROLES INSIDE A TENANT.** King wants employees connecting with admin restrictions and keys.
  Keys today are per TENANT, one key per world. Employees at different levels inside one company
  is a schema addition, not a config change.
- **Agents as records rather than TypeScript.** Now blocking FOUR things: giving Klarnow a copy
  without his material, adapting agents per client, open sourcing, and the fan out dispatching
  his 111 commands.

## Attribution, his own standing rule

WAT is Nate Herk's, from AIS+. "Logic" is King's naming. His CLAUDE.md already says to credit
Nate when pitching, and **releasing publicly makes that more important, not less.**

## Cross references

[[project-lllm-logic-layer-2026-08-25]] · [[project-logos-jarvis-mode]] ·
[[project-logos-os-whole-picture-2026-08-24]] · [[project-klarnow-world-brain-2026-08-17]]
