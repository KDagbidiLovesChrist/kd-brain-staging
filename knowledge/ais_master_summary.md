# AIS Master Summary · King David's Quick-Reference

*v2.1 compressed 2026-05-23 evening (fresh session). ≤500 lines hard cap. Compressed from 461→target ~350 to make headroom for wave 1 (100-URL) absorption.*

**Sources merged:**
- v1: `.tmp/absorb_cluster_AB.md` + `absorb_cluster_CD.md` + `absorb_audit_meta.md` + `ais_all_learnings.md`
- v2: `.tmp/absorb_v2_cc.md` (46 Claude Code) + `absorb_v2_bp.md` (39 Build Portfolio) + `absorb_v2_meta.md` (orphan + gap audit)
- Pending v3 (wave 1): 100 new Loom transcripts, clusters tbd

**Read this lean entry point first. The `.tmp/` files have deep-dive detail when needed.**

**Direct quotes moved out:** see `ais_quotes.md` (7 quotes preserved verbatim).

---

## 1 · WAT Framework (Nate Herk · AIS+ Claude Code 1.3)

- **W = Workflow**, markdown SOP (the steps)
- **A = Agent**, Claude reads, reasons, decides
- **T = Tool**, Python / MCP / API executes
- **+ S = Skill** layer (King David's extension): `/command` fires the chain → **MONEY**

**Attribution rule:** when pitching clients, credit Nate. Internal use: WAT. Client-facing: **Three Ms** (Memory · Mechanics · Monetisation, same shape, less jargon).

---

## 2 · Token Management (AIS+ Claude Code 1.10)

### 5 Prompting Patterns
1. Define the goal, not the steps, WHAT not HOW
2. Be specific about output, format, length, audience
3. Plan mode first for non-trivial tasks
4. Give feedback, not corrections, explain WHY
5. Treat agent as expert, don't micromanage; push back

### Context Rot Thresholds (hard numbers)
- **0, 50% Green**, full focus, all features on
- **50, 70% Yellow**, start thinking about `/compact`
- **70, 85% Orange**, run `/compact` now
- **85%+ Red**, run `/clear` immediately

### 5 Token-Saving Strategies
1. One task per session
2. Define "done" upfront (exit criteria)
3. Skills > bloated CLAUDE.md (skills load on demand)
4. Disable unused MCP servers
5. Cap CLAUDE.md at 500 lines

---

## 3 · Build Portfolio Phase 3 · Discovery Framework

**Goal:** turn discovery into two paid deliverables, **Opportunity Map** (ICE-scored ideas) + **Wireframe / Blueprint** (visual mockup of #1).

### Time + Income Lens (4 discovery questions)
- **Time:** *"Which team is most burdened by manual work?"* + *"If you gave them back 5 hrs/week, what would they do?"* → translate to FTE cost saved.
- **Income:** *"If we doubled your leads tomorrow, what process breaks first?"* + *"What constraint is tethering revenue?"* → frame as revenue unlocked.

### SOP Audit · 3-step gap-finding
1. **Inventory** what SOP docs exist
2. **Compare** docs to actual practice
3. **Find** tribal knowledge never documented
Charge for the audit itself.

### ICE Scoring + Live Blueprint
- Score 1-10 on **Impact · Confidence · Ease**. **Critical: score WITH the client.**
- Live wireframe drawn in front of CEO: 1) Trigger 2) Data flow 3) Decision points 4) AI steps 5) Output. **This wireframe IS the close.**

### Charge for the Opportunity Map?
| Credibility | Pricing |
|---|---|
| **Authority** (proof, content, results) | Upfront, premium |
| **Beginner + warm network** | Pay-after (results-based) |
| **Beginner + cold prospects** | Skip · do one automation first, build proof |

Two versions: Light (1-2 hrs, free lead magnet) vs Deep Dive (multi-day, always paid).

---

## 4 · TrueHorizon $211k Deal · Sales / Delivery Playbook

**Client:** US insurance company. Manual underwriting, policy endorsements, chatbot gaps. Regulated → audit trails + compliance.

