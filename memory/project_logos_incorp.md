---
name: project-logos-incorp
description: "PLAN CAPTURED, nothing built. King's long-term ambition to build his own AI company (working name LOGOS INCORP, not finalized), modeled on Anthropic/AWS/Apple/Microsoft, run by a real team (King + Olly + a legal friend + Uncle Tony). Runs alongside, not instead of, MONEY MODE. Read before any LOGOS INCORP work."
metadata:
  node_type: memory
  type: project
  originSessionId: unknown-plan-mode-session-2026-07-17
  modified: 2026-08-06T21:02:41.837Z
---

# 🏛️ LOGOS INCORP — the plan to build King's own AI company

**STATUS (2026-07-17): PLAN CAPTURED, NOTHING EXECUTED.** Nothing incorporated, built, or approved to
execute yet. This runs *alongside* the standing MONEY MODE priority (first euro from already-live
ventures by end of July), not instead of it — do not read this as a pivot.

**Update 2026-08-06: no longer purely hypothetical.** Path B/C is now live through
[[project-klarnow-os-deal]] as the real first case, not a someday scenario, a full working pitch
prototype + deck were built for Klarnow 2026-08-06 (still contractor-scope, £2,400 V1, not yet a
Logos Incorp entity). Still nothing incorporated. Phase 0 (the team sit-down: King + Olly + legal
friend + Uncle Tony) still hasn't happened, and that gap is now more load-bearing, not less, since
real client work is already ahead of the team/legal foundation this plan called for.

**Update 2026-07-21:** the maths/physics study lane (previously "Phase 3, not now") opened EARLY as
**The Book of Creation** ([[project-book-of-creation]], `/study`), King's call, a personal grace-paced
formation lane. It forms the founder (maths ladder tops at linear algebra + probability; engineering
strand = Stage-1 territory) but opens NO LOGOS gates: the Uncle Tony call remains the next hand-step.

## The vision
King already runs a real, working AI-operated brain (WAT framework + the "Logic"/Logos skill layer,
`_ops\CREED.md` + `reference_wat_framework.md`) that powers several live revenue ventures (Faceless
Engine, Hook Engine, UGC Studio, Website Sales, client work). On 2026-07-17 King named a bigger
ambition growing out of that: build his own company, working name **LOGOS INCORP**, modeled on how
Anthropic/AWS/Apple/Microsoft are built, that he legally owns.

## The team
- **King** — AI/data engineering + the vision
- **Olly** — marketing
- **A friend** — legal (incorporation, IP, contracts)
- **Uncle Tony** — senior CS/engineering mentor in his 60s; spent hours on 2026-07-17 validating the
  idea with King by phone and confirmed King "has a real system" but needs a team, not a solo build

## Where this sits vs the rest of the brain
- **MONEY MODE (still standing):** the first euro from live ventures by end of July is unchanged; this
  is a multi-year thread running alongside it, not a replacement.
- **The Foundation (`[[project-foundation-theosis]]`, SEED ONLY):** LOGOS INCORP's eventual profit is
  one of the things that could someday help fund the Foundation. That funding decision stays exactly
  where the Foundation file already puts it — gated on King + Fr Bogdan discerning it together. Nothing
  here loosens or reinterprets that gate.
- **WAT (`[[reference-wat-framework]]`) + the KD Main Brain (`[[project-kd-main-brain]]`):** the
  "Claude → WAT → Logic" stack King wanted built already exists and runs the brain today; LOGOS INCORP
  is about turning that proven engine into a company, not inventing it from zero.

---

