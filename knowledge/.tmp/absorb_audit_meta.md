# AIS Audit · Meta Findings (Cluster E)
**Generated:** 2026-05-23 · **Scope:** audit_log/ + ais_resources/ + commands/ glob (transcripts excluded, covered in clusters A/B/C/D)

---

## 1. Inventory Snapshot

**AIS+ paid classroom (8 accessible courses + 2 locked):**
| Course | Modules | Done | Status |
|---|---|---|---|
| START HERE | 8 | 8 ✅ | done |
| AI Partner Model | 6 | 6 ✅ | done |
| Build Your Portfolio | 62 | 15 (24%) | 47 untouched |
| Claude Code | 50 | 0 | untouched |
| Get Your First Clients | 17 | 0 | 🔒 23d or Premium |
| Scale | 84 | 0 | 🔒 83d or Premium |
| Member Perks | 13 | 0 | untouched |
| Live Call Recordings | 82 | 0 | Q&A library |
| Community Resources | 167 | 0 | peer gold |
| Archived | 142 | 0 | low priority |
| **AIS+ total accessible** | **~553** | **29 (5%)** | |

**AIS-free classroom (10 priority courses inventoried):** Build Your AI OS (9), n8n Templates (73), AI Business Navigation (16), Claude Code free (33), Discount Codes (9), Agent Skills (6), Your First AI Agent (16), 10 Hours to 10 Secs V2 (22), AIS Podcast (4), AIS+ Success Stories (31) = **~219 modules**, all untouched.

**Grand total:** ~772 modules across both communities.

**Transcribed coverage:** 12 videos already transcribed (8 Loom BP3 + 2 Fireflies TrueHorizon + Fathom + build_your_ai_os) = **~1.5% of total module count**, but covers the highest-leverage tactical lessons (WAT 1.3, Token Mgmt 1.10, BP3 Phase 3, $211k deal anatomy).

**What's left:** ~98% of modules. Highest-value remaining = AIS+ Claude Code Phase 1+2+3+4 (50 modules video-only), Build Your Portfolio macro 2+3 (47 modules), Nate's AI Business Talks (16 audio lessons), TrueHorizon Discovery SOP, n8n Templates library (133 templates across free + paid).

---

## 2. Top 10 Highest-Leverage Skills/Patterns (30-Day Action)

1. **Sell Setup Hours (€100, 500/session)**, already scaffolded as `/setup_hours`. Why: first-money-fast, no retainer cycle, fits "did first client booking → need second client" stage.
2. **Luca Giovinazzo Auto-Detailing Architecture Template**, n8n + Sheets + Telegram + Cal.com + Resend + Drive. Why: directly portable to Dublin plumber pitch as €500, 2,000 paid build. Replicable.
3. **TrueHorizon 5-Phase Delivery Workflow** (Kickoff → Architecture → Dev → Delivery → Deploy) + ClickUp 6-category board. Why: turns ad-hoc client work into a repeatable system, required for second client + retainer conversion.
4. **Value-Based Pricing + ROI Tracker pattern**, bake ROI dashboard into every client build (time saved per run → 30/60/180-day reports). Why: makes retainers self-justifying = 80%+ retention.
5. **Token Mgmt 5 Strategies + Context Rot threshold** (50/70/85 yellow/orange/red, /clear vs /compact). Why: King David runs Opus 4.7 max-effort, costs hit fast. Drops from 60%+ context = mistakes; this changes session discipline today.
6. **5 Cloud Code Prompting Patterns** (goal-not-steps, specific output, plan-mode-first, feedback-not-corrections, treat-agent-as-expert). Why: doubles output quality per session with zero new tooling.
7. **Curtis Morgan "Decision Rules First" insight**, spend 60% of discovery time on prioritisation rules with client, not the build. Why: directly fixes the "what to charge / what to scope" anxiety blocking second client.
8. **n8n-mcp 2,352 templates check before any build**, already added to settings.json. Why: 99% of client asks already have a template, start there, customise, save days.
9. **Stop Selling Agents, Sell Solutions** (positioning lesson), frame every pitch around the three pain points (leads, hiring, payroll), not the tech. Why: matches AIS Course 3 + plumber pitch sharpening.
10. **Enhancement Philosophy applied to existing skills** (error handling → output quality → UX, in order). Why: 12 existing skills can become agency-grade in <1 day each, leverage what's already built.