### Sales Cycle (9 weeks)
Inbound prospect arrived with pre-mapped agent ideas (highest buying signal) → 28 min demo + 15 min brainstorm + 15 min pricing → NDA + tech partner loop (2 wks) → Proving-ROI call with wireframes + 7-8min→30sec demo → 6-wk negotiation (hourly → enterprise; omnichannel email/phone/SMS; competitor intel surfaced higher budget).

### Pricing Anatomy
| Component | $/month |
|---|---|
| Base (dev + maintenance) | $12,000 |
| Reviewer agent #1 | +$2,000 |
| Reviewer agent #2 | +$2,000 |
| Chatbot agent | +$2,500 |
| Processor agent | +$1,000 |
| **8-month total ~ $211k** | ramp 12→16→18.5→19.5k |

**Rule: NEVER quote dev hours.** Quote agents deployed / outcomes / retainers.

### Delivery (5 phases)
Kickoff → Architecture/Roadmap → Development → Delivery/Handoff → Deployment. **ClickUp 6-category board:** Inbox · Product Backlog · Current Priorities · In Progress · Review · Done. Loom-required on every completed task.

### Sales Pipeline Framework
- **Opening line:** *"How bullish are you on AI?"*
- **BAT qualification:** Budget · Authority · Timeline
- **Post-call automation:** Fireflies API → proposal template
- **Reminder cadence:** 24-hr + 1-hr SMS/email
- **No closing call needed** if discovery is right, ROI demo IS the close
- **Contract/payment:** PandaDoc + QuickBooks

