---
name: project-proof-engine-money-plan
description: "King's current money plan to €10k/mo, done-for-you short-form video service + UGC, NOT cold website sales/Upwork. Aunty = client"
metadata: 
  node_type: memory
  type: project
  originSessionId: 86568dfd-2830-4ff9-9d7e-9cb167c320ad
---

# The Proof Engine · King's money plan to €10k/month (started 2026-06-23)

**This supersedes the old "website sales engine / Upwork bidding" money approach.** That was the wrong pond (50+ cold Dublin sample websites → 0 sales; Upwork = no-review stranger losing to strangers).

## The model
Done-for-you **short-form VIDEO service** sold to **content-VALUERS** (creators, gyms, clinics, coaches, cooks, people who already want to grow online), **+ UGC for fast cash.**
- **€10k/mo = 8, 12 retainers × ~€1,000, 1,400/mo.** Sell a "SYSTEM that gets customers," never "X posts."
- **Order:** build PROOF (one real client win) → productize the offer → sell to more content-valuers.
- **The winning sales move (evidence-backed):** outbound + a FREE tailored sample beats building a channel for inbound (first client ~2, 4 wks vs 3, 6 mo). This = King's existing demo-first superpower, aimed at people who VALUE content (not cold tradespeople).

## Hard lessons baked in
- Don't sell "online presence" to people who don't value it (King's 50-website lesson).
- Faceless-AI-ad-money is dead/risky in 2026 (platform bans + AI-disclosure). Dropped as a money plan.
- The 3 tracks are ONE engine: **editing** (the skill, CapCut + daily recreate drill) → trained free on **cooking (Aunty = proof)** → sold as **UGC/retainers** (wellness niche; JoinBrands/Billo/Twirl). The hook never changes, only the price.

## Client #1 = Aunty (Chidi Okonye) "The Buka" · Nigerian cooking, Dublin, done-for-you
FREE as a case study, deal = she films + gives a testimonial + lets King show her results. **Engaged + active (2026-06-26):** first posts going out. Iterated her caption drafts on her feedback (removed a duplicated paragraph in the jollof-spaghetti post; reused it on Post 2 same dish). **Built the starter pack:** order page PREVIEW live = **order-page-pearl.vercel.app** (sample menu, WhatsApp/DM buttons, Revolut/PayPal, swap real details before live), `the-buka\THE_BUKA_GROWTH_KIT.md` (profile/bio for IG+TikTok+YT, 1-cook-into-7-posts + 3x/wk cross-post schedule, SEO/keyword cheat-sheet, YouTube setup). Drafted + emailed King her light next-step ask (3 things: menu+prices, order contact+pay, batch-film 3-5 best dishes). **Pace rule: never push past "cook, film a few clips, approve", scale output, not her workload.** AWAITING: her menu/prices/order-contact + clip batch → then fill order page, go live, start posting + YouTube. Files: `the-buka\`. See [[project-client-work-olly-mum-aunty]].

## Aunty's REAL Instagram (pulled via Apify 2026-06-26 · plan revolves around HER reality)
**@thebukadub** ("THE BUKA", business/Restaurant account). Bio: "Nigerian Food Dublin · A Fresh Taste of
Home · **Pre-order Only (48hrs Notice)** · Dublin · Order via WhatsApp". **Order line: WhatsApp +353 89 973
5175** (wa.me/353899735175). Delivery from 4PM, Dublin & surrounding areas, delivery + pickup. **82
followers, 16 posts, low engagement (3-8 likes).** Posts = text-heavy "AVAILABLE TODAY" flyer graphics, NO
video. **Real menu (her own posts):** jollof spaghetti (2L bowl), party jollof rice, ayamase + ofada rice,
nkwobi, isiewu, oha/ora soup, roast fish platter (catfish/croaker/tilapia), isi-ewu, World Cup specials.
**The gap = the opportunity:** she cooks the real thing but the flyers don't travel → turn her real cooking
into scroll-stopping short-form video → reach + orders jump. **KING'S RULE (2026-06-26): the plan must
revolve around HER, she cooks on pre-order days, so we NEVER tell her what to cook; we ride whatever she's
already making and amplify it. Ask the right discovery questions, don't dictate.** Order page now carries
her REAL menu + WhatsApp (prices still TBC): order-page-pearl.vercel.app. Crew defined in `the-buka\TEAM.md`.

**🆕 2026-06-27:** The Buka is now a proper **WAT project folder** (`the-buka\CLAUDE.md` + `MANIFEST.md` +
workflow/tools/deliverables/sessions). King visited Aunty (going back next day); the real bottleneck = Aunty
can't yet film well or optimize her own account. Built **3 beginner iPhone guides FOR HER** (filming basics,
account/SEO setup, simple toolkit, `deliverables\guides\`), emailed to King. Order page now has **Pay by card
(Stripe) + Revolut + PayPal buttons** (placeholders, wired once she sets up + locks prices). **Standing steers:**
iPhone · **faceless now, introduce her TALKING later** · **Aunty's reference videos = the style guide** (King
sending them; analyse via `/watch`). **⚠️ IMPORTANT LEGAL/SAFETY (from /find-skills, see
`the-buka\workflow\BUSINESS_CHECKLIST.md`):** she legally must **register the food business with the HSE (free,
~28 days before trading, Article 6(2) Reg 852/2004)** even from home; must give **allergen info in writing (14
allergens, free MenuCal)**; food-safety/HACCP + insulated delivery (5-63°C danger zone); take a **deposit on
confirm** (fresh food = no cooling-off refund). Free scheduler = **Metricool**. Content-engine = run (brief locked
IG-home + TikTok/FB/Shorts, goal customers+reach; produce + deeper TSV waits on her clips + reference videos).

## Getting paid
Stripe Payment Link made but stuck in TEST mode + licence verification (he moved, getting new licence), parked. **Revolut + PayPal can receive money NOW** so he is NOT blocked.

## Coaching mode (standing)
King wants to LEARN to judge quality + edit himself. Be his coach, not just builder: the Top-Tier Scorecard + the daily recreate drill (`proof-engine\TRAINING.md`). Grade work against the Scorecard.

## Key files
`C:\Users\Dell\.claude\proof-engine\`, WEEKEND_BRIEF · AUNTY_PLAN · AUNTY_CALL_SCRIPT · SERVICE_OFFER · TRAINING · STUDY_PACK. Plan: `plans\ok-lets-start-making-enchanted-ocean.md`. Latest handoff: `handoffs\handoff_2026-06-23_21-45_save.md`.

## Tooling
Gmail `token.json` missing → send via SMTP (`tools\send_aunty_pack_smtp.py`, GMAIL_APP_PASSWORD), read via IMAP (`tools\imap_check.py`). Restore API token with `google_auth.py` later.
