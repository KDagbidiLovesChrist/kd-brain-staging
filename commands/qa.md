# /qa · The QA Gate (King's 8-Stage Release Pipeline)

**Trigger:** `/qa`, or "QA this", "gate this", "is this ready", before anything is called done or shipped.
**Purpose:** Make sure every task, no matter how small, is taken to top-tier quality and proven true before it reaches Production (the 24/7 brain). Emulates a top design and SRE team's release process. Part of THE KD MAIN BRAIN (see `plans\purring-chasing-quill.md`). Pairs with `/ship`. It is the **0 → 100 build-up arm of the Foundation Pipeline** (`_ops\FOUNDATION_PIPELINE.md`); when a thing reaches Production, `/ship` logs it as a **trusted stone** in `_ops\TRUST_LEDGER.md` (trust compounds, the next QA leans on what's proven).

## The rule
Nothing reaches Production unverified (Rule #21). Depth is scaled to stakes:
- FULL 8 stages for money, faith, client-facing, security or data, or anything irreversible.
- LIGHT sanity-check for trivial mechanical steps (lean-spend; do not choke throughput).

## Every task records (the WHAT / WHY / HOW)
- WHAT it is.
- WHY we are doing it (the goal it serves).
- HOW it aligns with the goal and with God (theosis first, money as fruit).

## The 8 stages
1. Spec / Consensus. Define the proven best standard via `/find-skills` plus multiple independent verified sources. Show the maths and the why (consensus error falls about 1 over the square root of N). No copycat or correlated sources (that is fake consensus).
2. Build. Make it.
3. Tested. Claude self-verifies against the reference and real data. Honest pass or fail. "It rendered" is never the bar. **Run this stage with `/qa-master`** (the adversarial verification gate, 2026-07-04): evidence rules, failure classes A-I, P0-P3 severity; FULL depth adds a second agent that tries to refute the PASS.
4. Approval. King reviews the real result (batched, so King is not the bottleneck). The human gate.
5. Trusted / Staging. It runs reliably over a trial period (lives in `.tmp` / staging).
6. Production. Promoted live into the 24/7 brain. Done via `/ship`.
7. Monitor + Fallback / Doomsday. Backups, rollback, failover. Heaviest where client or sensitive data lives.
8. Improve loop. Measure (goal lens `tools\goals.py`) then improve. Never ends.

## 🔍 The Edge-Case Question Sweep (King's technique · ask everything, least → max)
Before building, shipping, or deciding, run a deliberate sweep of questions to surface edge cases and failure
modes **before they bite**, a realistic, human pre-mortem, done in **humility** (we don't know everything),
**for theosis** (the questions serve King's growth + God's order, not just correctness; *"in the multitude of
counsellors there is safety"* — Prov 15:22; *"count the cost"* — Luke 14:28). **Live example:** the dongle was
red because we never asked *"is there even a SIM in it, and is it activated?"*, the sweep catches exactly that.

Ask, least → max:
1. **Clarity:** what is it *exactly*? why? who for? what does "done / working" look like?
2. **Assumptions:** what am I taking for granted that could be false? *(the #1 source of edge cases, e.g. "assumed the dongle had a SIM").*
3. **Small failures:** typo, wrong file, missed step, stale info, off-by-one.
4. **Big failures:** data loss, secret/security leak, breaks the live brain, money lost, a faith/doctrine error.
5. **Doomsday (max):** if it ALL fails, laptop dies, Claude gone, King unavailable, power/signal lost, what's the recovery? (→ `_ops\DOOMSDAY_AND_24-7_ENGINE.md`).
6. **What's missing:** what haven't I asked? what would a top expert ask? what would an adversary exploit? what depends on something unchecked?
7. **Goal + God:** does it serve the goal (theosis first, money the fruit) + the faith (doctrine → Fr Bogdan)?
8. **Realistic-human:** is it within what life allows, King's shifts, energy, money, non-technical reality (the realistic / provisional lens)?

**Depth scales to stakes** (Rule #21): a quick mental sweep for trivial steps; the full written sweep for
money / faith / security / irreversible. Pairs with **`grill-me`** (relentless interview), Rule #13
(discovery-first), and Rule #17 (consensus).

## File staging maps to the stages
- `.tmp` / experimental = sandbox (stages 1 to 3).
- King's Approval (stage 4) plus a Trusted trial (stage 5).
- `Documents` / live = Production (stage 6), via `/ship`.

## Guardrails
- Sacred accuracy (Rule #20): verified, cited, correct, especially anything touching God.
- No self-contradiction (Rule #19): flag any contradiction before proceeding.
- Faith items: route all doctrine to Fr Bogdan. Claude is a study aid, never the authority.
- Loops and automation: budget cap, rate limit, monitoring, kill-switch, idempotency.
- Love is the root (Rule #23). Never neglect King or his rest (Rule #24).

## Output
A short QA report: the stage reached, pass or fail per stage, the WHAT / WHY / HOW, the risks, and the recommendation (hold, fix, or ready for `/ship`).
