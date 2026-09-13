---
name: project-shopify-portfolio
description: "Shopify 'build + run online shops' engine. Portfolio of 4 store designs LIVE at kd-demos.vercel.app/shopify (fashion/skincare/coffee/supplements) + OUTREACH ENGINE LIVE 2026-05-30: IG-seller finder (scrape_ig_sellers.py) + console at send-console.vercel.app/shopify.html (9 vetted Irish no-store sellers). €249 launch + €59/mo (or €99/mo run-it). Mirrors website-sales for e-commerce."
metadata: 
  node_type: memory
  type: project
  originSessionId: 8fb279df-42f8-407e-b099-c5ed1554b8ea
---

# Project: Shopify Store Portfolio (NEW · built 2026-05-30)

## What it is
The same money model as [[project-website-sales]], but for **online shops**: build + RUN
e-commerce stores for brands. Free sample store → close a launch fee + monthly run-it
retainer. KD's words: "shopify portfolio similar to this website portfolio... claude code
will build and run shops similar to how we build and run websites."

## ⭐ LIVE NOW
- **Hub:** https://kd-demos.vercel.app/shopify/ (e-commerce framing + how-it-works + pricing
  + free-sample CTA). Links back to the website portfolio.
- **4 unique hand-built store designs** (each a genuinely different look, with product grid,
  working add-to-cart + cart drawer + total, reviews, niche-correct copy):
  - `/shopify/fashion/`, **LUNA & STONE** (editorial monochrome luxe boutique)
  - `/shopify/skincare/`, **DEW** (clean sage/cream beauty, ingredient-led)
  - `/shopify/coffee/`, **ROAST & CO** (warm rustic-premium roastery, subscription-led)
  - `/shopify/supplements/`, **APEX FUEL** (bold black + volt-green performance)
- All 5 verified HTTP 200 + correct titles on the CLEAN public alias (kd-demos.vercel.app,
  NOT the team-scoped *-king-david-s-projects2 alias which is SSO-401).

## How it's built (decision: best-ROI, protect the $300 Claude budget)
- **STATIC premium mockups**, hand-coded HTML/CSS/JS, same approach as the website
  portfolio (which is the proven pattern). Cost ~€0. NOT real Shopify dev stores (those have
  signup friction + expiring/password-gated URLs). Spin up a REAL Shopify Partner dev store
  ONLY after a client says yes.
- **Shopify Partner upside (future):** real Partner account = free dev stores to build in +
  ~20% recurring referral/affiliate revenue on top of KD's own launch+retainer fee.