---

## 3. All Tools, APIs, Frameworks, MCPs Mentioned

**Installed / Active ✅**
- Anthropic API, Claude reasoning, paid, ✅
- Perplexity API, research, paid ($50 credits), ✅
- Gmail SMTP, newsletter delivery, free, ✅
- Brave Search MCP, web search, free, ✅ key live
- Firecrawl MCP, web scrape, free tier + paid, ✅ (member discount available)
- Playwright MCP, browser automation, free, ✅
- n8n-mcp, 1,650 nodes + 2,352 templates, free, ✅ added to settings.json (needs CC restart)
- Vercel CLI, site deploy, free, ✅ authed
- GitHub PAT, version control, free, ✅ expires Jun 16, 2026
- Token Dashboard (Nate Herk), local analytics 127.0.0.1:8080, free, ✅ installed
- yt-dlp + faster-whisper + imageio-ffmpeg, Loom/YouTube transcripts, free, ✅
- YouTube Transcript Extractor, for video-heavy AIS courses, free, ✅ built
- Claude Code Routines, scheduled automations, free, ✅
- Claude Agent SDK, programmatic agents, paid per token, ✅
- Obsidian REST API, vault writing, free (port 27124), ✅
- AWS Bedrock, model hosting at work, Amazon pays, ✅ (Orcha)

**Pending ❌ (King David action needed)**
- kie.ai (Nano Banana), Excalidraw PNGs, paid (~$0.02, 0.09/image), ❌ KIE_AI_API_KEY needed
- Google CLI (Gmail API + Sheets + Drive + Calendar), free, ❌ setup pending
- n8n paid plan, required for API key + workflow management, paid, ❌ deferred
- Premium AIS+ upgrade, unlocks Get Your First Clients (17 modules) + Scale (84 modules) instantly + $3M Savings Vault, paid, ❌

