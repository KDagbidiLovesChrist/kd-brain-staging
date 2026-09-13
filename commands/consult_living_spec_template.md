# /consult · Living Spec Template
*Copy this into each project as `CONSULT_SPEC.md`. Every requirement is a row with a status tag (LOCKED / OPEN / NEEDS-FOLLOW-UP / ASSUMPTION). Only LOCKED rows go into the build prompt.*

---

Save as `workflow/consult_living_spec_template.md` (LAPTOP-ONLY: lives outside the synced brain, saved per client project, e.g. `Documents\ollystv-fba-course\`). Copy per client to `<project>/CONSULT_SPEC.md`.

```markdown
# CONSULT SPEC · [Client / Project]        e.g. "Olly · OllysTV FBA Course Site"
Status tags: 🟢 LOCKED · 🔴 OPEN · 🟡 NEEDS-FOLLOW-UP · ⚫ ASSUMPTION · ⛔ SUPERSEDED
Last updated: [date]  ·  Session #: [n]  ·  Build gate: __ / __ MUSTs locked

## 0. CONTEXT  (the "why" · never lose this)
- Who the client is · who their audience is · the business goal · the one success metric.

## 1. REQUIREMENTS REGISTER  (one row per requirement · this is the spine)
| ID | Requirement (plain English) | Layer | Must/Should/Could | Status | Acceptance check (the test) | Owner | Source (who said it, session #) | Notes / dependency |
|----|------------------------------|-------|-------------------|--------|------------------------------|-------|----------------------------------|--------------------|
| R1 | Course delivered as drip-fed modules | scope | Must | 🟢 | Buyer sees module 1 only on day 1 | King | Olly, S1 | none |
| R2 | Pay by one-off OR payment plan | tech | Must | 🔴 | Both options work at checkout | Olly | Olly, S1 | needs Olly's Stripe/Whop answer |
| R3 | Affiliate program | growth | Could | 🟡 | · | Olly | Olly, S1 | phase 2 |
| R4 | Members login area | scope | Must | ⚫ | Buyer logs in, sees their course | King | inferred | CONFIRM next session |

## 2. PARKING LOT  (raised, deferred · nothing gets lost)
- [R3] Affiliate program, phase 2
- "Maybe a community/forum?", needs Olly's decision (decide-by: __)

## 3. DECISION LOG  (append-only · handles changed minds, never delete)
| # | Decision | Date | Status | Supersedes | Why |
|---|----------|------|--------|-----------|-----|
| D1 | Platform = custom sales page → Whop | S1 | Accepted | · | cost + control |
| D2 | Use Skool instead | S2 | Accepted | ⛔ D1 | Olly will pay the €99 + built-in community |

## 4. OPEN QUESTIONS FOR NEXT SESSION  (the drill list = OPEN + NEEDS-FOLLOW-UP rows)
- [R2] Which payment model, one-off, plan, or both?
- [R4] Confirm the login-area assumption.

## 5. THE LOOK  (reference-driven · links, not adjectives)
- LOVE: [link], because… · [link], because…
- HATE: [link], because…
- Brand assets: logo? colours? fonts? (have / build from scratch)

## 6. WEB STACK  (website / course-site / SaaS-style builds only · skip for pure content/automation jobs)
- Build type: component-based (React/Next, needs the stack below) OR simple one-page HTML/Three.js
  (King's plain `/website` flow, no stack needed). Status: [status]
- Stack (free, install per project): shadcn/ui + shadcn MCP · Magic UI · Aceternity UI free tier.
  Paid template (Aceternity Pro ~$199 one-time, verify price + resale licence, or Tailwind Plus
  $299 one-time) only once a paying client is signed AND a specific template proves it saves hours.
  Never a monthly UI subscription (v0 Pro, Lovable, 21st Pro, Framer, Webflow). Status: [status]
- If course/membership platform: front end = King's custom build; login + payments + community =
  client's own Skool ($9-99/mo) or Whop (free, ~6-7% per sale). Log the choice in section 3 (DECISION
  LOG), not as a silent assumption. Status: [status]

## 7. BRAND PRESENCE  (any client with a public-facing/local business only · skip for pure content/automation jobs)
- Google Business Profile claimed + complete (category, hours, 100+ photos, products, Q&A)? [status]
- Review cadence + reply speed (target 3-5/week, replied within 24h)? [status]
- NAP consistency, name/address/phone identical everywhere (site, Google, Facebook, directories)? [status]
- Platform priority if the client asks where to focus (cross-agent consensus): 1. Google Business
  Profile 2. TikTok 3. Instagram 4. Facebook 5. YouTube 6. X/Twitter last.
- Honest expectation on record: local SEO gains show in 3-6 months, not overnight.

## 8. BUILD-GATE CHECK
- [ ] Every MUST is 🟢 LOCKED
- [ ] Each MUST has an acceptance check (testable)
- [ ] No OPEN dependency blocks a MUST
- [ ] Vision · audience · offer · look · pages/features · tech · funnel · 1 metric all LOCKED
- [ ] "OUT of scope for v1" list is LOCKED
→ All ticked? COPY the 🟢 LOCKED rows into the WAT build prompt (STEP 7 of /consult).

## 9. ROLL-UP · THE LOCKED SPEC  (auto-built from the 🟢 rows = the build brief)
> Paste the green register rows here as the final, signed-off requirements that feed WAT.
```

---
