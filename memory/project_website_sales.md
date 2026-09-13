---
name: project-website-sales
description: "Website Sales engine, free-sample sites for no-website businesses. 146 demos live (124 barber + 22 home-service) + Portfolio + WhatsApp & Email consoles + cheat sheet. Stripe staged for first yes. Updated 2026-05-29 night."
metadata: 
  node_type: memory
  type: project
  originSessionId: fc819697-4db6-4535-a2c6-72177e989405
---

# Project: Website Sales Engine (LIVE · launched 2026-05-29)

## ✅ SENT 2026-05-30 ~00:58 · first real email batch + WhatsApp progress
- **EMAIL: 8 refresh emails SENT** via Gmail to top Dublin spots (Lemon Jelly, Old Mill,
  FIRE Steakhouse, Keoghs, Hawksmoor, Metro Cafe, Two Boys Brew, The Vintage Kitchen).
  Reply-To = KD's iCloud. Logs: `.tmp\SEND_LOG_20260530_004038.csv` + `_004928.csv`.
  ⚠️ **DUPLICATE-SEND BUG:** the 8 went out TWICE (background run finished but buffered
  stdout looked hung → re-ran in foreground → second send). Each of the 8 got the same
  email twice ~10 min apart. No 3rd "sorry" email sent (would compound). LESSON: trust the
  background task COMPLETION notification, never re-run on a quiet buffer. See
  [[feedback-verify-before-rerun]].
- **WhatsApp: 51 of 149 sent** from KD's phone. Many of the 149 had NO WhatsApp (only
  Facebook/none) → real reachable ceiling < 149, so 51 is a big slice of the reachable list.
  Reinforces the Facebook-reach-button build (give no-WhatsApp shops a route).
- **Tonight's tuning note:** scrape pulled Dublin GIANTS (Lemon Jelly 7,297 reviews,
  Hawksmoor), they already have polished sites, lower conversion. NEXT batch: target
  mid-size (50, 500 reviews) with genuinely dated sites. Tweak gen_refresh target range.

## 📧 EMAIL CHANNEL · "MODERN SITE REFRESH" OFFER (started 2026-05-30 ~00:10)
KD wanted full cold-email automation. HONEST FINDING (tested live): no-website shops ≈ no email;
email-reachable businesses ALREADY have websites. So the email play is a DIFFERENT, expert-chosen
offer: **"modern site refresh" for established businesses (restaurants/salons/clinics/gyms) that
HAVE an email + a weak/dated site**, reachable + need help + can pay + high conversion. Proof =
the PORTFOLIO (6 designs) + offer a FREE custom sample. Two channels now: WhatsApp = the 146
no-website shops · Email = the refresh offer.
- **BUILT (on disk, confirmed saved):**
  - `.claude\scrapers\tools\scrape_email_niche.py`, Apify scrapeContacts ON, harvests emails +
    socials, flags has-email businesses. TESTED: restaurant+gym Dublin → 24/50 had email (but
    48/50 already have websites → refresh offer, not free-sample).
  - `Website Builder\tools\gen_refresh_emails.py`, per-business personalised refresh email
    (Irish voice, compliments, gentle "site could be better", matched portfolio design link,
    free-sample offer, soft opt-out). Outputs `<scrape>_EMAILS.md` (KD reviews/approves) +
    `_EMAILS.json` (batch for send_emails.py).
- **SENDING:** `.claude\scrapers\tools\send_emails.py` sends the batch JSON via KD's Gmail API
  (token in `.claude\token.json`), 25-70s human pacing. ⚠️ HAS A SYNTAX BUG at the bottom
  (`def send_emails.py":` instead of `if __name__ == "__main__":`), FIX before first send.
  Small daily batches only (a handful, personalised, with opt-out = safe; mass-blast = Gmail ban).