**Surface to King David ⚠️ (decisions pending)**
- ClickUp, project management (TrueHorizon 6-category board, Luca's build), free tier, ⚠️ install when client #2 lands
- Cal.com, booking (Luca's build, plumber pitch), free, ⚠️ install when first client needs booking flow
- Resend, transactional email (3,000/mo free), better deliverability than Gmail SMTP, ⚠️ first paid client
- Glaido, speech-to-text (Nate's pick, affiliate link), likely paid w/ free tier, ⚠️ check pricing, King David is voice-primary
- Pinecone / Supabase, vector DBs for RAG, free tier, ⚠️ when building client RAG agent
- AIS LIVE ticket, see §6, ⚠️ TIME-SENSITIVE
- Hermes, persistent agent platform (OpenRouter for routine, Codex/Claude for reasoning), varies, ⚠️ if "tank agent" still wanted
- Printing Press, wraps any API as agent-native CLI in 10 min, TBD, ⚠️ for client CRM/booking integrations
- Claude Design, Claude-native visual builder (3D scroll websites, PDFs, slideshows), TBD, ⚠️ upgrade path for /website
- Hostinger VPS, community discount, paid, ⚠️ if self-hosting needed

**Skipped (paid, deferred per faith/budget rules):** Vapi, ElevenLabs, HeyGen, Lindy, Loom Pro, Apify paid, Airtop, Blotato, Poppy AI.

**Cross-ref `to_install.md`:** All TIER 4 items confirmed installed. Glaido + Token Dashboard partial-status reconciled (Token Dashboard ✅; Glaido still ⚠️ unchecked).

---

## 4. Courses Worth Deep-Transcribing Next (Ranked)

**1. AIS+ Claude Code Phase 2, remaining 11 modules** (1.4 First Agentic Workflow, 1.5 MCP, 1.6 Firecrawl, 1.7+1.8 Skills + Skills in Action, 1.9 Slide Deck, 1.11 Personal Challenge). *Why:* Direct upgrade path to King David's current 29-skill arsenal. Phase 2 is where the WAT teaching lives.

**2. AIS+ Build Your Portfolio Macro 3 Phase 3, remaining 1 module** ("Should You Charge for the Opportunity Map?", retry already running) + Macro 2 Agent Zero RAG/Vector DB 9 modules. *Why:* Phase 3 IS the first-client → retainer playbook King David is mid-flow on. RAG content directly upgrades `/search` skill.

**3. AIS-free "Build Your AI OS" 9 modules** (Three Ms + Four Cs frameworks, Skills, Routines, Wikis/Dashboards). *Why:* Unlocks `/os_builder` (€1k, 5k setup + €100, 500/mo), King David's highest-margin offering. Requires Level 3 unlock first (~30 min grind).

**4. AIS+ Community Resources → Nate's AI Business Talks (16 modules)**, Your First Client, Pricing Workflows, Stop Selling Agents, $1,200 in 2 Hours, $2,600 in 2 Hours, $1,650 in 3 Hours, Why No One is Buying. *Why:* Pure money-tactic library. Each lesson = revenue case study with replicable framework. Highest dollar-per-minute lesson tier.

**5. AIS+ Live Call Recordings → TrueHorizon $211k Deal series (5 modules)**, Discovery Call SOP gold. *Why:* Full template for enterprise sales pipeline. Even at SMB scale, the SOP is reusable.

**6. AIS+ Live Call Q&As, King David's bottleneck shortlist (10 of 50+):** What service/product to offer · Building Trust in Outreach · Discovery Calls and Niching Down · First Consulting Call · Quality Assurance and Client Communication · Conducting an AI Audit · Framing AI Automation Offers · High Impact, Low Effort · Business Consulting and AI · AI Second Brain.

**7. AIS-free "AI Business Navigation" (16 modules)**, Mindset, Finding Clients, Pricing, Delivery, 5 revenue case studies ($1.2k/$1.65k/$2.6k/$23k/$6k). *Why:* Tightest course on the actual revenue path. Free, condensed.

**Lower priority:** Claude Code free 33-module list (mostly duplicates of AIS+ Phase 1/2 + YouTube videos already captured in 87-video database). AIS+ Success Stories (31 modules, inspiration, low actionable density). Archived 142 modules (skipped per relevance filter).

---

## 5. Open Surfacing Questions (still unanswered in `to_review.md`)

1. **Grind Level 3 now** to unlock "Build Your AI OS" course? (~30 min → unlocks `/os_builder` recipe)
2. **Watch + extract "AI Offer You Can Sell Tomorrow Morning"** 7-step plan? Already partly absorbed into `/setup_hours` scaffold, confirm whether to fully codify.
3. **Token Dashboard repo URL**, already resolved/installed.
4. **First client details**, who, what service, what price, what deadline? Still missing → blocks `clients.md` + CLAUDE.md updates + tailored next-client strategy.
5. **AIS+ membership tier**, annual or monthly? Determines free ticket vs `AISLIVE50` 50% off for AIS LIVE.
6. **Draft `/plumber_full_stack` DEV skill** modelled on Luca's auto-detailing build (n8n + Sheets + Telegram + Cal.com + Resend + Drive)?
7. **Check Glaido pricing**, improves voice-input quality materially?
8. **WAT attribution**, already corrected in CLAUDE.md + reference file ✅ (no longer open).
9. **`/lead_qualifier_app` skill**, frontend on top of `/scrape` (per Claude Code Phase 4 Module 1.4)?
10. **Wait 23 days vs Premium upgrade** to unlock Get Your First Clients (17 modules)?
11. **Extract Build Your Portfolio Phase 3 lesson descriptions** + flag for video-transcript pipeline?

---

## 6. AIS LIVE · July 11-12, 2026 (TIME-SENSITIVE)

- **Format:** Virtual event, 2 days. "Real Projects, Real Revenue", every speaker shows actual work, clients, numbers.
- **Day 1:** What businesses are actually paying for in 2026, exact projects, industries, deliverable formats.
- **Day 2:** Niche selection · cold outreach that books calls · discovery call that closes · pricing · delivery · retainer conversion. **Exactly King David's current bottleneck.**
- **Cap:** ~3,000 attendees, 3,600+ AIS+ members → first-come basis → will sell out.
- **Registration:** https://app.aiautomationsociety.ai/ais-live/register/
- **Source post:** https://www.skool.com/ai-automation-society-plus/heres-how-to-get-your-tickets-to-ais-live (4 days ago in AIS+ Announcements)
- **AIS+ Annual members:** FREE VIP ticket ($199 value), fill out form, **check email already**.
- **AIS+ Monthly members:** 50% off with code `AISLIVE50`.
- **Annual upgrade math:** $699/year vs $99/mo = $1,188 → save $489 + free ticket to every future quarterly AIS Live.
- **Why uniquely relevant:** King David just booked first client (per public Wins Recap). Day 2 = his exact bottleneck. Peer network at event = source for second-client referrals.
- **Action needed within days:** Confirm membership tier → claim or buy ticket.

---

## 7. Items Already Covered by Existing Skills (Don't Rebuild)

Cross-referenced against 29 skills in `commands\*.md`:

| AIS finding | Existing skill (don't duplicate) |
|---|---|
| Newsletter automation (n8n template) | `/newsletter` ✅ live |
| Lead scraper / Google Maps scraping / Apify | `/scrape` ✅ live + `/browser` fallback |
| Website builds (incl. 3D + scroll) | `/website` + `/video-to-website` ✅ |
| Cold outreach / cold email | `/cold-email` ✅ built |
| Proposal generation (Gamma proposals) | `/proposal` ✅ built |
| Multi-agent teams / agent swarm | `/agent-team` + `/subagent_registry` + `/orchestrate` ✅ |
| Multi-source research consensus | `/research` ✅ built |
| Content for 9 socials | `/content` ✅ built |
| Excalidraw images (Nano Banana) | `/excalidraw-visuals` ✅ built (needs KIE_AI key) |
| Session save / handoff / recovery | `/save` + `/handoff` + `/recover` ✅ (Nate's Skill.md = Plus-locked · skip) |
| Personal life OS / EA / second brain | `/exec` ✅ |
| Obsidian notes bridge | `/studynotes` ✅ |
| Context / 500-line scanner | `/context` ✅ |
| RAG knowledge query | `/search` ✅ |
| Discovery → ROI → proposal | `/monetize` + `/dtransform` ✅ |
| CV / cover letter tailoring | `/cv-tailor` ✅ |
| Skool community posting | `/skool-post` ✅ |
| AIS classroom knowledge router | `/ais` ✅ |
| Master prompt / shared brain | `/master_prompt` ✅ |
| Deploy / GitHub / scheduling | `/deploy` ✅ |
| Capstone / handoff outputs | `/capstone` + `/handoff` ✅ |
| 1-on-1 setup hours sale | `/setup_hours` ✅ scaffold (codify pending · see §5) |
| Full AI OS for client | `/os_builder` ✅ scaffold (locked until Level 3 · see §5) |

**Net new skills to potentially build (gaps confirmed):**
- `/plumber_full_stack`, Luca-architecture template (DEV), surfaced in §5
- `/lead_qualifier_app`, frontend on top of `/scrape` (Claude Code Phase 4 Module 1.4), surfaced in §5
- `/voice-agent`, planned, waiting on ElevenLabs + Cal.com (skip per paid-tool rule)
- `/email-agent`, Gmail triage + KB-matched replies (from Workflow 1 in ais_workflows.md), not yet built
- `/kb-indexer`, knowledge base indexer (Workflow 2 in ais_workflows.md), partly covered by `/search` but no dedicated ingestion skill

Everything else from the audit maps to an existing skill, focus is enhancement (per Enhancement Philosophy: error handling → output quality → UX), not rebuilding.
