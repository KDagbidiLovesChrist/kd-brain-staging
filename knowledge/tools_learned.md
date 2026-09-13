---
name: knowledge-tools-learned
description: Notes on every tool and API King David has used, what works, what doesn't, gotchas, rate limits, and tips. Prevents repeating mistakes. Queried by /search.
---

# Tools Learned · API & Tool Notes

Every time something surprising is discovered about a tool, a gotcha, a workaround,
a rate limit, a thing that works especially well, it gets logged here.

This file prevents King David (and Claude) from making the same mistake twice.

---

## FORMAT FOR NEW ENTRIES

```
## [Tool Name] · [Date]
**What it does:** [one line]
**Account:** [Free / Paid, link to dashboard]
**Key in .env:** [KEY_NAME]
**What works well:** [specific things that work]
**Gotchas / Watch out for:** [things that trip people up]
**Rate limits:** [what limits exist and how to handle them]
**Useful endpoints/features:** [the ones actually used]
**Links:** [docs, dashboard, billing]
```

---

## TOOL NOTES

### Anthropic API (Claude AI)
**What it does:** Powers Claude, summarising, writing, reasoning, coding
**Account:** Paid via Claude subscription
**Key in .env:** `ANTHROPIC_API_KEY`
**What works well:**
- Prompt caching on long CLAUDE.md files, faster + cheaper repeated reads
- claude-sonnet-4-6 is the best balance of speed + quality for most tasks
- claude-haiku-4-5 for fast/cheap tasks (summarising, formatting)
- claude-opus-4-7 for hardest thinking tasks (architecture, strategy)
**Gotchas:**
- API calls through code cost tokens just like chat, don't run in loops without thinking
- Max tokens per response varies by model, set max_tokens appropriately
- Context window is 200K but performance degrades with very long prompts
**Rate limits:** Varies by plan, Max plan has highest limits
**Links:** console.anthropic.com

---

### Firecrawl MCP
**What it does:** Web scraping, search, extract, crawl
**Account:** Paid, check firecrawl.dev for plan details
**Key:** Connected via MCP URL in settings.json (key embedded in URL)
**What works well:**
- `firecrawl_scrape` with `formats: ["markdown"]` for clean text extraction
- `firecrawl_search` for finding multiple pages on a topic
- Very fast for standard business directories
- Returns clean markdown, easy to parse
**Gotchas:**
- Some sites block Firecrawl (Cloudflare protection, JS-heavy sites) → use Playwright instead
- Rate limit hits with very rapid repeated calls, add small delays between scrapes
- Dynamic content (loaded by JavaScript) sometimes not captured, use Playwright for those
**Rate limits:** Check firecrawl.dev dashboard
**Fallback:** Playwright MCP for blocked sites

---

### Playwright MCP
**What it does:** Full browser automation, navigate, click, fill, extract, screenshot
**Account:** Free, runs locally via npx
**Key:** No API key, configured in settings.json
**What works well:**
- Works on sites that block Firecrawl
- Can handle login flows, forms, JavaScript-rendered content
- Screenshots are high quality and save to .tmp\
- `browser_snapshot` gives the full page structure for reading
**Gotchas:**
- Slower than Firecrawl (real browser startup time)
- Some sites detect Playwright and block it too (rare but happens)
- Need to close browser explicitly after tasks, use `browser_close`
- Headless mode is default, can switch to visible for debugging
**Rate limits:** None (local tool), limited only by site's own rate limiting

---

### Gmail SMTP
**What it does:** Send emails programmatically from a Gmail account
**Account:** Existing Gmail account
**Setup:** Need to enable App Passwords in Google Account settings
**Keys in .env:** `GMAIL_ADDRESS`, `GMAIL_APP_PASSWORD`
**What works well:**
- Simple, reliable for sending newsletters
- No additional cost, uses existing Gmail account
- Python `smtplib` library is built-in (no install needed)
**Gotchas:**
- Must use App Password, NOT your main Google password
- Google occasionally blocks SMTP if sending volume is high → use Gmail API for production
- Daily send limit: ~500 emails/day for free Gmail, 2,000 for Google Workspace
- HTML emails need inline CSS (email clients strip external stylesheets)
**Upgrade path:** → Gmail API (see reference_google_cli.md) for higher limits

---

### Perplexity API (To Be Set Up)
**What it does:** AI-powered web research, searches and synthesises information from the web
**Account:** Create at perplexity.ai, paid API ($20/month or pay-per-use)
**Key in .env:** `PERPLEXITY_API_KEY`
**What works well:**
- Real-time web search with AI synthesis, much richer than RSS
- Returns sources + citations automatically
- `sonar` model is the most capable for research
- Can research ANY topic, not tied to a specific feed
**Gotchas:**
- Costs per API call, set a monthly budget alert
- Rate limits on free tier, paid tier is needed for production use
- Results include web sources so verify claims before publishing
**Endpoint:** `https://api.perplexity.ai/chat/completions`
**Links:** perplexity.ai/settings/api