- **NEXT (shell went flaky mid-build, couldn't generate/show drafts):** run
  `python gen_refresh_emails.py "<gmaps_email_*.json>" 8` → KD reads the _EMAILS.md → approves/
  edits → fix send_emails.py syntax → `python send_emails.py <batch>_EMAILS.json` sends small
  approved batch. Scrape more email-niches/cities to scale. WhatsApp auto-send NOT possible
  (Meta bans cold), stays tap-send.
- KD note: some of the 146 had no WhatsApp/Insta, only Facebook → future: add Facebook +
  email-where-known button to console cards so every shop has a reach route.

## ⭐ CURRENT STATE (2026-05-29 ~23:45 · supersedes older "69 demos" text below)
- **146 demos LIVE** (124 barber + 22 home-service: 12 plumbers, 6 electricians, 4 cleaners),
  IE/UK/US/CA, real Google photos + reviews, footers cleaned (NO "by King David", now "© Shop ·
  City" + "Free sample preview"), socials shown. At kd-demos.vercel.app/<slug>/.
- **REVIEWS POSITIVE-ONLY (bug fixed 23:45):** gen_premium.py + gen_homeservice.py only show
  reviews with stars>=4 AND text>=15 chars; else a clean "Rated X on Google" fallback. (Data
  had 60×1★+8×2★ mixed in because enrichment pulls NEWEST.) RULE: never show a negative review.
- **UNIQUENESS (honest):** 146 demos = ONE barber layout + ONE home-service layout, varied by
  colour palette (1 of 6) + each shop's own photos/reviews. NOT 146 unique layouts. The 6 truly
  unique hand-built layouts are in the PORTFOLIO only. Per-business unique layouts = future build.
- **Portfolio:** kd-demos.vercel.app/portfolio (6 unique designs + pricing tiers).
- **TWO consoles:** WhatsApp send-console.vercel.app + Email send-console.vercel.app/email.html
  (both 146 shops, niche-aware msg+pricing, demo + portfolio link in every message, Read-before-
  send). Built by tools\build_send_console.py + tools\build_email_console.py.
- **REPLY_CHEATSHEET.md** (Website Builder\), exact reply for every response type.
- **Pipeline:** scrape_gmaps_niche → enrich_new (merges any niche) → gen_premium (barbers,
  WIPES+rebuilds) → gen_homeservice (APPENDS) → re-add portfolio → build_send_console +
  build_email_console → deploy kd-demos + sites/send-console. ORDER MATTERS.
- Apify $49/mo Starter topped up 2026-05-29. Tiers: barbers €99+€39 · home-service €149+€49 ·
  premium add-ons (booking/deposits/reviews, ANY niche on a yes). Stripe staged (CLOSE_KIT.md),
  fires on first yes. €0 earned, KD now sending.

**The goal this serves:** King David's €10k/month. Recurring (€39/mo) is the engine that
compounds; the €99 is cash per close. €10k/mo ≈ 257 shops at €39/mo = a 3, 6 month climb,
NOT 30 days. June's job = prove the model + bank the first 5, 15 paying shops.

## The model (decided with KD 2026-05-29)
Find a local business that has Google reviews but **no real website** → build a free,
premium **sample** of THEIR site → message it to them → close **€99 to launch + €39/month**
(hosting + updates + Google visibility, no contract, cancel anytime).
- **Why this, not the other ideas:** the bottleneck was never building (KD can build
  anything), it's DISTRIBUTION + ticket size. One €99+€39/mo beats 100 × $5 Fiverr leads.
- **Remote only.** Text/WhatsApp/Instagram DM. Worldwide (matches [[feedback-pivot-to-global-market]]).
- **Honesty rule (faith filter):** every sample is a FREE DEMO, never the shop's live site.
  Footer says "Sample site made for X by King David Agbidi." Demos sit on KD's own
  kd-demos.vercel.app domain (reinforces it's a demo, no impersonation).

## What's BUILT and LIVE (all ~€0 spent)
- **69 PREMIUM live demos** at **https://kd-demos.vercel.app/<slug>/** (one public Vercel
  project). UPGRADED 2026-05-29 night (Group A): each demo now uses the shop's REAL Google
  photos (hero/gallery/about) + REAL review quotes + full contact, on a per-shop colour
  palette (1 of 6 → no two look alike), correct currency (€/£/$), and OG tags for rich
  WhatsApp link previews. Built by `tools\gen_premium.py` from enriched Apify data
  (`.claude\scrapers\tools\enrich_places.py` → real photos/reviews by Google place ID).
  Premium template: `templates\premium\`. Spread: Ireland (Dublin/Cork/Galway), UK
  (Manchester/Birmingham), US (Fresno/MA). Verified live (WebFetch + screenshots).
- **SEND CONSOLE: https://send-console.vercel.app**, all 69 demos, grouped by region
  (Ireland→UK→US→AU), one-tap pre-filled WhatsApp (KD's wording), per-region currency
  (€/£/$/A$), 2 rotating human variants, ✓Sent tracking. KD opens on phone, taps, sends.
- **Master template:** `Website Builder\templates\master\` (premium barber one-pager).
- **Batch tools (2026-05-29):**
  - `Website Builder\tools\gen_demos_batch.py`, mass-builds demos from scrape JSONs
    (reuses build_html), per-country currency swap (€/£/$/A$), dedup vs live demos +
    `existing_demos_seed.json`, city-spread + cap, writes `demos_manifest.json`. Bundle →
    `Website Builder\kd-demos\` (deploy whole folder as one Vercel project = 1 deploy,
    no per-site quota, scales to hundreds).
  - `Website Builder\tools\build_send_console.py`, rebuilds the console from seed + manifest
    (adds GBP £ pricing, region grouping). Takes the kd-demos base URL as arg.
- **Prospect scraper:** `.claude\scrapers\tools\scrape_gmaps_niche.py` (any niche/city, flags
  no-website, writes .json+.csv+_NOWEBSITE.csv). ~82 barber prospects scraped (Dublin/London/
  Galway/Manchester/Birmingham + US). Salons scraped but NOT built (barber copy ≠ salon).
- **SOP:** `Website Builder\SALES_SOP.md`. **Close kit:** `Website Builder\CLOSE_KIT.md`.
  **Pipeline:** `knowledge\clients.md` (69 demos logged, batch-2 table added).
- Vercel: team `king-david-s-projects2`, CLI authed `kdagbidiloveschrist`. NOTE: team-scoped
  aliases (`*-king-david-s-projects2.vercel.app`) have SSO protection (401), always use the
  CLEAN alias (`kd-demos.vercel.app`, `send-console.vercel.app`), which are PUBLIC.

## The winning message (KD wrote/approved · used in the console, per region/currency)
> howaya, I'm King David, I do websites for [city] barbers. [X] reviews and no website yet
> seems mad to me so I built ye a sample with your shop in it already: [link], that's just
> the demo, the real one I'd do around your own photos and colours. €99 to put it live this
> week then €39 a month and I handle the lot, hosting, updates, and getting ye showing up
> on Google. no pressure, want me to send it live for ye?

Irish voice, lowercase, no em-dashes, no AI tone. See [[feedback-sound-human-not-ai]].

## KD sends · not automated (critical)
KD sends every message himself (one tap from the console, editable). **Do NOT mass-auto-send
WhatsApp/IG**, it bans accounts. Pace ~20, 40/day, spaced out.

## To take money: STRIPE · DEFERRED until first "yes" (KD's call 2026-05-29)
KD decided NOT to set up Stripe upfront, we create the 2 Payment Links **only when a shop
wants to pay**. Steps ready in `CLOSE_KIT.md` (€99 one-off + €39/mo recurring, Adaptive
Pricing ON). KD creates them himself (payment-security rule), pastes back → Claude wires in.
Real social photos = an AFTER-YES step (never scrape/repost socials before a paying yes, platform rules + honesty filter; free demos use Google photos only).

## Next steps
- KD works the Send Console top-down (Ireland first = warmest), ~20, 40/day. Eyeball one demo
  on his phone first (SOP quality gate).
- KD creates the 2 Stripe links (CLOSE_KIT.md Part 1) → pastes them back to wire in.
- On a reply → build the full custom site (their real photos + colour pref) → close.
- Mark `won` in clients.md ONLY when cash clears (see [[project-first-client-FALSE-ALARM-2026-05-25]]).
- Scale: re-run gen_demos_batch + build_send_console for more cities (2nd-night repeat).
  Owed to KD: personal portfolio site. Codify a `/website-sales` skill after first close.
- Kill rule: if a fair run of quality samples + warm sends = €0, fix message/channel, not model.