## Part 1 — The honest 1-9 (built with Uncle Tony, 2026-07-17 and 07-18, preserved in full)
How a frontier model (like the one King talks to) actually gets built, at the level that's publicly
known (not any lab's internal trade secrets):

- **1 — Compute + infrastructure, before anything else.** A frontier lab first secures tens of
  thousands of specialized AI chips (GPUs/TPUs), wired into huge clusters, plus the power and cooling to
  run them — the literal data-centre layer King already works inside at Amazon (DCEO). The single
  biggest gate: without the cluster, nothing below happens. Frontier-scale clusters cost hundreds of
  millions to billions of dollars and take real lead time, which is why cloud providers (AWS/Azure/GCP)
  renting out that compute is itself one of the biggest AI businesses that exists.
- **2 — Data.** Huge amounts of text (books, code, web, conversation, increasingly images/audio/video)
  collected, deduplicated, filtered for quality/safety, licensed or scraped. Can run into trillions of
  tokens. Getting this wrong (biased, low-quality, copyright-tainted) shows up later as a worse/riskier
  model, so labs invest heavily just in curating it.
- **3 — Pretraining.** The model (a Transformer) learns by repeatedly predicting the next token across
  the whole dataset, adjusting billions to over a trillion internal weights via gradient descent. Pure
  pattern-compression, no concept of true/false yet. Runs into hundreds of millions of dollars in
  compute for a frontier-scale model, weeks-to-months of continuous cluster time — the step that makes
  "build a new Anthropic from scratch" a fundamentally different scale of project than anything else on
  King's plate right now.
- **4 — Instruction-tuning (SFT).** The raw pretrained model is shown curated example conversations
  (question → good answer) so it learns to *follow instructions* instead of free-associating text. Turns
  a raw text-predictor into something that behaves like an assistant.
- **5 — Alignment (RLHF / Constitutional AI / RLAIF).** Human and increasingly AI raters rank candidate
  answers against a written set of principles; that ranking trains a reward model used to adjust the
  main model toward helpful/honest/harmless answers. Anthropic pioneered training against a *written
  constitution* rather than only raw human preference — notably, this is exactly what `_ops\CREED.md`
  already does for King's own system: a written constitution his skills answer to, one layer up.
- **6 — Tool use / agent training.** Extra, specialized training so the model can call external tools
  (read/write files, run code, browse, call APIs), hold state across many steps, reason before acting.
  This is the "agent"/"Claude Code" layer King talks to right now — a distinct training stage on top of
  a plain chat model, not a free side effect of the earlier steps.
- **7 — Evaluation + safety testing / red-teaming.** Run against benchmark tests (reasoning, coding,
  factual accuracy) and deliberately attacked by internal/external red teams trying to produce harmful,
  biased, or dangerous output, before any public release.
- **8 — Deployment + serving infrastructure.** Once trained, the model still needs a production system
  to answer millions of real requests cheaply and fast (quantization, load balancing, caching,
  monitoring, abuse detection) — its own engineering discipline, separate from training, where most of a
  live AI company's day-to-day engineering work actually happens.
- **9 — Continuous iteration.** Nothing above is one-time. Labs cycle data → pretrain → tune → align →
  evaluate → ship → monitor → feed learnings into the next version, on a rolling basis. "The model" is a
  pipeline that keeps running, not a finished artifact.

**The two layers King already has on top of a model — not hypothetical, already built:**
- **WAT** (Workflow → Agent → Tool) — how you *use* a model reliably, not part of building one. Nate
  Herk's framework (attribute to Nate). Fully documented at `[[reference-wat-framework]]`.
- **Logic** (the Logos-named trigger layer) — the `/command` that fires a WAT chain, named after the
  Word (John 1:1) per `_ops\CREED.md`. Already the skill system King uses daily (111+ skills).

So "Logos prompt on top of WAT prompt on top of Claude prompt" is not something to invent from zero —
it is, largely, the actual architecture already running in this brain today.

**The one gap that has to stay honest:**
- **(a) Fine-tuning an existing open-source model** (e.g. Llama-family) on King's own data/voice/style —
  realistic, real-but-reachable cost, exactly where Uncle Tony's depth could matter most.
- **(b) Training a frontier foundation model from scratch** to rival Claude/GPT — needs
  hundred-million-to-billion-dollar compute and a large research team. Not reachable by any team King's
  size without years of proven revenue first.

King already said "I know this is years." (a) is a real near-to-mid-term milestone; (b) is the long-game
moonshot a profitable, proven company could eventually fund.

**Update (2026-07-18):** the 9 stages above are numbered 1-9 per Uncle Tony's call (Stage 1 = the
foundation), replacing the original 0/10/25/40/55/70/85/95/100 percentage-style labels. He also gave two
working principles: saturate each stage near-completion before advancing, and name the real challenge
at each stage before building its strategy. Carried out below as a draft sheet, ready for the next call
with Uncle Tony, not yet reviewed or confirmed by him.

### Stage-by-stage challenge + strategy (draft, 2026-07-18, for review with Uncle Tony)

**Stage 1 — Compute/infrastructure.** *Challenge:* King doesn't own or need to own compute yet; the
real risk is confusing the far-off "own a cluster" milestone with what actually matters today (API and
hosting cost control). *Strategy:* keep routing spend lean (Rule #12's Llama-vs-Claude flag on every
task); don't spend on owned compute before Phase 2/3 revenue justifies it. Uncle Tony's depth becomes
load-bearing only once fine-tuning (Phase 3) needs real rented GPU time.

