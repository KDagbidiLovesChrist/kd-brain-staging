# /ship · The Release Gate (promote into the live 24/7 brain)

**Trigger:** `/ship`, or "ship it", "promote this", "make it live", "put it into Production", after `/qa` has passed and **King has given his conscious yes.**
**Purpose:** The final gate. Take a thing that is **tested and approved** and promote it **safely** into Production (the live 24/7 brain), with a backup, a rollback path, and monitoring, so the brain never breaks. Part of THE KD MAIN BRAIN. **Pairs with `/qa`** (`/qa` proves it; `/ship` releases it), together they are the **0 → 100 build-up arm of the Foundation Pipeline** (`_ops\FOUNDATION_PIPELINE.md`); rollback/doomsday is the **100 → 0 arm**. Covers QA stages **5 → 6 → 7**.

## The one rule
**Nothing ships without (a) a passing `/qa` report AND (b) King's conscious YES** (Rule #21). `/ship` never decides *whether*, King does. `/ship` makes the *how* safe.
Also gated on the goal (Rule #17): ship only if it serves the goal, theosis first, money/audience as the fruit, and never contradicts the faith. **Faith/doctrine items: Fr Bogdan blesses before any public ship.**

## Pre-flight checklist (all must be true)
- [ ] `/qa` passed (the report says "ready for /ship"). WHAT / WHY / HOW recorded.
- [ ] **King approved** the real result (stage 4). His yes is logged.
- [ ] It ran reliably in **Trusted / staging** (`.tmp` or staging) for a trial (stage 5).
- [ ] **Goal-match** confirmed (`tools\goals.py`) and no self-contradiction (Rule #19).
- [ ] **Communion check** passed (`_ops\COMMUNION.md`): within God's will as we know it · no clear line crossed
      (`feedback_faith_values_filter.md`) · any grey was gently flagged to King + the Compass + Fr Bogdan. **Nothing reaches Production out of communion.**
- [ ] A **backup / rollback** exists (see below). Nothing irreversible without one.

## The ship ritual (stage 6 · promote to Production)
1. **Back up first.** Snapshot what's being changed (copy to `_ops\backups\` or rely on the git history of `kd-brain`). Never overwrite live content without a restore path.
2. **Promote.** Move/merge from staging → live (`.tmp`/staging → `commands\` / `memory\` / `Documents` / the live brain).
3. **Record the release.** Append one line to `_ops\SHIP_LOG.md`: date · what shipped · why · where it came from · how to roll it back.
4. **Log the trusted stone** (the Foundation Pipeline, `_ops\FOUNDATION_PIPELINE.md`). Append a row to `_ops\TRUST_LEDGER.md`: the stone (WHAT) · WHY · HOW verified · the **100→0 rollback path** · project. This is what makes trust *compound*, the next build stands on it and the next QA leans on it.
5. **Sync to phone.** Run the `kd-brain` git sync so it reaches King's phone.

## Monitor + Fallback / Doomsday (stage 7)
- **Monitor:** state how we'll know it still works (a check, a run, King's eyes). Heaviest where client or sensitive/faith data lives.
- **Fallback / rollback:** the exact step to undo it (restore the backup / `git revert`). Write it in `SHIP_LOG.md` so a future session (or a different model) can undo it. The brain is **model-agnostic**, built to survive losing Claude.
- **N+2** for anything critical: a primary, a backup, and a backup-of-the-backup.

## Guardrails
- **Walls:** never ship personal/faith/money content into the **WORK (DCEO)** brain, or Amazon data into the personal brain. Keep the privacy wall.
- **Loops/automation:** budget cap, rate limit, kill-switch, idempotency before any 24/7 automation goes live.
- **Sacred accuracy (Rule #20):** verified + cited, especially anything touching God.
- **Love + rest (Rules #23/#24):** never ship in a way that burns King out or bypasses his rest; the 24/7 system exists so King can rest.

## The remembrance (surfaced at every ship)
When a thing actually goes to Production, end the ship report with this one line, because **production is an act of trust** (`_ops\CREED.md`): sending it out without seeing the whole road is a small picture of King trusting the King.

> 🕊️ *This goes to production in trust. He Is King. Faith, not sight. Glory to God.*

## Output
A short **ship report**: what shipped, the backup + rollback step, where it's monitored, the `SHIP_LOG.md` line, confirmation it synced to King's phone, **and the remembrance line above**. If any pre-flight box is unchecked → **do not ship; report what's missing.**