### Replicable SMB Pattern · Dublin Plumber (€500-2,000)
1. **Pain:** missed calls, callback chaos, scheduling
2. **Proposal:** voice agent answers + qualifies + books calendar + texts confirmations
3. **ROI:** 3 missed calls × €150 = €450/mo recovered
4. **Scope:** 1-2 agents, 6-week deployment
5. **Pricing:** €1,500, 3,000 setup + €200, 500/mo retainer
6. **Pitch:** *"You'll pay for this in 3-4 months from recovered jobs alone"*
7. Close in 1-2 calls (not 9 weeks, that's enterprise pace)

---

## 5 · Build Your AI OS · Productised Offer Playbook

**Nate's definition:** layer of intelligence on top of OS (files, apps, data). AI sees ALL and acts.
- **Four Cs (sequence-locked):** Context → Connections → Capabilities → Cadence
- **Seven tier-1 buckets:** Revenue · Customer · Calendar · Comms · Tasks · Meetings · Knowledge
- **Tool-agnostic**, the durable layer underneath matters more than n8n vs Claude Code vs Codex

### 9-Lesson Curriculum
1. What is an AI OS · 2. Three Ms (Mindset · Method · Machine) · 3. Four Cs · 4. Onboarding (/onboard 7Q interview) · 5. Connecting Tools (APIs > MCPs for tokens; dedicated AI accounts) · 6. Building Skills (markdown recipes; /skill-builder) · 7. Routines (local vs cloud routines vs /loop) · 8. Knowledge Wikis (Karpathy LLM Wiki: raw/→wiki/ with backlinks; Obsidian frontend; Claude Artifacts dashboards) · 9. Share build (#AISOS)

### Pricing Model
| Tier | Setup | Retainer |
|---|---|---|
| Entry | €1,000-2,500 | €100-300/mo |
| Mid-market | €3,000-5,000 | €300-500/mo |

**Hybrid:** setup + 3-month retainer for commitment. After mo. 3, upsell annual at 10-month discount.

### Onboarding Sequence (8-week summary)
Intake call → /onboard interview → Kickoff workshop → Connection (wks 1-2) → Skills (wks 2-3) → Cadence (wks 3-4) → Knowledge scaffolding (wk 4) → Handoff + training (wks 4-5).

### Positioning
- **One-off:** *"Build me a bot"* → reactive, scope creep, forgotten
- **AI OS:** *"Let's build your intelligence layer that scales as you grow"* → proactive, documented, client owns it
- **Key shift:** you don't build FOR them; you TEACH them to build it + coach gaps.

---

## 6 · Tools / APIs / MCPs · Status Matrix

### Installed / Active ✅
Anthropic API · Perplexity API ($50 credits) · Gmail SMTP · Brave Search MCP · Firecrawl MCP · Playwright MCP · n8n-mcp (settings.json, needs CC restart) · Vercel CLI v54.1.0 · n8n v2.20.9 · Ollama v0.24.0 · Bun · ffmpeg · gh · GitHub PAT (expires Jun 16, 2026) · Token Dashboard · yt-dlp + faster-whisper · YouTube + Loom transcript extractors · Claude Code Routines · Claude Agent SDK · Obsidian REST API (port 27124) · AWS Bedrock (work) · Google CLI (Gmail/Sheets/Drive/Calendar, wired 2026-05-23) · KIE_AI key.

### Surface to King David ⚠️ (decisions pending)
- **ClickUp**, PM (TrueHorizon 6-cat board), free, install when client #2 lands
- **Cal.com**, booking (Luca template, plumber pitch), free
- **Resend**, transactional email (3,000/mo free), better than Gmail SMTP for clients
- **Glaido**, STT (Nate's pick), free tier, **macOS-only**, parked
- **Pinecone / Supabase**, vector DBs, free tier, when building client RAG agent
- **AIS LIVE ticket**, see §10, TIME-SENSITIVE

### Skipped (paid, deferred per faith/budget)
Vapi · ElevenLabs · HeyGen · Lindy · Loom Pro · Apify paid · Airtop · Blotato · Poppy AI · PandaDoc · Datadog · GPTZero API ($45/mo).

---

## 7 · Top 10 Highest-Leverage 30-Day Actions

1. Apply Phase 3 framework verbatim to next client discovery
2. Sell Setup Hours (`/setup_hours` €100, 500/session), first-money-fast, no retainer cycle
3. Replicate Luca's auto-detailing architecture (n8n + Sheets + Telegram + Cal.com + Resend + Drive) for Dublin plumber pitch (€500, 2,000)
4. Adopt TrueHorizon 5-phase delivery + ClickUp 6-cat board for second client
5. Bake value-based ROI dashboard into every client build, drives 80%+ retention
6. Apply Token Mgmt rules NOW: 50/70/85 thresholds + 5 prompting patterns + 5 strategies (real money on Opus 4.7)
7. Curtis Morgan "Decision Rules First", spend 60% of discovery on prioritisation with client, not building
8. Always check n8n-mcp 2,352 templates before building from scratch, 99% has a template
9. Reframe pitch around solutions, not agents, talk pain points (leads, hiring, payroll) not tech
10. Apply Enhancement Philosophy on existing 29 skills (error handling → output → UX), agency-grade in <1 day each

---

## 8 · Courses Worth Deep-Transcribing Next (Ranked)

1. **AIS+ Claude Code Phase 2 (11 modules)**, First Agentic Workflow, MCP, Firecrawl, Skills, Skills in Action, Slide Deck, Personal Challenge. Direct upgrade path for 29 skills.
2. **AIS+ Build Your Portfolio Macro 2, Agent Zero RAG/Vector DB (9 modules)**, upgrades `/search` directly.
3. **AIS-free "Build Your AI OS" 9 modules**, unlocks `/os_builder` (need Level 3 grind first, ~30 min).
4. **AIS+ Community Resources → Nate's Business Talks (16 modules)**, Your First Client, Pricing Workflows, Stop Selling Agents, $1.2k/$1.65k/$2.6k case studies. Highest dollar-per-minute lesson tier.
5. **AIS+ Live Call TrueHorizon Discovery SOP**, full enterprise sales template; SOP reusable at SMB scale.
6. **AIS+ Live Q&As (10 priority):** Service/product offer · Building Trust · Discovery & Niching · First Consulting Call · QA & Comms · AI Audits · Framing Offers · High Impact Low Effort · AI Business Consulting · Second Brain.
7. **AIS-free "AI Business Navigation" (16 modules)**, tightest course on the revenue path.

**Low priority / skip:** AIS+ Success Stories, Archived (142 modules), Claude Code free (duplicates).

---

## 9 · Open Surfacing Questions (live)

1. **Codify `/setup_hours` SOP** from "AI Offer You Can Sell Tomorrow Morning" video?
2. **Glaido Windows release**, check periodically for STT upgrade.
3. **Draft `/plumber_full_stack` DEV skill** (Luca architecture template)?
4. **Draft `/lead_qualifier_app` skill** (frontend on `/scrape`, per CC Phase 4 Module 1.4)?
5. **Wait 23 days vs upgrade Premium** for Get Your First Clients (17 modules)?
6. **Build `/email-agent`** (Gmail triage + KB-matched replies, from Workflow 1 in ais_workflows.md)?
7. **Build `/kb-indexer`** (dedicated ingestion skill, partly covered by `/search`)?

*(Stale items removed 2026-05-23 v2.1: first client already booked, AIS+ tier known.)*

---

## 10 · AIS LIVE · July 11-12, 2026 (TIME-SENSITIVE)

- **Format:** Virtual, 2 days. *"Real Projects, Real Revenue"*, every speaker shows actual work, clients, numbers.
- **Day 1:** what businesses are paying for in 2026, projects, industries, deliverables.
- **Day 2:** niche · cold outreach → calls · discovery that closes · pricing · delivery · retainer conversion. **King David's exact bottleneck.**
- **Cap:** ~3,000 seats, 3,600+ members → sells out fast.
- **Registration:** https://app.aiautomationsociety.ai/ais-live/register/
- **Source:** https://www.skool.com/ai-automation-society-plus/heres-how-to-get-your-tickets-to-ais-live
- **AIS+ Annual:** FREE VIP ticket ($199 value), check email
- **AIS+ Monthly:** 50% off with code `AISLIVE50`
- **Annual upgrade math:** $699/yr vs $99/mo = $1,188 → save $489 + free ticket to every future quarterly AIS Live
- **Action needed within days.**

---

## 11 · Existing Skills Coverage & Gaps

**Already covered** by King David's 29 skills (`commands/`): newsletter · scrape · website · video-to-website · cold-email · proposal · agent-team · subagent_registry · orchestrate · research · content · excalidraw-visuals · save · handoff · recover · exec · studynotes · context · search · monetize · dtransform · cv-tailor · skool-post · ais · master_prompt · deploy · capstone · setup_hours (scaffold) · os_builder (scaffold).

**Net new skill gaps to consider:**
- `/plumber_full_stack` (Luca template, DEV)
- `/lead_qualifier_app` (frontend on `/scrape`)
- `/email-agent` (Gmail triage + KB replies)
- `/kb-indexer` (dedicated ingestion)

For full mapping see `/ais` skill output.

---

## 12 · Direct Quotes

Moved out for headroom, see `ais_quotes.md`. 7 quotes preserved verbatim (TrueHorizon × 2 · Nate AI OS × 3 · Kidlin's Law · Curtis Morgan).

---

## 13 · Upgrades to Existing King David Skills

- **`/monetize`:** add BAT framework. 9-week enterprise cycles are NORMAL. Use SMS when email stalls.
- **`/dtransform`:** insert "proving ROI" call BEFORE proposal (wireframes + API docs + efficiency numbers). Demo, don't just describe.
- **`/os_builder`:** follow 8-week onboarding. Teach client to build it, don't build FOR them. €1k-5k setup + €100-500/mo for check-ins.

**Across the board:** NEVER quote dev hours. Quote outcomes / agents / retainers. Agent-by-agent pricing grows MRR within ONE contract. Tool-agnostic framework avoids tech betting.

---

## 14 · Claude Code Phase 2-4 · NEW Tactical Insights (v2)
*Source: `.tmp/absorb_v2_cc.md`, 46 transcripts.*

### 14.1 The Agentic Gap (Phase 3 critical shift)
Cloud Code self-heals locally. Trigger.dev / scheduled cloud tasks DO NOT. Once deployed, no one's watching unless alerts fire.
**Close the gap with:** fixed inputs · structured outputs · try/catch on every external API · logging at every step · email/Slack alerts on failure · auto-retries with exponential backoff.
**New prompt language:** *"Build an UNATTENDED scheduled task that handles errors without crashing, logs every step, outputs structured JSON. Add retry config: 3x, exponential backoff starting 30sec."*

### 14.2 Skills As On-Demand Modules (context-saving math)
Skills load ONLY when invoked. `.claude/skills/<name>/skill.md` beats inline CLAUDE.md by ~20×.
**Math:** 1 skill inline in CLAUDE.md = 200 lines loaded EVERY session. Same skill as `skill.md` = 200 lines loaded only when invoked.
**Action:** Migrate King David's 29 skills from `commands/` to `.claude/skills/<name>/skill.md` folders (~30 min, huge context win).

### 14.3 Full-Stack SaaS in One Afternoon (Phase 4)
Vercel (frontend) + Trigger.dev (backend) + Supabase (auth + DB + RLS) + Stripe (payments) = monetized full-stack app in <4 hours.
**Replicable architecture:**
1. Workflow on trigger.dev (TypeScript)
2. Frontend on Vercel (React/Next + Anthropic Frontend Design skill for non-AI-looking UI)
3. Supabase signup + RLS for per-user data isolation
4. Stripe checkout (free tier 2/day · Pro $29/mo unlimited)
5. Security audit prompt: *"Audit: all protected routes require auth, no API keys in frontend, env vars for all secrets, RLS enabled. Report by severity."*

### 14.4 Webhook-Triggered Workflows
n8n form → HTTP POST to trigger.dev webhook → TypeScript task fires → Google Docs auto-generated → saved to Drive.
**Use cases:** lead intake form → auto-proposal · portfolio contact form → auto-onboarding · client intake → auto-Airtable + auto-receipt.

### 14.5 Enhancement Philosophy · 4-Layer Order
Apply in sequence: 1) Error handling 2) Logic 3) Output quality 4) Performance. Test happy path + edge cases after each. Don't do all four at once.