**Stage 2 — Data.** *Challenge:* the brain's memory/skill logs are a real, growing dataset, but built
for King's own use, not structured as a training or product asset. *Strategy:* keep the existing
discipline (consistent files, no secrets logged) from day one, so it's usable later without a costly
cleanup project if fine-tuning ever becomes real.

**Stage 3 — Pretraining.** *Challenge:* completely out of reach financially/technically right now; the
real danger is vision-excitement pulling time or team energy toward it before the business exists to
fund it. *Strategy:* park this explicitly as the Phase 3 moonshot only, nothing before Phase 1/2 prove
revenue.

**Stage 4 — Instruction-tuning.** *Challenge:* King already has a lightweight, prompt-level version of
this (the Logic/skill layer) — the real question is when a prompted system stops being enough.
*Strategy:* keep refining Logic/skills as the working substitute now; real weight-level tuning only
matters once Path B needs behavior a competitor can't copy by just reading the prompts.

**Stage 5 — Alignment.** *Challenge:* CREED.md is a real constitution, but it's only ever been tested
against King's own use; it's untested against strangers' use if Path B ever sells to outside customers.
*Strategy:* treat CREED.md as a governance document that needs versioning and real testing once anyone
other than King depends on it.

**Stage 6 — Tool use / agent training.** *Challenge:* this is the layer LOGOS already runs in today
(Claude Code + skills + MCP), tuned around King's own workflows; unproven whether it holds up run by
someone else. *Strategy:* keep documenting WAT/Logic patterns (already underway via
`reference_wat_framework.md`) clearly enough that a client or teammate could run it without King
hand-holding every step.

**Stage 7 — Evaluation + safety.** *Challenge:* the existing QA gates (`/qa`, `/qa-master`, `/ship`) are
built around King checking his own work, not a formal "would this embarrass a paying stranger" pass.
*Strategy:* before Path B's first paying customer, run `/qa-master` explicitly reframed as an
adversarial test on behalf of a stranger, not King.

**Stage 8 — Deployment/serving.** *Challenge:* even a Path B product needs real hosting/serving beyond
King's own laptop setup; this is a near-term concern regardless of the "own a model" question.
*Strategy:* decide the actual serving architecture for a first paying customer, with the legal friend,
Olly, and Uncle Tony all weighing in, before signing that first customer up, not after.

**Stage 9 — Continuous iteration.** *Challenge:* the brain iterates constantly for King's own use, but
carries no versioned "release" discipline for anything meant for outside eyes. *Strategy:* once Path B
exists, apply the same trusted-stone/production-gate discipline already used internally
(`_ops\TRUST_LEDGER.md`) to customer-facing releases.

### The saturation gates (draft, 2026-07-18 — the "when is this stage done" test, Uncle Tony's rule #2)
- **Gate 1→2:** the infra layer runs 24/7 lean AND alerts on failure (qa-master class J); zero
  owned-compute spend before Phase 2/3 revenue.
