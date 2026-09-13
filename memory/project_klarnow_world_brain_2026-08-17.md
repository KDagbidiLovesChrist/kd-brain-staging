---
name: project-klarnow-world-brain-2026-08-17
description: "17 Aug 2026 work, recorded 22 Aug: the Klarnow World brain repo, the Logos engine service contract (api/world, per tenant audit, actor header, second instance on 3100), two real client missions run end to end on the local model, and a FIFTH verbal cap table version"
metadata:
  node_type: memory
  type: project
  modified: 2026-08-22
---

# Klarnow World brain + the Logos engine service contract · 17 August 2026

**Type:** project · **Status:** built and run 17 Aug, recorded 22 Aug, five days late
**Plan, the full record:** `plans\hey-i-am-with-synthetic-stream.md`
**Repos:** `projects\klarnow-logos-sandbox\engine` (King's engine) · `C:\Users\Dell\Klarnow\klarnow-world` (Klarnow's brain)

## Why this file exists

Stage 5 of the 17 Aug plan, the records step, never ran. No memory file, no MEMORY.md line, no
handoff, and `klarnow-world\handoffs\` was empty. A grep of the whole KD brain for `klarnow-world`
returned nothing. So every session after 17 Aug believed the Logos engine last moved on 16 August
and that the isolation stage was untouched. Both were false. This closes that gap. Rule 19.

**Read the dates literally: this is 17 August work written down on 22 August. It is not fresh movement.**

## What was built

**Two brains that talk, on purpose.** Logos (Diagnose, Builder, grounding, approval) stays on King's
side and Klarnow's brain calls it over HTTP. King's engine IP and master prompt never cross. King's
words on the split: "the 10% he won't get but doesn't need."

**1. The engine service contract** (King's side, `engine\standalone-server.ts` + `prisma\seed.ts`):
- `GET /api/world` and `GET /api/world/<slug>`, token gated, a JSON read model (`tenantWorld()`)
  carrying missions, briefs, assets, pending approvals and recent audit rows.
- Per tenant audit view through `listRecentAuditEventsForTenant` (`src\lib\db.ts:226`).
- `actorOf(req)` reading an `x-logos-actor` header, wired into `/command`, `/approve` and `/reject`,
  replacing the hardcoded actor "king" so a partner instance records its own people.
- Tenant lookup by slug, JSON responses on command, diagnose, build and on Builder refusals, and a
  `LOGOS_INSTANCE_LABEL` so a partner's page never carries King's name.
- `scripts\start-klarnow-instance.ps1`: a second instance on :3100 with its own `klarnow.sqlite3`,
  its own token and its own seed profile. V0 on :3000 untouched.

**2. The Klarnow World brain** (`C:\Users\Dell\Klarnow\klarnow-world`, its own git repo, 2 commits):
29 skills and 8 Workers on disk (the first commit says 18 skills, the Loop commit added the rest),
`_ops\` with CANON, LEXICON, ACCESS, APPROVAL_TIERS, PROVIDERS, CAPABILITY_REGISTRY and THE_LOOP,
three Worlds (klarnow the Sun, chopiva and clypme the planets), a World HQ, and nine test files
including `test_no_secrets.py`, `test_world_isolation.py` and `test_masking_by_role.py`.
Second commit, 19:15: "The Loop is the spine: ten stations 0 to 9, gates enforced, laps that close
only when whole, the World View drawn as the ring."

## The proof, and it is the strongest this project has

Two real client missions ran end to end on qwen3:8b, local only, through the Klarnow brain into the
engine over HTTP. Logs: `klarnow-world\sessions\chopiva_run_2026-08-17.log` and `clypme_run_...log`.

- **Chopiva: RED.** Brief 147 s, build 285 s, 4 assets, 432 s total. The grounding gate caught
  **1 violation in 11 specifics checked: [invented] "9 out of 10 ratings from real people"**, and
  held it out of publication behind a typed reason.
- **ClypMe: AMBER.** Brief 38 s, build 259 s, 4 assets, 298 s total, 3 advisory notes.

That is the engine refusing to invent a fact, in a live client shaped run, unprompted. It is the
demo. It is also the answer to the "80% increase" problem from 09 Aug: the engine will not let a
number that has no source reach a client.

## Decisions recorded 17 Aug (none of them signed, none encoded into Klarnow files)

- **Engine as a service.** Logos stays King's, reached only as an endpoint. `_ops\PROVIDERS.md` on
  the Klarnow side names it "Logos engine, external service, endpoint + token", no name, no repo
  path, no prompt.
- **Local only**, both sides, Ollama qwen3:8b, nothing leaves the laptop, zero credits.
- **His Lexicon stands.** World / District / Building / Mission / Proof / Chronicle / Worker as
  Goodness defines them. Sun = Klarnow World tenant zero, planets = client Worlds.
- **No secrets is a test, not a promise.** `tests\test_no_secrets.py` fails the build on any hit.
  Anything secret shaped that must be displayed renders as ******** (King's own word for it).
- **King's two roles, and only two:** the maths (Logos as a service) and the structure (upgrading
  Klarnow's brain architecture). Klarnow's own people fill it and run it.

## ⚠️ THE KLARNOW TERM: BOTH 10% of the company AND 10% of sales (King, 22 Aug) + what the public register actually shows

**King's own words, 22 Aug:** "i make 10% of its sells klarnow keeps other 90%", then "my engine and
any work automatically is 10% of klarnow 10% belongs to me of klarnow cost". Asked to settle it, King
confirmed: **BOTH.** He owns 10% of Klarnow the company, AND takes 10% of what clients pay. The engine
and any work he does earn him both.

### Two corrections Claude made on 22 Aug, both Claude's errors

1. **Filed as "equity" when King's first statement was a revenue share.** The 17 Aug plan
   (`plans\hey-i-am-with-synthetic-stream.md` line 10) put it under the heading "Equity, memory only"
   and Claude copied that through. Settled now: it is both instruments, not one.
2. **Category error: Klarnow and Theosis are DIFFERENT COMPANIES.** Claude filed a Klarnow ownership
   line into the list of clashing **Theosis** cap tables. Theosis is King's company and Logos is its
   product (confirmed by King 08-08, `project_robot_logos_ownership_2026-08-08.md`). Klarnow Ltd is
   Goodness's registered UK company. **The three clashing cap tables are Theosis. The 10% is Klarnow.
   They are not the same table and must never be merged again.**

### 🔴 COMPANIES HOUSE, checked 22 Aug 2026 (public record, free, anyone can repeat it)

**KLARNOW LIMITED, company number 16544261.** Incorporated **26 June 2025**, status Active.
Registered office Suite 12 St James House, Pendleton Way, Salford, Manchester, M6 5FW.
SIC 62012 software development, 73200 market research, 82990 other business support.

- **Officers: ONE.** Dada, Goodness Olawale, Director, appointed 26 June 2025, Nigerian.
  **Moyo is not a registered officer of the company.** CTO is a job title, not a Companies House role.
- **Persons with significant control: ONE.** Goodness Olawale Dada, **ownership of shares 75% or more,
  voting rights 75% or more, right to appoint or remove directors**, notified 26 June 2025.
- **Entire filing history, three items only:**
  - 26 Jun 2025 NEWINC, incorporation, **statement of capital GBP 1**
  - 07 Dec 2025 AD01, registered office moved from Kay Street Manchester to Salford
  - 20 Jul 2026 CS01, **"Confirmation statement made on 25 June 2026 with no updates"**
- **No SH01 (allotment of shares) has ever been filed.**

### What that means, stated carefully

**As of the last filed record, King owns 0% of Klarnow Limited.** A 10% holder would NOT appear on the
PSC register, since that threshold is 25%, so PSC absence alone would prove nothing. But **zero SH01
filings plus a confirmation statement dated 25 June 2026 saying "no updates" means the share structure
is unchanged since incorporation.** Goodness holds 75% or more; on a one pound company with a single
director it is likely the whole of it (inference, not a filed fact).

**This is not evidence of bad faith.** The conversations are from August 2026, after the 25 June
statement date, and shares can be issued at any time. It is evidence that **"automatically" is not
accurate.** Nothing about King's 10% exists in law yet.

**Three practical consequences:**
1. **Share capital is GBP 1.** You cannot hold 10% of a single share. To give King 10%, Klarnow must
   **issue new shares**, and an **SH01 must be filed within one month of the allotment**. That is a
   specific, cheap, checkable act with a legal deadline attached. Its absence is visible to anyone.
2. **The next confirmation statement is due around 25 June 2027.** With no action, the public register
   will say King owns nothing for roughly another ten months.
3. **A 10% minority here carries almost no power.** Goodness holds 75%+ and the right to appoint and
   remove directors. King would sit below the **25% needed to block a special resolution**, could not
   force a dividend, could not appoint a director, and **would be diluted on any raise unless the
   document protects him**. 10% of a company he cannot influence is worth what someone eventually pays
   for it, and nothing before that.

**The revenue share is the stronger and faster half.** 10% of sales is contractual. It does not depend
on the share register, does not dilute, and can be made real with one page. **The ownership half needs
an SH01 or it is a conversation.** Pursue both, but do not wait on the slower one.

### The lever King already owns

**The engine writes its own immutable audit log of every Mission.** A share of sales is a share of a
number only Klarnow can see. King does not need to trust their count: **his own audit log is the
count, and neither side can edit it.** Tie payment to it and the measurement problem never arises.

### The maths, so the number is not abstract

King earns `0.10 x price x paying clients` monthly. The $400/mo tier was flagged 09 Aug as roughly
twice the ~$200/mo market ceiling, so the defensible price is the lower one.

| clients | at $200/mo | at $400/mo |
|---|---|---|
| 10  | $200/mo   | $400/mo   |
| 25  | $500/mo   | $1,000/mo |
| 50  | $1,000/mo | $2,000/mo |
| 100 | $2,000/mo | $4,000/mo |
| 250 | $5,000/mo | $10,000/mo |

King's current spare is roughly €550 to €600/mo. At $200 pricing that is about **25 to 30 paying
clients to add the same again**. He controls none of price, volume or sales effort.

**Costs decide whether the 10% is real money.** Compute reads as Klarnow's cost in their own words:
`tools\router.py` quotes the master build prompt, "They buy Klarnow. Klarnow pays and manages the
underlying intelligence infrastructure", and `ROUTER_POLICY.json` sets £3 per Mission and £15 per day
ceilings. **Hosting the engine is unsettled.** If King hosts, it comes out of his 10%. On the LOGOI
figures for the same model class, matching the laptop is roughly €20 to €40/mo and a fast box is €100+.
At €100/mo hosting and $20 per client he needs 5 to 6 clients just to break even.

### Before any paper is signed

1. The ownership half: how many shares, issued when, and **is the SH01 filed**? Until it is, it is talk.
2. Anti-dilution, or at minimum pre-emption rights, so a raise does not quietly erase the 10%.
3. Revenue share: 10% of **gross**, or of net after Klarnow's costs? Net can be zero forever.
4. All Klarnow revenue, or only sales the engine touches?
5. Renewals and upsells, or first sale only? A subscription product lives on renewals.
6. **Is there a floor?** A minimum monthly regardless of their sales performance.
7. Who pays to host the engine?
8. Term, termination, exclusivity. If they stop selling or drop King, do they keep using it?
9. **Payment computed from King's own audit log**, not from an invoice he cannot check.
10. How does this sit with the "personal 50/50" stated the same 17 Aug day, still unreconciled?
11. The still unsigned Preliminary Founder and IP Protection Agreement binds **Klarnow Ltd only**, not
    Goodness personally. See [[project_logos_maths_and_agreement_2026-08-09]].

## What is still open on the engine

- **Guard test missing on the engine side.** Isolation is enforced in Python
  (`world_state.filter_for_actor`), not in the engine.
- **One token opens the whole instance.** `/api/world` with the single `SANDBOX_TOKEN` returns every
  tenant's missions, briefs, asset content and audit rows. `authorised()` says so itself: sound for a
  single user loopback sandbox, not sufficient once a second party holds the token. A partner brain
  holding it is exactly that case.
- **`GET /` hands the operator token to any loopback GET** as an HttpOnly cookie.
- The legal gates are unchanged and still block anything client facing: the cap table, the unsigned
  Founder and IP agreement, the unread Amazon contract, and the Commercial Anthropic account
  precondition the moment real client data enters ([[reference_anthropic_data_terms]]).

## Links

[[project_klarnow_os_deal]] · [[project_logos_sovereignty_2026-08-15]] ·
[[project_logos_maths_and_agreement_2026-08-09]] · [[reference_anthropic_data_terms]] ·
[[feedback_verify_route_by_last_run]] (this file is that rule proving itself: the dashboard was wrong
and only reading the disk showed it)