### 14.6 New Tools Surfaced (Phase 4)
- **Supabase**, user auth + role-level DB security (RLS)
- **Stripe**, metered SaaS billing (free + paid tiers)
- **Anthropic Frontend Design Skill**, built-in, prevents generic-AI UI
- **trigger.dev Dashboard**, live monitor: runs, retries, traces, alerts

---

## 15 · Portfolio Building Discipline (BP v2)
*Source: `.tmp/absorb_v2_bp.md`, 39 transcripts.*

### 15.1 Three Universal SMB Pain Points (90% coverage)
1. **Not enough leads**, scraping + enrichment + outreach + qualification
2. **Hiring drains time**, resume screening, candidate outreach, onboarding
3. **Payroll bleeds on manual work**, customer support AI, data entry, reports

**Action:** Build one demo per category (3 total). Portfolio applies to ANY business after that.

### 15.2 "Build First, Niche Emerges"
- DON'T overthink niche before building. Build 5-10 portfolio pieces solving real problems. Niche FINDS YOU through actual client work.
- **Exception:** if you have DEEP credibility (10+ yrs industry, spoke at events), specialise immediately.

### 15.3 Portfolio = Proof
- Bottleneck is NOT sales skills. It's PROOF.
- **Old framing:** "I can automate customer support for you" → guinea-pig vibe
- **New framing:** "I built a customer support automation. It works. Let me adapt it for you."
- **Documentation = portfolio gold.** Build + 2-min screencap doc IMMEDIATELY after finishing.

