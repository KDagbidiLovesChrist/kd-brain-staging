# Cluster C+D · TrueHorizon $211k + Build Your AI OS
*Phase 4 absorption, generated 2026-05-23 from full read of 4 transcripts + ais_all_learnings cross-refs.*

---

## 1. TRUEHORIZON $211K DEAL · THE ANATOMY

### The Client
- Small-to-midsize US insurance company (~50-100M annual revenue est.)
- Pain: manual underwriting, policy endorsements, customer-facing chatbot gaps, internal process inefficiency
- Highly regulated industry, data privacy, audit trails, compliance logging required

### Discovery / Scoping (Part 1)
- **Sales cycle:** 9 weeks total (March 18, May 12, 2025)
- **Inbound lead:** prospect emailed Nate with multiple AI agent ideas already mapped
- **Initial discovery call (March 18):**
  - First 28 min: prospect demoed platform; Millen + Nate showed real-time AI solutions for each manual step
  - Next 15 min: brainstormed additional agents beyond initial two
  - Final 15 min: pricing & IP ownership
  - **HIGHEST buying signals:** prospect came with pre-built ROI assessment + bullish-on-AI stance
- **NDA + tech-partner loop (Mar 20, Apr 1):** prospect required existing full-stack tech partner for API access + front-end
- **Proving ROI call (April 1):** deep dive on API docs, wireframes, demonstrated actual ROI (7-8 min manual → 30 sec automated)
- **Negotiation (Apr 1, May 12):**
  - Client expressed timeline urgency → Millen/Nate presented "enterprise option" (vs initial hourly dev model)
  - Omnichannel: email → phone → SMS
  - Competitor intel: bigger firms also pitching → signaled higher budget available
  - **Final deal: 12k/month base + agent deployment fees increasing MRR**

### Project Management (Part 2)
- **5-phase delivery:** Kickoff → Architecture & Roadmapping → Development → Delivery & Handoff → Deployment
- **ClickUp board (6 categories):** Inbox · Product Backlog · Current Priorities · In Progress · Review · Done
- Integrated with client portal for transparency
- **Loom video documentation required on all completed tasks**
- **Sprint cadence:** 1-2 week sprints with review cycles; capacity planning baked in
- **Scope:** 2 reviewer agents (7-8 min → 30 sec automation) + 1 processor agent (internal reporting) + 1 chatbot (NLP-to-SQL, replicated DB for isolation)
- **Testing:** automated batch QA using LLM-as-judge for output validation pre-prod

### Modern Sales Pipeline (Part 3)
- **Discovery opening:** *"How bullish are you on AI?"*, highest buying signal when prospect has competitive pressure + ideas ready
- **BAT framework:** Budget · Authority · Timeline qualification
- **Post-discovery automation:** Fireflies API converts call transcript → proposal template; 24-hr + 1-hr SMS/email reminder for show rates
- **Proving value:** tangible front-end demos > n8n workflows; ROI sourced from client's own data, not industry averages
- **Closing philosophy:** "no closing call" if discovery framework followed, prospect signs after ROI demo proves fit
- **Contract & payment:** PandaDoc + QuickBooks; manual Milan review before send
- **Onboarding:** kickoff call establishes sprint cadence; early PoC demos for fast feedback

### Exact Pricing Breakdown
| Component | Cost |
|---|---|
| Base monthly (dev + maintenance) | $12,000 / month |
| Reviewer agent #1 deployment | +$2,000 / month MRR |
| Reviewer agent #2 deployment | +$2,000 / month MRR |
| Chatbot agent deployment | +$2,500 / month MRR |
| Processor agent deployment | +$1,000 / month MRR |
| **Total 8-month contract** | **~$211k** |

Ramp: months 1-2 = 12k · months 3-4 = 16k · month 5 = 18.5k · month 6+ = 19.5k
- **Model:** NOT hourly dev rates (replaced early); agent-by-agent value deployment
- **Enterprise tier vs Business tier:** premium = top-tier PM + 2 engineers + solutions architect

### Tools Used End-to-End
- **Workflow builder:** n8n (primary, enterprise license, reviewed every 8 weeks vs Make/Zapier/Relevance)
- **PM:** ClickUp (client portal, 6-category board, API)
- **Document processing:** Datadog (monitoring), Snowflake (historical infra)
- **API layer:** AWS (deployment, CloudWatch, ECS on Fargate auto-scaling, DPA/SLA compliance)
- **Database:** PostgreSQL on AWS RDS (replicated for chatbot data isolation)
- **AI models:** OpenAI (LLM evals), AWS Bedrock (local models for HIPAA-adjacent compliance)
- **Vector DB:** tested but chose NLP-to-SQL for latency
- **Code pipeline:** proprietary n8n CI/CD (built in-house; dev/test/prod safe)
- **Video docs:** Loom
- **Transcription:** Fireflies API
- **Contracts:** PandaDoc
- **Payments:** QuickBooks