---

### Fiverr (Platform, Not API)
**What it does:** Marketplace to sell digital services
**Account:** Create at fiverr.com
**Key insights:**
- Lead gen gigs do well with specific geographic focus ("Ireland/UK" beats generic)
- First 5 reviews are hardest to get, consider doing 2-3 free jobs for testimonials
- Respond fast to messages (within 2 hours), Fiverr rewards fast responders
- Add before/after examples (sample CSV) to gig description
- Delivery speed is a selling point, "same day" for small orders
**Pricing:** €25/50 leads, €50/150 leads, €90/300 leads
**Current status:** Gig NOT yet posted, top priority

---

### trigger.dev (To Be Set Up)
**What it does:** Schedule and deploy automations to run 24/7 in the cloud
**Account:** Create at trigger.dev, free tier available
**Connection:** Links to GitHub repo → reads tools\ → runs on schedule
**What works well:**
- Free tier handles most personal projects
- Schedule in plain English cron format ("every Monday at 8am")
- Logs available to see when runs happened and if they succeeded
- Environment variables stored securely in the dashboard
**Gotchas:**
- Code must be committed to GitHub before trigger.dev can read it
- .env secrets must be manually added to trigger.dev dashboard (they don't read .env)
- First time setup requires some config in the repo
**Links:** trigger.dev, docs.trigger.dev

---

---

### sync_dceo_brain_to_drive.py · 2026-05-23
**What it does:** Recursively syncs `DCEO_BRAIN\` folder structure to Google Drive (preserves directories). Uses existing `token.json` from `google_auth.py`.
**Path:** `C:\Users\Dell\.claude\tools\sync_dceo_brain_to_drive.py`
**Auth:** `drive.file` scope from `tools\google_auth.py` token
**What works well:**
- One command syncs everything: `python tools/sync_dceo_brain_to_drive.py`
- Re-runs UPDATE existing files in place (not duplicate)
- SKIPS .git, __pycache__, node_modules (configurable in SKIP_DIRS set)
- Output shows `[created]` vs `[updated]` per file + final tally
- 113 files synced in ~60-90 seconds
**Gotchas:**
- `drive.file` scope only lets the app see files IT created, folder must be created via this script (not via Drive UI) for re-sync to work
- If Drive auth expires, just re-run `python tools/google_auth.py` to refresh token
**Use cases:** Cross-laptop sync of DCEO_BRAIN, backup of any folder under .claude\

---

### Glaido (STT desktop dictation) · 2026-05-23 · ACCOUNT PARKED
**What it does:** Speech-to-text desktop dictation (Nate Herk's pick), hotkey to dictate into any app
**Account:** Free tier created (kingagbidi@gmail.com via Google OAuth)
**Free tier:** 2,000 words/week, no credit card, no trial limits, use in any app, AI auto-edits, agent mode
**Pro tier:** $20/month (unlimited words)
**BLOCKER:** macOS only as of 2026-05-23. Windows + Linux "coming soon."
**Status:** Parked, re-check periodically for Windows release
**URL:** https://app.glaido.com/

---

### GPTZero (AI detection API) · 2026-05-23 · API SKIPPED
**What it does:** AI content detection (consumer + API)
**UI account:** Free tier active (kingagbidi@gmail.com via Google OAuth), 10K words/month for the consumer detector
**API tier:** PAID ONLY, starts at $45/month. No free dev tier.
**Status:** Skipped per faith/budget rule. Revisit when CV Tailor revenue justifies $45/mo.
**Note:** CV Tailor interview-first rebuild reduced GPTZero urgency, defer indefinitely

---

---

### Supabase (Postgres DB + Auth + RLS) · 2026-05-25 · LIVE
**What it does:** Postgres database + auth + row-level security + REST/GraphQL APIs in one platform. Backbone for `/lead_qualifier_app` skill, client RAG agents, production auth/DB.
**Account:** kingagbidi@gmail.com (email/password, Saturday password compromised in Playwright snapshot, reset 2026-05-25)
**Project:** `king-david-prod` (org "King David Agency") · Region: West EU (Ireland) eu-west-1 · Free tier (500MB DB, 1GB storage, 50k MAU)
**Project URL:** `https://nvopnmjywqtiibiqqjlu.supabase.co`
**Keys saved to .env.master:**
- `SUPABASE_URL`, base URL
- `SUPABASE_PUBLISHABLE_KEY` (new 2026 style), replaces `anon`, safe for browsers when RLS is on
- `SUPABASE_SECRET_KEY` (new 2026 style), replaces `service_role`, server-only
- `SUPABASE_ANON_KEY` (legacy JWT), kept for compatibility with current libraries + AIS course material
- `SUPABASE_SERVICE_ROLE_KEY` (legacy JWT), same
**DB password:** NOT in .env.master, King David's password manager only. Rotated 2026-05-25 after Saturday password was burned in chat transcript.
**Direct Postgres connection string:** `postgresql://postgres.nvopnmjywqtiibiqqjlu:<DB_PASSWORD>@aws-0-eu-west-1.pooler.supabase.com:5432/postgres`
**Security defaults at project creation:** Data API ON · Auto-expose new tables OFF · Auto-RLS ON (Supabase's own recommendation)
**Verified:** `curl -H "apikey: <key>" -H "Authorization: Bearer <key>" https://<URL>/auth/v1/settings` → HTTP 200 (both new + legacy keys)
**Gotchas:**
- Supabase rolled out new key naming in 2026, pages have BOTH "Publishable/secret" tab and "Legacy anon/service_role" tab. Save both.
- `/rest/v1/` root endpoint returns 401 without a table query, use `/auth/v1/settings` for health checks
- Don't put DB password in `.env.master`, it's for direct Postgres connections only (DataGrip, psql), not the standard Supabase client
- Project provisioning takes ~2 min after Create, wait before hitting endpoints
**URL:** https://supabase.com/dashboard/project/nvopnmjywqtiibiqqjlu

---

### Cal.com (booking automation) · 2026-05-25 · LIVE
**What it does:** Booking page + scheduling API. Backbone for plumber pitch (booking automation), voice agent → calendar flow, client discovery booking page (Luca's auto-detailing template uses Cal.com).
**Account:** kingagbidi@gmail.com (Google OAuth signup) · Free tier (unlimited bookings, 1 connected calendar)
**Username:** `kingdavid` · **Booking URL:** `https://cal.com/kingdavid`
**Calendar:** Google Calendar auto-connected via OAuth scope (no separate connect step needed)
**Timezone:** Europe/Dublin (auto-detected from browser)
**API key saved to .env.master:** `CALCOM_API_KEY=cal_live_...` (label "Claude Code automation", never expires)
**Also saved:** `CALCOM_USERNAME=kingdavid`, `CALCOM_BOOKING_URL=https://cal.com/kingdavid`
**Verified:** `curl -H "Authorization: Bearer $CALCOM_API_KEY" https://api.cal.com/v2/me` → HTTP 200 returning user object
**Gotchas:**
- **Cal.com API v1 is DECOMMISSIONED.** Always use v2: `https://api.cal.com/v2/...` (v1 returns HTTP 410)
- Auth via Bearer token header (`Authorization: Bearer cal_live_...`), NOT query param `?apiKey=` like v1 used
- Onboarding flow username field needs explicit "Update" click after typing, then Save. The change doesn't auto-commit on blur.
- Username changes on the onboarding step often don't persist, verify via API `/v2/me` after onboarding and fix via Settings → Profile if needed
**URL:** https://app.cal.com/settings/developer/api-keys

---

### Apify (web scraping fallback) · 2026-05-25 · LIVE
**What it does:** Pre-built scraping actors for sites Firecrawl can't crack (LinkedIn, Twitter, paywalled content). Apify Store has thousands of ready-made scrapers, don't write your own.
**Account:** kingagbidi@gmail.com (Google OAuth signup) · Free tier $5/month compute credit (~5,000 page scrapes typical)
**Username:** `kingdavidagency` (`kingdavid` was taken on Apify)
**Token saved to .env.master:**
- `APIFY_API_TOKEN=apify_api_...` (default token auto-created on sign-up)
- `APIFY_USER_ID=...`
- `APIFY_USERNAME=kingdavidagency`
- `APIFY_PROXY_PASSWORD=apify_proxy_...` (for Apify Proxy access, residential proxies enabled on free tier)
**Verified:** `curl -H "Authorization: Bearer $APIFY_API_TOKEN" https://api.apify.com/v2/users/me` → HTTP 200 with full user/plan/proxy details
**Use cases:**
- LinkedIn scraping (`apify/linkedin-profile-scraper` actor)
- Twitter/X scraping
- Generic JS-heavy pages (`apify/web-scraper` actor, ~$0.01/page)
- Cheap HTML-only pages (`apify/cheerio-scraper` actor, ~$0.001/page, try this first)
**Gotchas:**
- Token reveal is via "Show" button, token is permanently masked in UI display, can't be re-displayed if lost (use Regenerate)
- Free tier: $5/mo compute, 25 concurrent runs, 8GB max actor memory, 7-day data retention
- Residential proxies counted separately ($8/GB after free tier), use only when needed
- Apify Store actors charge per-page, budget burns fast on JS-heavy sites. Test with cheerio-scraper first.
**URL:** https://console.apify.com/settings/integrations

---

*New entries added by /save after sessions where new tools are explored or gotchas are discovered.*