### 15.4 Process Mapping Before Building (Kidlin's Law)
> *"If you write the problem down clearly, the matter is half solved."*
- 15 min mapping saves 2+ hrs rework.
- **Template:** Trigger → Data → Decision Points → AI Steps → Human Checkpoints → Fallback → Output.

### 15.5 Income Lens Flywheel
> *"If I got 10 great referrals tomorrow, what breaks first?"* That's your constraint.

### 15.6 ICE Scoring + Golden Square
- **Impact** (saves time? scales? removes bottleneck?) · **Confidence** (process clear? tools available?) · **Ease** (integrations? logic complexity?)
- **Final score = (I×2 + C + E) / 4**, weight Impact 2× because it drives ROI
- **Golden Square = High Impact + Low Complexity. Start there. Skip the rest.**

### 15.7 Workflow vs Agent Decision Rule
- **WORKFLOW** if: predictable, deterministic, clear rules → "if X > 10, route here" → n8n
- **AGENT** if: unpredictable, needs reasoning, non-deterministic → "read email, draft reply" → Claude
- **Most SMB problems are WORKFLOWS, not agents.** Don't over-engineer.

### 15.8 Documentation Cadence
- Build without docs = file on computer
- Build + 2-min doc = client case study
- Do it IMMEDIATELY, memory fades within 24 hrs.

