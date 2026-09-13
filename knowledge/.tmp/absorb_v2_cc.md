# NEW Claude Code Insights v2, Phase 2-4 Synthesis
*Distilled 2026-05-23 from 46 loom_CC_*.md transcripts (Phase 1-4, all modules).*
*Source: Phase 2 (8 modules), Phase 3 (10 modules), Phase 4 (8 modules). Phase 1 mostly baseline WAT/vibe coding, already covered in master summary.*

---

## TOP 5 MOST-ACTIONABLE FINDINGS

1. **Agentic Gap = Lost Self-Healing (Phase 3 critical shift)**, Cloud Code heals locally; trigger.dev doesn't. Must prompt with: fixed inputs, structured outputs, error handling baked-in, logging at every step. Ask for `try-catch` around every external API call. King David: apply this to next Phase 3 build today. [loom_CC_P3_1_2_The_Agentic_Gap]

2. **Skills = Slash Commands on Demand (Phase 2)**, Skills load ONLY when invoked (`/draft_email` fires skill.md). Store repeatable tasks as skills in `.claude/skills/` folder, not in CLAUDE.md. 20-50 skills ≠ context bloat; CLAUDE.md with 50 inline workflows = death. King David's 29 skills should migrate hard-coded ones → individual skill folders. [loom_CC_P2_1_7_Skills, loom_CC_P2_1_8_Skills_in_Action]

3. **Stripe + Supabase + Vercel = SaaS in One Afternoon**, Phase 4 shows: workflow on trigger.dev + front end on Vercel + Stripe checkout + Supabase for user subscriptions = monetized full-stack app. King David's `/lead_qualifier_app` can charge €29/month in <4 hours after learning this pattern. [loom_CC_P4_1_6_Stripe_Payments, loom_CC_P4_1_5_Authentication_Security_Audit]

4. **Webhook + n8n Form = Serverless Report Generation**, Fire a webhook from n8n form → trigger.dev task → Google Docs generation → auto-saved to Drive. No code, pure workflow. Reusable for client proposal generators, lead reports, intake forms. [loom_CC_P3_1_7_Masterclass_Webhook_Report_Generator]

5. **Enhancement Philosophy: Error → Logic → Output → Performance (in order)**, Fix what breaks first (error handling), then make it efficient (logic), then polish UX (output), THEN optimize speed. Test happy path + edge cases after each layer. King David's existing 29 skills should each get one enhancement pass. [loom_CC_P1_3_1_Intro_Enhancement_Philosophy]

---

## BY THEME

### **Phase 2: Agentic Workflows (Deterministic → Non-Deterministic)**

**Deterministic vs Non-Deterministic Mindset**
- Deterministic = same input → same output every time (n8n, traditional automation). Boring is beautiful.
- Non-deterministic = AI reasons, adapts, asks clarifying questions. May produce different outputs. Requires you describe WHAT, not HOW. [loom_CC_P2_1_2_Understanding_Agentic_Workflows]

**Workflow → Agent → Tool → Skill (WAT fully mature)**
- Workflow: markdown SOP with natural language
- Agent: Claude reads, reasons, decides
- Tool: Python/MCP/API executes
- Skill: /slash_command wrapper for reuse
- Every skill loaded on-demand, saves 40%+ context vs inline. [loom_CC_P2_1_4_First_Agentic_Workflow]

**MCP as Toolbox Language (not SDK)**
- MCP = Model Context Protocol: single integration point for MANY tools. Install Firecrawl MCP once → agent auto-discovers 10+ Firecrawl actions (search, scrape, extract, etc.).
- Find MCPs: mcp.so or GitHub `MCP server <service_name>`
- Top MCPs for King David: Firecrawl (web), Postgres/Supabase (DB), Google Drive (docs), Slack/Gmail (comms), Notion (wiki).
- Safe install: Cloud Code handles setup, you manually add API key to mcp.json. [loom_CC_P2_1_5_MCP_Servers_in_Cloud_Code]