- **Gate 2→3:** a data audit passes clean: no secrets in logs, no contradictions (Rule #19), files
  consistent enough to hand a future fine-tune without a cleanup project.
- **Gate 3 (stays shut):** opens only when Phase 2 revenue is real AND Uncle Tony has given an actual
  fine-tuning cost number, not a guess.
- **Gate 4→5:** every money engine's SOP/skill is written so a stranger could run it; prompted Logic
  demonstrably covers current needs.
- **Gate 5→6:** CREED.md is versioned and has passed a real test against an outside user's use before
  anyone but King depends on it.
- **Gate 6→7:** one full WAT chain has been run end-to-end by someone who is NOT King, without
  hand-holding.
- **Gate 7→8:** a FULL-depth /qa-master pass run on behalf of a stranger returns zero P0/P1 before
  Path B's first paying customer.
- **Gate 8→9:** the serving architecture is decided and signed off by the whole team BEFORE the first
  customer signs, and it alerts on failure.
- **Gate 9 (never closes):** customer-facing releases pass the Trust Ledger production gate; the
  system provably improves month over month.

---

## Part 2 — Three structural paths (King asked to see all of them)

**Path A — Umbrella / holding company.** Fold existing ventures (Faceless Engine, Hook Engine, UGC
Studio, Website Sales, client work) under the LOGOS name; combined profit funds the company (and,
downstream, the still-gated Foundation). King's own WAT/Logic system runs operations internally, not
sold to anyone else. *Pro:* builds on revenue that already exists or is close; lowest new-execution
risk. *Con:* doesn't yet turn the AI system itself into a sellable product.

**Path B — New AI product company.** LOGOS INCORP builds and sells the WAT/Logic system itself — other
businesses pay to run their operations on it. *Pro:* directly matches the "own Anthropic" ambition; real
IP to legally own and defend (the friend's legal skill matters most here — trademarks, licensing,
ownership). *Con:* unproven as a sellable product to strangers yet; needs real discovery with a first
paying customer before it's more than a hypothesis; slower to first revenue than Path A.

**Path C — Both, in sequence (fold in now, productize later).** Start with Path A now (near-term
revenue, low new risk). Once LOGOS is a real, profitable, named entity with a working AI-operated back
end, treat the AI system itself as a second-stage product to package and sell (Path B), using the
umbrella's own operation as the proof/case study. *Pro:* doesn't force a choice today; near-term revenue
funds the long-term ambition. *Con:* slower to reach the "sell the AI system" ambition; needs discipline
not to skip to Path B before Path A is proven.

**Recommended working default: Path C.** Uncle Tony's read ("you have a real system but need a team")
fits Path C best — it explains why a team is needed *now* (to run and prove the umbrella) even though the
eventual ambition (a sellable AI product) is Path B. King can revisit this once the team has actually sat
down together.

---

## Part 3 — Recommended sequence

1. **Phase 0 — Ground it (weeks, not months).** King can explain the Claude → WAT → Logic stack back in
   his own words. First real sit-down with the whole team (King, Olly, friend, Uncle Tony). Friend
   (legal) scopes what incorporating "LOGOS INCORP" (name still pending) actually requires: entity type,
   IP ownership terms for a system built on top of Anthropic's API (King owns his
   prompts/orchestration/brand, not Claude itself). Name gets finalized once not already
   trademarked/taken.
2. **Phase 1 — Prove Path A.** Fold existing ventures under LOGOS using the existing `/new-project` WAT
   scaffold (Rule #14) once the team confirms direction. Near-term revenue continues to matter most
   (MONEY MODE still standing).
3. **Phase 2 — Prove the product (Path B, once Path A is real).** Package the WAT/Logic operating
   system as an actual product with a first outside customer; Uncle Tony's depth + Olly's marketing
   become load-bearing here.
4. **Phase 3 — The moonshot.** Fine-tuning an open model on King's own data becomes realistic once
   Phase 2 produces real revenue and Uncle Tony can scope actual compute cost. Training a frontier model
   from scratch stays the honest long-game horizon, "years away," not a near-term milestone.

Every dollar this ever produces for the Foundation stays under the Foundation's own existing rule: no
action there until King and Fr Bogdan discern it together (`[[project-foundation-theosis]]`).

**How King will know each phase actually worked (not just felt right):**
- Phase 0: the team has actually sat in the same room/call together; the friend has given a real,
  specific answer on entity type and IP terms, not a maybe.
- Phase 1: LOGOS has its own real project structure (`/new-project` scaffold), and at least one existing
  venture is genuinely operating under the new name with revenue attached.
- Phase 2: a real outside business (not King's own ventures) is paying to use the system.
- Phase 3: Uncle Tony has given King an actual number for what fine-tuning would cost, not a guess.

---

## Update 2026-08-06 night: the "everyone" version of Path B named out loud, honest counsel given
King articulated, in a conversation with another Claude instance (forwarded via email, then discussed
here), the fullest version of Path B yet: a personal-to-institutional guardrailed agent network, AWS
and Google as adopters, rolled out to their own members, "everyone, companies to individuals." Full
detail kept in `[[project-logos-for-everyone]]`'s 2026-08-06 update, not duplicated here.

The counsel given, worth preserving as the standing read on this: the underlying pattern (role-based,
guardrailed, learns-over-time access) is real, already independently validated by Klarnow's own written
spec. But "AWS/Google adopt this" is not a realistic go-to-market, they build their own agent platforms.
Nothing here changes Path C or its gates. Klarnow remains the actual Phase 2 test (a real outside
business paying to use the system), Phase 2's gate has not opened yet (nothing signed, no deposit), and
the "everyone" scale of this vision is exactly what Path C already describes as coming *after* that gate,
not instead of it. This session did not move any gate, it named a bigger version of an already-planned
phase, and pointed back at the existing sequence.

## Cross-links
[[project-foundation-theosis]] · [[reference-wat-framework]] · [[project-kd-main-brain]] ·
[[project-logos-for-everyone]] · [[project-klarnow-os-deal]]