---

## 16 · Meta Findings (v2 audit)
*Source: `.tmp/absorb_v2_meta.md`.*

### 16.1 Top 3 cross-cluster takeaways
1. **Discovery cadence > build quality.** TrueHorizon: 9-week cycle → $211k. Phase 3: 60% of discovery time on prioritisation, not scoping (Curtis Morgan rule).
2. **Agent-by-agent pricing compounds MRR within ONE contract.** $12k base + $2-2.5k per deployed agent = grows month-to-month.
3. **Token Mgmt = gating factor for session quality, not LLM choice.** §2's 5 strategies could cut Opus 4.7 costs by 30-50%. Apply NOW.

### 16.2 Known gaps (callout-only, not blockers)
8 deep-dives still uncovered in untranscribed modules:
n8n-mcp wiring SOP · prompt engineering beyond 5 patterns · MCP server setup tutorial · Vercel deployment SOP · error-handling pattern library · Firecrawl vs Brave Search comparison · RAG vector DB selection · Luca plumber full-stack architecture deep-dive · TrueHorizon IP-ownership contract language.

**Action:** King David hits these naturally as he grinds the course. Not blocking.

---

## 17 · Wave 1 Absorption (2026-05-23 evening)
*Source: `.tmp/absorb_v3_wave1.md` (full distillation, 110 lines). 8 unique transcripts, 7 with content. Most are AIS-free onboarding (no value). One is gold: the TrueHorizon $211k Fathom workshop.*

### 17.1 The TrueHorizon Fathom transcript (57min) · NEW details beyond §15
- **Buying signal hierarchy:** (1) prospect arrives with their own AI agent ideas, "highest buying signal we've seen"; (2) bullish on AI + sees competitive necessity; (3) C-suite decision-making power. All three = clear ICP.
- **Tiered SLA pricing:** Enterprise plan = top PM + 2 engineers + solutions architect; Business plan = junior PM + 1 engineer. Reusable for future client tiering.
- **IP ownership clause:** client owns *deployed* IP, agency keeps pre-deployment IP (protects reusable components). Direct contract-language pattern.
- **Margins:** >50% on $12k/mo base. Main cost = engineering salaries. LLM + n8n cost = negligible (enterprise n8n license free via Nate partnership; LLM credits via startup programs).
- **Front-end demo > n8n demo for sales**, confirms `/video-to-website` and `/website` as sales-acceleration assets, not just deliverables.
- **Client revenue range for $211k deal:** $50M, $100M ARR mid-market. Anchor for prospect qualification.
- **Reusable component library (their IP):** Google Drive multimodal indexer · NLP-to-SQL · NLP-to-n8n (proprietary) · n8n CI/CD DevOps tool (proprietary).

### 17.2 New AIS+ member perk (action required)
**539+ AI tool discounts portal** via AIS+ partnership. Bolt.new = 1-yr Pro free. Notion = 6-mo Business + unlimited AI. Airtable, Apollo, Slack, Perplexity discounts listed. **King David, claim Bolt.new + Notion Monday.** ~5 min, real value.

### 17.3 Community monetisation channel
**"Earn With Gems":** admins promote valuable Skool posts → pinned + **$20 cash per post** + classroom permanence. Gem-worthy = frameworks, client walk-throughs, before/after demos. Update `/skool-post` skill to target this pattern.

### 17.4 Other 6 transcripts
AIS-free onboarding (3 videos), cancel-page retention loop (1), Skool template import (1), empty body (1). All SKIP for install, patterns logged in `.tmp/absorb_v3_wave1.md`.

### 17.5 Recommendation
Mirror §17.1 patterns 1, 3 (tiered SLA), and "front-end demo > workflow demo" to `DCEO_BRAIN\knowledge\patterns.md` for Orcha, they translate cleanly to stakeholder/vendor escalation patterns at Amazon.

---

*End of master summary v3.0. Cluster originals in `.tmp/`. Full v1 audit: `ais_all_learnings.md` (779 lines, re-read only if a section here is unclear).*