**Research Workflow Pattern (Firecrawl + synthesis)**
- Give topic → Firecrawl searches 3-5 sources in parallel → Claude synthesizes → outputs markdown + PDF document (both generated in one shot).
- Iteration loop: run once, get markdown output, ask for format changes (e.g., "list sources instead of table"), Cloud updates both outputs.
- Applicable to King David's `/newsletter`, client discovery research, competitive analysis. [loom_CC_P2_1_6_Research_Workflow_Firecrawl_MCP]

**Skills Placement & Token Math**
- CLAUDE.md: ONLY rules that apply every session (WAT framework, constraints, brand voice). Hard cap 100-150 lines.
- Skills: repeatable workflows live in `.claude/skills/<skill_name>/skill.md`. Load on demand.
- Math: 1 skill in CLAUDE.md = 200 lines loaded on every session. Same skill as skill.md = 200 lines loaded only when /skill invoked. 20x context savings. [loom_CC_P2_1_7_Skills, loom_CC_P2_1_8_Skills_in_Action]

---

### **Phase 3: Cloud Deployment & The Agentic Gap**

**The Agentic Gap (Cloud Code can't watch production)**
- Phases 1-2: Cloud Code self-heals in real-time. Sees error, fixes it, retries, logs. Magical.
- Phase 3+: Deploy to trigger.dev or cloud schedule. Cloud Code isn't watching. If task fails, no one knows unless alerted.
- Close the gap with: Fixed inputs (no clarifying questions), structured outputs (predictable format), error handling baked-in (try-catch every API), logging at every step, alerts (email/Slack on failure), retries (exponential backoff). [loom_CC_P3_1_2_The_Agentic_Gap]

**Prompting for Cloud Deployment (new language)**
- Old: "Help me research this topic"
- New: "Build an UNATTENDED scheduled task that researches this FIXED topic every morning, handles errors without crashing, logs every step, outputs structured JSON"
- Keywords that signal "production": unattended, schedule, fixed, handle errors, no questions, structured.
- Ask for retries: "Add retry config: up to 3 retries, exponential backoff starting 30sec" [loom_CC_P3_1_2_The_Agentic_Gap]

**Scheduled Research Agent (Cron + Firecrawl + Google Sheets)**
- Cloud Code + trigger.dev + cron schedule = daily research briefing written to Google Sheets automatically
- Cron syntax: `0 8 * * *` = 8am every day. Setup in trigger.dev env, Google Sheets service account + OAuth, Firecrawl API.
- Watch runs in trigger.dev dashboard for errors, traces show every step. If Firecrawl fails, still writes partial row (fail-safe design). [loom_CC_P3_1_6_Masterclass_Scheduled_Research_Agent]

**Webhook-Triggered Workflows (event-driven)**
- n8n form → HTTP POST to trigger.dev webhook → TypeScript task fires → Google Docs generated → saved to Drive (all in background).
- Setup: n8n form node + HTTP request node (bearer auth + secret key) → trigger.dev task receives JSON payload.
- Use case: lead intake form → auto-generate client proposal, auto-log to Airtable, auto-email receipt. King David: portfolio page contact form → trigger client intake workflow. [loom_CC_P3_1_7_Masterclass_Webhook_Report_Generator]

**Error Handling Layers (defense-in-depth)**
- Layer 1: Logging, every meaningful step + context. "Fire crawl returned 429 on source 3" not just "failed".
- Layer 2: Try-catch, wrap every external API call. Log error, continue where possible, only throw for critical failures.
- Layer 3: Retries, trigger.dev auto-retries; configure (3x, exponential backoff).
- Layer 4: Alerts, email/Slack fired on failure (trigger.dev dashboard → Alerts section, <2 min to setup).
- Layer 5: Debugging, copy full trace from trigger.dev, paste into Cloud Code: "This trace failed, what broke?" Cloud diagnoses and redeploys. [loom_CC_P3_1_8_Error_Handling]

---

### **Phase 4: Full-Stack Apps (Frontend + Backend + Auth + Payments)**

**Mental Model: Frontend (browser) + Backend (server)**
- Frontend = what user sees/clicks (HTML/CSS/JS, runs in browser)
- Backend = business logic, APIs, databases (runs on server)
- Flow: user clicks button (frontend) → sends request to backend (server) → server runs workflow, calls APIs → response back to frontend → UI updates
- Design matters (users expect clean UX). Speed matters (10sec wait = app looks broken). Security matters (real user data). [loom_CC_P4_1_2_Mental_Model_to_Building_Apps]

**Full-Stack Architecture for Lead Qualifier (replicable)**
- Backend: trigger.dev task (TypeScript, Claude API, structured analysis)
- Frontend: Vercel (React/Next, form to input lead info, results page to display report)
- Database: Supabase (store user accounts + lead history)
- Integration: Vercel calls trigger.dev webhook via environment secret → results returned → displayed on results page
- Payment: Stripe checkout on Vercel frontend → payment recorded in Supabase → usage limits enforced in backend
- Deploy steps: (1) build workflow on trigger.dev, (2) build UI on Vercel (use Anthropic frontend design skill for polish), (3) connect Vercel ↔ trigger.dev via secret keys, (4) test end-to-end. [loom_CC_P4_1_4_AI_Lead_Qualifier_App, loom_CC_P4_1_2_Mental_Model_to_Building_Apps]

**Anthropic Frontend Design Skill (non-generic UX)**
- Use skill: "Build website using Anthropic's frontend design skills (avoid purple gradients, clichés, generic patterns)"
- One-shot prompt + skill = modern, professional site (typography, motion, color harmony). Prevents "obviously AI-generated" look.
- King David's existing `/website` skill should call this on next build. [loom_CC_P4_1_4_AI_Lead_Qualifier_App]

**Authentication + Role-Level Security (Supabase)**
- Supabase signup/login pages auto-created by Cloud Code (email + password).
- RLS (Role-Level Security) = database rules prevent users seeing other users' data (belt-and-suspenders security).
- User history (leads analyzed) persisted in Supabase table, visible only to that user.
- Setup: 1) Create Supabase project, 2) Cloud Code generates SQL schema, 3) Run SQL in Supabase editor, 4) Add Supabase URL + key as Vercel env vars, 5) redirect URLs configured in Supabase auth settings.
- Result: User logs in → sees only their own lead history. [loom_CC_P4_1_5_Authentication_Security_Audit]