### Replicable Pattern · Dublin Plumber at €500-2,000 ticket
1. Find plumber with phone booking pain (missed calls, callbacks, scheduling chaos)
2. Proposal: voice agent answers, qualifies, books calendar, texts confirmations → quantified ROI
3. Discovery: show €X/month saved (e.g., 3 missed calls × €150 = €450/mo)
4. Scoping: 1-2 agents, 6-week deployment
5. Pricing: €1,500-3,000 setup + €200-500/month retainer
6. Pitch: *"You'll pay for this in 3-4 months from recovered lost jobs alone"*

---

## 2. BUILD YOUR AI OS · PRODUCTISED OFFER PLAYBOOK

### Definition (Nate's framing)
- Layer of intelligence on top of OS (files, apps, contacts, workflows)
- AI agent that sees ALL your data and can act on it
- **Four Cs:** Context (what AI knows) → Connections (what it reaches) → Capabilities (what it produces) → Cadence (when it acts autonomously)
- Replaces "work about work" (searching, context-switching, forgetting)
- **Stay tool-agnostic**, the durable layer underneath matters more than n8n vs Claude Code vs Codex

### 9-Lesson Curriculum
1. **What Is an AI OS?**, framework, why it beats manual tabs
2. **Three Ms Framework**, Mindset · Method · Machine
3. **Four Cs Framework**, + seven tier-1 buckets (Revenue · Customer · Calendar · Comms · Tasks · Meetings · Knowledge)
4. **Onboarding**, VS Code + Claude Code extension, clone template, /onboard skill (7-question interview)
5. **Connecting Your Tools**, APIs > MCPs (token efficiency), dedicated AI accounts (scoped perms), .env for secrets, ClickUp + Google Workspace CLI walkthrough
6. **Building Capabilities With Skills**, reusable markdown recipes, progressive context loading, 6-step framework, /skill-builder
7. **Routines, Schedules & Loops**, local scheduled tasks vs cloud routines (24/7 off-laptop) vs /loop (short bursts)
8. **Knowledge Wikis, Dashboards & Daily Use**, Karpathy's LLM Wiki pattern (raw/ → wiki/ with backlinks), Obsidian frontend, Claude Artifacts for fast dashboards
9. **Congrats! Your Next Step**, share build in community (#AISOS hashtag)

### Setup vs Retainer Deliverables
| Setup (one-time €1k-5k) | Retainer (€100-500/mo) |
|---|---|
| Folder structure + CLAUDE.md master prompt | Monthly health check + audit score |
| /onboard 7-question interview output | New connections as business evolves |
| Connect first 2-3 tools (ClickUp + Google Workspace min) | Skill scaling: ad-hoc → reusable → scheduled |
| Build 1-2 first skills (/daily-briefing, /weekly-review) | Knowledge tending: new docs into wiki, backlinks |
| Local scheduled tasks or first cloud routine | Troubleshooting: broken routines, SDK updates |
| Knowledge wiki raw/ folder scaffolding | Quarterly recalibration |
| 2-4 hr training on Four Cs + how to extend | |

### Pricing Tiers
- **Entry:** €1,000, €2,500 setup (smaller biz, simpler stack)
- **Mid-market:** €3,000, €5,000 setup (multi-tool, custom skills)
- **Retainer:** €100, €500 / month by size + complexity
- **Hybrid:** "setup + 3-month retainer" bundle for commitment
- **Upsell:** after month 3, offer annual retainer at 10-month discount

### Positioning
- **One-off:** "Build me a bot" → reactive, scope creep, client forgets how to use
- **AI OS:** "Let's build your intelligence layer that scales as you grow" → proactive, documented, client owns it
- **Sales:** *"This is not a project. This is your new operating system. We're teaching you how to run your business 50% faster."*

### Exact Onboarding Sequence (8 weeks)
1. **Intake call (30 min):** situational briefing, budget alignment, 4 Cs diagnostic
2. **Assignment (async):** /onboard interview, writing samples, 90-day priorities, business description
3. **Kickoff workshop (Day 1-2, 2-4 hours):** walk through structure + CLAUDE.md in client's own Claude Code instance, refine docs, map 7 tier-1 buckets together
4. **Connection (Weeks 1-2):** first API (ClickUp or Google), reference doc, "ask my AI" test
5. **Skills (Weeks 2-3):** /skill-builder → 2-3 foundational skills, iterate on feedback
6. **Cadence (Weeks 3-4):** daily/weekly schedule, first cloud routine, test morning briefing / weekly report
7. **Knowledge (Week 4):** create raw/ folder, ingest first docs, run /ingest → wiki + backlinks
8. **Handoff (Week 4-5):** video walkthrough, client runs full use-case, troubleshooting call, doc custom tweaks

---

## 3. TOOLS / APIs / FRAMEWORKS · MINI INSTALL PASS CANDIDATES

| Name | Purpose | Free/Paid | When Needed |
|---|---|---|---|
| n8n | Workflow builder, 1,650+ nodes, 2,352+ templates | Free / €999+ enterprise | All client agent work |
| Claude Code | AI coding agent in VS Code | $17-20/mo Claude sub | Build AI OS, skills, automation |
| ClickUp | PM, API, client portals | Free / $5-19/mo | Client delivery tracking |
| Google Workspace CLI | Auth into Drive/Sheets/Docs/Gmail/Cal/Slides | Free / OSS | Any Google Workspace client |
| Fireflies AI | Meeting transcription, proposal API | Free / $100+ pro | Auto-generate proposals from calls |
| AWS | Hosting, Bedrock, RDS, ECS, CloudWatch, S3 | Pay-per-use | Scaling agents, compliance |
| OpenAI | LLM inference (GPT-4, Embeddings) | $0.01-0.03 / 1K tokens | Model evals, voice agents |
| AWS Bedrock | Local model hosting, HIPAA-adjacent | Pay-per-use | Privacy-critical clients |
| PandaDoc | Contracts, proposals, e-sign | $29-149/mo | Close deals remotely |
| Datadog | Observability, monitoring, alerting | $15+/mo per host | Monitor production agents |
| Postgres on AWS RDS | Relational DB, replication | $15-100+/mo | Client data, chatbot KB |
| Loom | Video documentation, async recording | Free / $10/mo | Task walkthrough docs |
| Obsidian | Knowledge wiki front-end | Free / $4/mo Sync | Browse knowledge graph |
| Karpathy LLM Wiki pattern | Self-organising knowledge in MD + backlinks | Free (pattern only) | Ingest raw docs → wiki |
| Stripe / QuickBooks | Payments, accounting | 2.2% + $0.30 | Recurring billing, invoicing |
| Brave Search MCP | Web search in Claude | Free MCP + API key | Real-time research |
| Firecrawl MCP | Scrape websites, structured extract | Free MCP + API key | Lead gen, competitor research |
| Playwright MCP | Browser control | Free MCP | Browser automation |
| GitHub | VC, cloud routine triggers | Free / $4-12/mo Pro | Store AI OS repo, deploy routines |
| Perplexity API | Web research w/ citations | Free / $20/mo | Deep research on any topic |
| n8n-mcp | 1,650 n8n nodes in Claude Code | Free MCP | Query n8n templates without leaving Claude |

---

## 4. DIRECT QUOTES WORTH KEEPING

1. **"If the prospect comes to the call with a bunch of ideas for automations, hands down, it's the highest buying signal we've seen."**, Millen (TrueHorizon Part 1), *Use for ICP targeting*

2. **"We're not easy money. This requires handling pre-sales, engineering, data compliance, security concerns, and complex integrations. It's a generational opportunity with a continuous skills gap."**, Millen (Part 3), *Reframe AI services as expertise, not commodity*

3. **"The default is now stubborn. If anything sounds boring or repetitive, I'm not doing it. The AI OS is."**, Nate (AI OS Lesson 2), *Mindset pitch, the paradigm shift you're buying*

4. **"You can't have cadence without connections. You can't have capabilities without context. Go 1, 2, 3, 4 in order."**, Nate (AI OS Lesson 3), *Why rushing automation without setup fails*

5. **"Most business processes don't need a fully autonomous AI agent. They need a deterministic workflow with maybe one AI step inside it."**, Nate (AI OS Lesson 8), *Manage expectations; simplicity wins*

---

## 5. UPGRADES TO KING DAVID'S EXISTING SKILLS

### vs `/monetize`
- Add BAT framework (Budget · Authority · Timeline) explicitly
- 9-week sales cycle for enterprise is NORMAL, don't see long cycles as red flags
- Use SMS/phone when email stalls

### vs `/dtransform`
- Insert "proving ROI" call BEFORE proposal (wireframes + live API docs + efficiency numbers)
- Assessment alone isn't enough, demo the solution works
- Quote by agent deployed or value captured, NOT by hours consumed

### vs `/os_builder`
- Follow the 8-week onboarding sequence
- Key shift: you're not building their OS FOR them; you're TEACHING them to build it + coaching gaps
- Pricing reflects this: €1k-5k setup + €100-500/mo retainer for check-ins + new wiring (not ongoing dev work)

### Dublin Plumber (your niche)
- Lead with urgency ROI: *"You're losing 3-5 jobs per week to missed calls. At €200/job that's €600-1k/week. This pays for itself in 2 weeks."*
- Close in 1-2 calls at this price point, don't wait for 9 weeks

### General
- **NEVER quote dev hours again.** Quote outcomes or retainers.
- **Agent-by-agent pricing** (MRR grows per deployment) keeps client invested + you profitable from day 1
- **Tool-agnostic framework** is how you avoid tech betting (same setup works in n8n, Claude Code, Make, etc.)
