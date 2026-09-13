# /website-sales · Website Sales Engine Skill

> READ FIRST: `C:\Users\Dell\.claude\CLAUDE.md` (master brain, WAT, operating rules) and
> `C:\Users\Dell\.claude\brand_assets\brand_guidelines.md`.

> ⛔ **STANDING KILL (King, 2026-07-03): WhatsApp cold-send sprints are DEAD — never propose them as King's
> hand-step again** ("im not doing the whatsapp again i did it before no luck!!!"). The 146 demos stay live
> as ASSETS; any future outreach on them must be a DIFFERENT motion (email console · GBP service via the
> Buka case study · inbound) and only on King's explicit ask. See `memory\feedback_no_cold_outreach_king_tried.md`
> + `_ops\REVENUE_QUEUE.md` (KILLED).

**Trigger:** King David types `/website-sales` OR says "scrape and build demos", "add a niche/
city to the send list", "make me sites to sell", "rebuild the console", "write the pitch
messages", "more website prospects", "continue the website sales".

**The money play:** find local businesses with Google reviews but NO real website → build a
free premium SAMPLE of their site → send a personalised message (demo link + portfolio) →
close. Barbers €99+€39/mo (volume, easy yes) · home services €149+€49/mo · premium add-ons
(booking/deposits/reviews) for ANY niche on a yes. The €39/mo retainer is the engine to €10k/mo
(stacks over 3, 6 months, not 30 days). Full state: `memory\project_website_sales.md`.

**Honesty filter (always):** every site is a FREE DEMO/sample, never their live site. Footer
= "© Shop · City" + "Free sample preview" (NO "by King David"). Reviews shown are POSITIVE-ONLY
(stars>=4 + real text); never a negative review. Real photos = the shop's own Google photos.
No scraping/reposting socials before a paid yes. KD sends every message himself (NO auto-send =
no bans), ~20, 40/day spaced at human times.

---

## WAT chain
- **W (Workflow):** `Documents\Website Builder\WEBSITE_SALES_WORKFLOW.md` (the SOP) + `SALES_SOP.md`
- **A (Agent):** Claude, scrape → enrich → build → write pitch → help close
- **T (Tools):** the 6 pipeline scripts below + Apify + Vercel CLI + Stripe (close) + Gmail (email)
- **S (Skill):** this file, `/website-sales`

## The pipeline (FIND → ENRICH → BUILD → SEND). RUN SEQUENTIALLY, one at a time.
> Tool runs occasionally cancel if fired in big parallel batches, run each step alone, verify,
> then the next. ORDER MATTERS in the build (gen_premium WIPES the bundle).

1. **FIND**, `.claude\scrapers\tools\scrape_gmaps_niche.py "barber Cork Ireland" "plumber Leeds UK" ...`
   Any niche/city. Flags no-website shops. Writes ONE combined `.tmp\gmaps_<first-search>_*.json`
   (+ .csv + _NOWEBSITE.csv). NOTE: most home-service shops already have sites, pool is thin;
   barbers/salons/cafés/gyms are richer.
2. **ENRICH**, `.claude\scrapers\tools\enrich_new.py "<filename-substring>" <out_prefix> yes`
   Pulls REAL photos + reviews by Google place ID, MERGES with prior enriched file (dedup by
   phone). Prefixes: `enriched_demos` (barbers), `gmaps_plumber-homeservice-enriched` (home svc).