**Stripe Payment Integration (free tier + paid tier)**
- Free: 2 lead qualifications/day
- Pro: 29/month = unlimited qualifications
- Setup: (1) Create Stripe product + pricing in test mode, (2) Cloud Code generates checkout flow + subscription tracking, (3) Set env vars (Stripe secret key, publishable key, price ID, webhook secret) in Vercel, (4) Create Supabase subscriptions table via SQL, (5) Stripe webhook sends checkout_complete event → Vercel receives → user marked as subscriber, (6) Backend enforces limits based on Supabase subscription status.
- Test with Stripe test card (4242424242424242).
- Revenue unlock: Quota system (usage tracking) + Stripe checkout (payment) + Supabase (subscription state) = metered SaaS. [loom_CC_P4_1_6_Stripe_Payments]

**Security Audit Prompt (catch before launch)**
- Run: "Audit codebase for: all protected routes require auth, no API keys in frontend, env vars for all secrets, RLS enabled, report issues by severity"
- Cloud Code acts as security reviewer, flags issues (rate limiting, token expiry, CORS).
- Fix: ask Cloud Code to remediate. [loom_CC_P4_1_5_Authentication_Security_Audit]

---

### **Phase 1: Enhancement Philosophy (already covered, but deepening)**

**Working vs Working Well (4 layers to upgrade)**
- Layer 1: Error handling, what breaks? (fix first)
- Layer 2: Logic improvements, what's inefficient? (fix next)
- Layer 3: Output quality, user experience/formatting (polish third)
- Layer 4: Performance, speed/latency (optimize last)
- Don't do all at once. Iterate in layers. Test happy path + edge cases after each change. [loom_CC_P1_3_1_Intro_Enhancement_Philosophy]