## Files / WAT
- Source: `Website Builder\shopify-portfolio\` (index.html + fashion/ + skincare/ + coffee/
  + supplements/). Deployed by copying into `Website Builder\kd-demos\shopify\` then
  `vercel deploy --prod` (same kd-demos project, prj_D3WZgZq4lUYoI0n5CVzRptrc2K89).
- Brand: navy/gold on the HUB (matches KD brand); each STORE has its own distinct palette
  (that's the point, uniqueness sells, per [[project-website-sales]] honesty note).
- Same WAT chain as /website-sales. Could become a `/shopify-sales` skill after first close.

## Pricing (set 2026-05-30, higher ticket than websites)
- **Store:** €249 setup + €59/mo (shop, payments, hosting, edits).
- **Store + Run-It-For-Me:** €249 setup + €99/mo (KD adds products, runs promos, all tech).
- Higher than the €99+€39 website tier because "build AND run a shop" is more work + value.

## ⭐ OUTREACH ENGINE LIVE (2026-05-30 evening) · IG sellers with no store
Audience DECIDED (KD's call): **Instagram sellers with NO real online store**, Irish first.
- **Finder:** `.claude\scrapers\tools\scrape_ig_sellers.py`, Apify `instagram-hashtag-scraper`
  (discover handles from 19 Irish maker/market hashtags) → `instagram-scraper` "details" (bio,
  followers, link-in-bio, category) → keeps SELLERS with NO real store (empty / linktr.ee /
  beacons / social link = prospect; own-domain / shopify / etsy = skip), matches each to a demo
  store (candles/skincare→DEW, clothing/art→LUNA, coffee→ROAST, supplements→APEX, else hub).
  BLOCKLIST auto-drops pharmacies/supermarkets/B2B/PR. Pay-per-result ~$0.0023. Output:
  `.tmp\ig_sellers_<ts>.json` + `_PROSPECTS.csv`. Run: `python scrape_ig_sellers.py --per 30
  --max 120`. First run: 25 prospects / 120 profiles, ~$1.60 spent.
- **Console:** `Website Builder\tools\build_shopify_console.py` → `sites\send-console\shopify.html`
  → LIVE at **https://send-console.vercel.app/shopify.html** (deploys with the existing
  send-console project; vercel resolves via PowerShell, NOT the python deploy helper which
  can't see the .cmd shim). Reads latest `ig_sellers_*_PROSPECTS.csv` or a path arg. Per seller:
  pre-written Irish store-pitch (2 variants, €249+€59 / €99-mo run-it, demo + hub link, NO
  em-dash, verified via browser_evaluate), 👁Read, 📋Copy (primary, IG DMs can't pre-fill),
  Instagram, 🔗Demo, ✓Sent (localStorage). KD sends every DM himself (no auto-send, IG bans).
- **First batch curated to 9 best money-fits** (KD: "only ones with best chance of making money"):
  craftylanedesigns(9.7k), emmahiggins(5.8k), healthyhousecahir(4.6k), gemmaoneill(3.7k),
  naturallybalancedkinsale(2.3k), florentinestreasures(1.9k), ros.eo.soap(795),
  hilltop_blankets(355), algaran.seaweed.donegal(325). Manifest: `Website Builder\shopify_prospects.json`
  + curated CSV `.tmp\ig_sellers_MONEY.csv`. Dropped 16 weaker/risky (supermarket, pharmacies,
  chemist, PR acct, B2B mfr, trailer mfr, likely-already-have-store, charity/gallery, no-info).
  KD pinged (push + iCloud email).

## ⭐ PER-SELLER DEMO STORES (2026-05-31) · KD's call: "do it like the websites"
KD flagged the gap: the first cut just MATCHED sellers to 4 generic stores. He wanted each
seller's OWN store (like the per-shop website demos). Honesty constraint: their photos are on
Instagram (social), we do NOT repost socials before a yes (platform/copyright). So each demo
is branded to THEM (name, tagline-from-bio, fitting palette) with premium STOCK products;
real products swapped in on a yes.
- **Generator:** `Website Builder\tools\gen_shopify_demos.py`, re-skins the proven DEW store
  template per brand. 9 PALETTES + per-category PRODUCT SETS (proven Unsplash sets harvested
  from the live stores for skincare/supplements; keyword-matched loremflickr for soap/art/
  crafts/ceramics/blankets, verified loading). Curated PROFILES dict = brand+tagline+palette+
  set per seller. Writes `kd-demos\shopify\s\<slug>\index.html` (working cart, honesty footer
  "Sample store designed by King David Agbidi for @handle"). Re-run to regenerate.
- **9 stores LIVE** (all HTTP 200) at `kd-demos.vercel.app/shopify/s/<slug>/`, e.g.
  /naturallybalancedkinsale/, /hilltop-blankets/, /ros-eo-soap/, /emmahiggins/, etc.
  QA'd 2 (Unsplash + loremflickr), both look premium + on-brand.
- **Console rewired:** `build_shopify_console.py` now links each card's Demo to the seller's
  OWN store (`/shopify/s/<slug>/`, falls back to category/hub if none) + message updated to
  "I built ye a sample shop with your name on it already" (still no em-dash). Redeployed.
- **On a YES:** swap in their real products/photos for the full high-quality build (KD: "if they
  ask for another free demo we make it as high quality as it needs"). Both kd-demos + send-console
  redeployed 2026-05-31.

## OFFER STRATEGY · land then expand (decided 2026-05-31, KD: "do what's best strategically")
KD floated adding SEO / "get you sales" / a free tier / running their socials into the pitch.
Expert call (taken): **cold DM sells the CORE only** (free sample → €249+€59 / €99 run-it). Stuffing
extras kills reply rate + credibility, and a cheap/free tier would eat the €59/mo recurring (the
engine). So:
- **Message sharpened** (build_shopify_console.py) to be OUTCOME-led + honest: leads with "you're
  losing sales to the dms / a real shop lets people just buy day or night" + keeps "sample with your
  name on it." NO over-promising sales figures (honesty filter). "Found on Google / tech handled" is
  in the price line. Redeployed. (em-dashes only in page <title> + a copied-toast, NOT in the sent message.)
- **Upsell menu built** for AFTER a yes: `Website Builder\SHOPIFY_UPSELL_MENU.md`, social mgmt
  €250, 450/mo, content/photo day €150, email €99, 150/mo, Meta ads €200/mo + spend, SEO/blog €120/mo,
  bundles (Growth €499/mo, Full €799/mo). Rule: offer ONE at a time, only what helps + what KD can
  deliver, promise the deliverable not a sales number. This is the real recurring upside per client.

## 📤 SENT · all 9 messaged 2026-05-31 (KD's first Shopify outreach)
KD sent the DM to all 9 sellers from his phone (craftylanedesigns, emmahiggins, healthyhousecahir,
gemmaoneill, naturallybalancedkinsale, florentinestreasures, ros.eo.soap, hilltop_blankets,
algaran.seaweed.donegal). Status now = WAITING ON REPLIES. €0 still (won only when cash clears).
- **Reply + close kit READY:** `Website Builder\SHOPIFY_REPLY_CLOSE.md` (reply scripts per response
  type + the YES flow: confirm tier → collect products/photos/domain/payment → KD makes 2 Stripe
  links €249 + €59/99mo → build real store → launch → mark won on cash). Stripe deferred to first yes.
- On ANY reply → KD pastes it to Claude → Claude drafts the response from the kit → on a yes, build.

## NEXT (when KD comes back to this project)
1. KD works the Shopify console on his phone (send-console.vercel.app/shopify.html), Irish
   first, 20, 40/day: Read → Copy → open Instagram → paste DM → Sent. Eyeball each page first.
2. On a yes → open a real Shopify Partner dev store, build their actual shop, close
   (€249 + €59/mo, or €99/mo run-it). Mark `won` only when cash clears.
3. Scale: re-run `scrape_ig_sellers.py` with more/other hashtags (or `--max` higher) →
   rebuild console (`build_shopify_console.py`) → redeploy send-console. Repeatable pipeline.
4. Consider real Shopify Partner signup (free) for the 20% affiliate revenue + real dev
   stores. Needs KD's signup (payment/security rule).
5. Future: per-seller product-photo demos after a yes; `/shopify-sales` skill once first close lands.

## Honest position
€0 earned. Portfolio is a sales ASSET, not income yet. The website engine is still June's
primary money (live, sending). Shopify = a higher-ticket second door, near-zero cost to
stand up, ready to pitch.