3. **BUILD barbers**, `Website Builder\tools\gen_premium.py "https://kd-demos.vercel.app" 200 30` (LAPTOP-ONLY: lives outside the synced brain, in `Documents\Website Builder\`)
   Builds ALL barbers from latest enriched_demos_*. **WIPES kd-demos\** then rebuilds + writes
   `demos_manifest.json`. Premium dark template `templates\premium\`, per-shop palette (1 of 6),
   positive-only reviews, OG tags.
4. **BUILD home services**, `Website Builder\tools\gen_homeservice.py "https://kd-demos.vercel.app" 30` (LAPTOP-ONLY: lives outside the synced brain, in `Documents\Website Builder\`)
   APPENDS home-service demos + folders + manifest rows. Trust-blue template `templates\homeservice\`.
5. **RE-ADD portfolio** (step 3 wiped it): copy `Website Builder\portfolio\` → `kd-demos\portfolio\`
   (delete the copied `.vercel`). Portfolio = 6 unique hand-built niche designs + pricing tiers.
6. **BUILD consoles**,    - `Website Builder\tools\build_send_console.py "https://kd-demos.vercel.app"` (LAPTOP-ONLY: lives outside the synced brain) → WhatsApp console
   - `Website Builder\tools\build_email_console.py "https://kd-demos.vercel.app"` (LAPTOP-ONLY: lives outside the synced brain) → email console
   - (optional) `Website Builder\tools\build_research.py` (LAPTOP-ONLY: lives outside the synced brain) → research.html (per-shop IG/FB/TikTok)
7. **DEPLOY** (clean public aliases):
   - `vercel deploy --prod --yes --cwd "Website Builder\kd-demos"` → kd-demos.vercel.app
   - `vercel deploy --prod --yes --cwd "Website Builder\sites\send-console"` → send-console.vercel.app
   VERCEL NOTE: use clean aliases (kd-demos / send-console .vercel.app), team-scoped aliases are
   SSO-protected (401). Verify with curl/WebFetch after deploy.

## Live assets (KD's daily tools)
- Demos: https://kd-demos.vercel.app/<slug>/   ·   Portfolio: https://kd-demos.vercel.app/portfolio/
- WhatsApp console: https://send-console.vercel.app   ·   Email console: https://send-console.vercel.app/email.html
- Research: https://send-console.vercel.app/research.html

## Personalised message style (KD's voice · keep EXACT)
Lowercase, Irish, warm, no em-dashes, no AI tone. Two rotating variants (even/odd index),
personalised by city + review count + currency + trade, demo + portfolio link in every message.
Home services swap to JOBS angle ("more jobs, quote form, phone keeps ringing"). See
`memory\feedback_sound_human_not_ai.md`. Console has a 👁Read button so KD reviews before send.

## When a shop replies → close
- Use `Website Builder\REPLY_CHEATSHEET.md` (exact reply for every response type).
- On a YES: create the 2 Stripe links (`Website Builder\CLOSE_KIT.md` Part 1), €99 one-off +
  €39/mo recurring, Adaptive Pricing ON. KD makes them (his card, payment-security rule), pastes
  back to wire in. Send €99 link → €39/mo link → collect photos/colours → build real site →
  mark `won` in `knowledge\clients.md` ONLY when cash clears.
- Premium add-ons (booking/deposits/review automation) = extra monthly, any niche. Lead-system
  scaffolding NOT yet on disk, rebuild fresh when first Pro client asks.

## Cold email channel
Email console writes a full personalised email per shop (subject+body+demo+portfolio). The 146
no-website shops mostly lack emails → for a real email pipeline, scrape EMAIL-FRIENDLY niches
(restaurants/gyms/salons/dentists) which list emails. Existing email tooling:
`.claude\scrapers\tools\` send_emails.py, enrich_emails.py, check_replies.py, generate_send_batch.py.
Google OAuth token+creds in `.claude\`. KD sends from his Gmail at human times, never auto-send.

## Honest current numbers (2026-05-29)
146 demos live (124 barber + 22 home-service, IE/UK/US/CA). €0 earned, ~$49 spent (Apify).
NOTE: 146 = 2 layouts (barber + home-service) varied by colour+content, NOT 146 unique layouts;
the 6 unique layouts are the portfolio. Next ideas: email-niche scrape, salon/café generators,
per-business unique layouts, AI OS upsell to a happy website client.