---

## KING DAVID'S NEXT MOVES (Ranked by impact x feasibility)

1. **Refactor 29 skills into individual `.claude/skills/` folders** (today, 30 min)
   - Move hard-coded workflows from `/commands/` → `.claude/skills/<skill_name>/skill.md`
   - Gain 40%+ context savings. Load only invoked skills.
   - [loom_CC_P2_1_7_Skills]

2. **Build scheduled research agent** (2-3 hours)
   - Use Phase 3 template: topic → Firecrawl → Google Sheets daily
   - Replace manual `/newsletter` calls with unattended trigger.dev schedule
   - Client pitch: "Daily briefing written to your Sheets automatically"
   - [loom_CC_P3_1_6_Masterclass_Scheduled_Research_Agent]

3. **Add Stripe to `/lead_qualifier_app` skill** (Phase 4 pattern)
   - Free tier: 2 leads/day. Pro: 29/month unlimited.
   - Full-stack: Vercel frontend + trigger.dev backend + Supabase auth + Stripe checkout
   - Revenue: first SaaS app built in <1 afternoon
   - [loom_CC_P4_1_6_Stripe_Payments, loom_CC_P4_1_5_Authentication_Security_Audit]

4. **Upgrade existing `/dtransform` to Phase 3** (3-4 hours)
   - Add webhook trigger (n8n form → trigger.dev task → Google Docs report)
   - Client fills form → proposal auto-generated + saved to Drive
   - Pricing unlock: charge 100-500 for intake form automation alone
   - [loom_CC_P3_1_7_Masterclass_Webhook_Report_Generator]

5. **Apply enhancement layers to top 3 skills** (error → logic → output → performance)
   - Start with `/scrape`, `/website`, `/monetize`
   - Each: 1 enhancement pass = agency-grade quality
   - [loom_CC_P1_3_1_Intro_Enhancement_Philosophy]

---

## NEW TOOLS / MCPS INTRODUCED IN CC PHASE 2-4

| Tool/MCP | Use Case | Setup | Status |
|----------|----------|-------|--------|
| **Firecrawl MCP** | Web search + scraping in workflows | Install via Cloud Code, add API key | Active |
| **trigger.dev** | Schedule + webhook-trigger tasks | GitHub + deploy button + env vars | Active |
| **Supabase** | User auth + role-level DB security | Sign up + create project + SQL schema | For apps |
| **Stripe** | Monthly subscription payments + metered usage | Create product + add to Vercel env vars | New pattern |
| **Anthropic Frontend Design Skill** | Polish UI (no generic gradients) | Built-in, call in prompt | New |
| **trigger.dev Dashboard** | Monitor runs, retries, logging, alerts | mcp.so or GitHub | Active |

---

## NOT IN EXISTING MASTER SUMMARY (KEY GAPS FILLED)

- **Agentic gap explained**, why Phase 3+ fails silently, how to close it (prompting, logging, alerts, retries)
- **Skills as on-demand modules**, context math, when to use (.claude/skills/ vs CLAUDE.md vs inline)
- **Webhook architecture**, event-driven workflows (n8n form → trigger.dev task → output)
- **Full-stack app pattern**, Vercel + trigger.dev + Supabase + Stripe (monetization layer)
- **Security audit prompt**, catch issues before launch, ask Cloud Code to fix
- **Enhancement philosophy**, 4-layer upgrade path (error → logic → output → performance)
- **Anthropic Frontend Design Skill**, call before building UI to avoid "AI look"

---

*End of absorb_v2_cc.md. Master summary updated 2026-05-23, refer here for Phase 2-4 tactical details. For Phase 1 baseline, see master summary §1-6.*
