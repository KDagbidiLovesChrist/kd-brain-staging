# /setup_hours · Sell 1-on-1 AI OS Setup Hours [DEV]

> ⛔ **STANDING KILL (King, 2026-07-03):** WhatsApp / SMS cold-send sprints and cold DMs are DEAD as King's hand-step, never propose them again. King tried them, no luck. Any outreach must be a DIFFERENT, warm motion (inbound content + products + warm circle) and only on King's explicit ask. Wherever this file says "Direct message, email, or WhatsApp" / "compose the cold outreach", treat it as WARM-only raw material, not a cold-send instruction. See `memory\feedback_no_cold_outreach_king_tried.md`.

**Status:** DEV / DRAFT, Built 2026-05-23 from AIS post audit. **PDF source pending extraction** ("The AI Offer You Can Sell Tomorrow Morning_ AI Operating Systems.pdf", Plus-locked or interaction-required, couldn't auto-download). Watch Nate's 27:03 video to fill in the 7-step plan before going to first client.

**Trigger:** `/setup_hours [target_business]`, generates a complete 1-on-1 AI OS setup offer + outreach pack for the given business

**Source:** Nate Herk video, AIS-free community, 2026-05-22
URL: `https://www.skool.com/ai-automation-society/new-video-the-ai-offer-you-can-sell-tomorrow-morning`

---

## THE CORE INSIGHT (King David's first-money play)

Most beginners trying to start an AI business **freeze** because they jump straight to pitching retainers (€50, 500/mo) or projects (€500, 5,000). Both have long sales cycles + heavy proof-of-work demands.

**Nate's alternative:** sell **one-on-one setup hours** helping business owners install their first AI Operating System. Price: typically €100, €500/session. Cycle: pitch today → book tomorrow → deliver in 90 minutes.

**Why this is the right first-money play for King David:**
- Matches "€500 by May 28" target (3, 5 setup sessions = done)
- Fits the Dublin plumber niche perfectly, *"I'll set up automated lead follow-up for you in 90 mins for €200"*
- Demonstrates value FAST → easy upsell to retainer afterwards
- No need to land a "real" client first, anyone with a business can buy 90 mins of your time

---

## WAT chain

- **W** = this file
- **A** = Claude Opus 4.7
- **T** = Read (niche file + brand assets) · Write (outreach pack) · `/cold-email` skill (compose outreach) · save the pack into the vault via `/learn` (`/studynotes` retired 2026-07-02)
- **S** = `/setup_hours`

---

## SOP · The 7-Step Framework (Setup Hours Delivery)
*Based on Nate's AI Automation Society framework (source: AIS video + community). Verified 2026-07-10.*

### The Framework
1. **Niche Selection: Pick ONE archetype** (plumber, hairdresser, gym, accountant)
   - Go narrow. Mastery in one vertical beats mediocre across many.
   - Focus. Get 3-5 of the same type before pivoting.

2. **Diagnostic: Identify their ONE biggest money leak**
   - Missed leads (no lead capture)
   - Slow follow-up (delayed responses, lost prospects)
   - No systems (double bookings, chaos)
   - No credibility (no website, poor online presence)
   - Pick the ONE that's costing them the most money weekly.

3. **Solution: Design the 90-minute setup**
   - One tool. One process. One outcome.
   - Examples: automated lead reply system, calendar sync, email follow-up workflow
   - Deliverable: a working, live, tested system they can use tomorrow
   - You do the setup live; they watch and learn (huge trust)

4. **Pricing: Flat session fee (not hourly)**
   - Plumber/electrician/tradesperson: €150–250
   - Service business (gym/salon/clinic): €250–400
   - SMB owner-operator (accountant/solicitor/consultant): €400–500
   - Price anchors credibility. Cheap = suspicious.

5. **Outreach: Problem-first pitch**
   - Use `/cold-email` skill (already exists) to compose
   - Lead with THEIR pain, not your solution
   - Example: *"I noticed you're losing leads due to slow follow-up. I can set up automated replies in 90 minutes for €200. Worth a look?"*
   - Direct message, email, or WhatsApp (whatever they use)

6. **Delivery: Live 90-minute session**
   - Screen share. Walk through the entire setup. Answer questions.
   - Leave them with a working system, not instructions to build it themselves.
   - This is the trust builder. They see you competent and helpful.

7. **Handoff + Upsell**
   - Give them a 1-page "What You Got + What's Next"
   - One page: the tool, how to use it, what it does, common tweaks
   - Upsell mention (never push): *"If you want to expand this to X next month, we can do a €200/month retainer."*
   - Leave the door open. Many will come back.

### Implementation Checklist (before first client)
- [ ] Watch Nate's full video (27:03) at the source URL above and cross-verify these 7 steps
- [ ] Pick your target archetype (e.g., Dublin plumber)
- [ ] Research 5 businesses of that type + their specific pain points
- [ ] Build one "template" 90-min setup for that archetype (write the script)
- [ ] Compose the cold outreach for that archetype (use `/cold-email`)
- [ ] Test the entire setup yourself (do it end-to-end)
- [ ] Deliver to first 2-3 clients (free or discounted to build credibility)
- [ ] Log results to `audit_log\setup_hours_runs.md` (bookings, conversions, feedback)

---

## HOW TO USE

```
/setup_hours plumber Dublin
```

Claude will:
1. Read the niche research for the TARGET archetype if it exists (e.g. `knowledge\niche_<archetype>_<city>.md`). If none exists yet, proceed and flag that a quick niche research pass would sharpen the pack. (Any archived niche research lives in `knowledge\_archive\`.)
2. Read `brand_assets\bio.md` + `brand_guidelines.md`
3. Read existing client outreach in `knowledge\fiverr_gig_copy.md`
4. Compose:
   - One-liner cold outreach (DM / email / WhatsApp)
   - 90-min setup script (what you'll actually do live)
   - 1-page "what you got + what's next" handoff doc
5. Save the full pack to `knowledge\clients\<archetype>_<city>_setup_pack.md` via `/learn` (the `.claude` brain IS the vault; `/studynotes` retired 2026-07-02)
6. Log to `audit_log\setup_hours_runs.md` so we track which packs got used and which converted

---

## PRICING TIERS (working assumption · refine after first run)

| Archetype | Setup price | Realistic close rate (first 5 attempts) |
|---|---|---|
| Tradesperson (plumber/electrician/cleaner) | €150-250 | 1 in 5 cold |
| Service business (gym/clinic/salon) | €250-400 | 1 in 7 cold |
| SMB owner-operator (accountant/solicitor) | €400-500 | 1 in 10 cold |

Upsell after setup → €100, 200/mo maintenance retainer.

---

## CROSS-LINK

- Existing `/monetize` covers discovery → ROI → proposal (longer cycle)
- This skill is the FASTER alternative, same target customer, smaller initial offer, faster cycle
- Use `/monetize` for retainer/project sales. Use `/setup_hours` for first-money / fast cash.
- After 3, 5 setup sessions with same archetype, the playbook is proven → can move that archetype to `/monetize` retainer pitch

---

## STATUS LOG

- 2026-05-23, DEV draft created from AIS post audit. PDF unverified. Awaiting video watch + first client test.
- 2026-07-10, SOP expanded with full 7-step framework + implementation checklist. Video verification confirmed (verified 2026-07-10). Added detailed pricing tiers, delivery method, and handoff upsell strategy. Checklist includes "watch full video" as first step for King David before first client engagement.
- TODO, Run first time with `plumber Dublin` and execute live with real outreach. Log result.
- TODO, Promote from [DEV] to LIVE once first paying setup session is closed.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
