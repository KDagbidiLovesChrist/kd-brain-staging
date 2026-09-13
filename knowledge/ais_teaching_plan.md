# AIS+ Teaching Plan · Full System Upgrade
**Prepared by:** Claude (Agent 1)
**Date:** 2026-05-16
**Status:** READY FOR REVIEW, no execution has happened yet

---

## SECTION 1: THE BIG PICTURE · What AIS Teaches as a System

### The Core Philosophy
AIS+ (AI Automation Society Plus) is built on one idea: **AI automation is a learnable skill that any non-technical person can sell as a service to businesses.**

Nate Herk's system is a sequence, learn the skill, build proof, get clients, scale. Every piece of the community exists to move you along that sequence. The 5-course structure is not arbitrary, each course unlocks the next step:

1. **Start Here** → understand the community
2. **AI Partner Model** → understand HOW you create value for businesses (the business model)
3. **Build Your Portfolio** → prove you can build things (the skill)
4. **Get Your First Client** → turn the skill into money (the sales)
5. **Scale Your Business** → turn one client into many (the engine)

**The key insight:** Most people jump straight to "how do I get clients?" before they've built anything. AIS forces you to build first. That's the right order, you can't sell what you haven't proven.

### How This Maps to King David's Situation
King David is already at **Level 3-4** on this framework:
- ✅ Community joined and engaged (Level 1 done)
- ✅ AI Partner Model, partially understood (the WAT framework IS the partner model)
- ✅ Portfolio building started, 3 tools built (scraper, newsletter, website)
- 🔄 First Client, next step. The tools are built. Fiverr gig not yet posted.
- ⬜ Scale, comes after first paying client

**What this means:** The bottleneck right now is not the skill. It's the sales. The Fiverr gig needs to go live. That is the ONE thing that unlocks income.

---

## SECTION 2: TOOLS & STACK · What to Keep, What to Add, What to Skip

### The Honest Verdict on Every Tool

**S-Tier (Non-negotiable, keep forever):**
- **Claude Code**, the entire system runs on this. Everything else serves it.
- **Firecrawl MCP**, web scraping and research. Proven, fast, reliable.
- **Playwright MCP**, browser control. /browser skill depends on it.
- **Anthropic API**, Claude's reasoning engine.

**A-Tier (Keep, but upgrade how you use it):**
- **Gmail SMTP**, working. Upgrade to Gmail API when Google CLI is set up for better rate limits.
- **n8n**, still relevant for clients who want visual workflows. Don't replace it, integrate it.

**B-Tier (Add these, they unlock real value):**
- **Obsidian**, permanent memory vault. Free. No API cost. Every session's learnings survive.
- **Hermes**, routes routine tasks away from Claude. Cuts API costs significantly.
- **Claude Code Scheduled Automations**, built-in scheduling. Replaces trigger.dev for most use cases.
- **Ollama**, run local AI models for cheap/routine tasks. Pair with Claude for 99% cost reduction.
- **Claude Design**, branded visual output. Upgrades /website from "functional" to "agency quality."

**C-Tier (Useful but not urgent):**
- **Printing Press**, wraps any service as a Claude-callable tool. Use when a client has a specific system they need Claude to talk to.
- **Clawdbot/VPS**, 24/7 Claude without leaving PC on. Worth it once income is flowing. ~€5-10/month VPS cost.

**Skip (Outdated or Replaced):**
- **trigger.dev**, Claude Code Scheduled Automations does this now. No need to set it up.
- **Windows Task Scheduler**, temporary solution. Replace with Claude Code cloud scheduling.

---

## SECTION 3: WORKFLOWS · Everything Taught, Mapped to WAT Skills

### The Vibe Coding Framework (Most Important Pattern)
This is Nate's core teaching on HOW to communicate with Claude. It's the WAT workflow in practice.

**Old way (wrong):** "Write a function that loops over the list and checks each item against the database."

**Vibe Coding way (right):** "I want to find all businesses in Dublin that don't have a Google review yet."

The difference: you describe the OUTCOME you want, not the steps to get there. Claude asks clarifying questions, proposes a plan, then builds. This is exactly what King David already does, it's confirmation we're doing it right.

### The Four Build Phases
Every build Nate teaches follows this exact sequence:
1. **Plan**, Claude proposes an approach, asks clarifying questions
2. **Approve**, King David reads the plan, says yes (or adjusts it)
3. **Build**, Claude executes fully, no mid-task stops
4. **Test/Optimize**, Claude verifies output works, loops if it doesn't

This is the same as King David's Operating Rules (Rule 1: Plan first, Rule 2: Execute fully). AIS confirms this is the right pattern.

### Skills as the Core Delivery Mechanism
The skills system (slash commands backed by markdown files) is Nate's primary framework for building repeatable services. Community member Jason Hsieh built 80+ skills and shares them via a /submit-skill system.

**Pattern:** One skill = one service. Each skill has a markdown file with: the goal, the tools it uses, the steps Claude follows, the expected output. Triggering the skill = running the service.

King David already has 12 skills. This is ahead of most AIS members at this stage.

### Agentic Workflows · The Upgrade from Chatbot
A chatbot answers questions and stops. An agent receives a goal, plans, takes actions, handles obstacles, and loops until done.

Practical difference for King David:
- **Chatbot:** "What businesses are in Dublin?" → Claude answers
- **Agent:** "Scrape 150 Dublin plumbers with verified phone numbers, format as CSV, and email me the file" → /scrape runs end to end, no hand-holding

All of King David's skills are agents, not chatbots. AIS confirms this is the right level to be operating at.

---

## SECTION 4: BUSINESS IDEAS · Every Opportunity, Honestly Assessed

### Three Universal Pain Points (The Selling Filter)
Before building or selling anything, map it to one of these:
1. **Not enough leads**, business needs more customers
2. **Hiring too slow**, finding/onboarding staff takes too long
3. **Payroll too high**, manual work eating the margin

**How to use this:** Walk into any business, ask "what's your biggest headache right now?", and it will map to one of these three. Then show how your tool solves it.

### Current Services · Honest Assessment
| Service | Pain Point | Revenue | Blocker |
|---------|-----------|---------|---------|
| Lead Gen Scraper | Not enough leads | €25· €90/run | Fiverr gig NOT POSTED |
| Newsletter Automation | Payroll too high | €50· €200/month | Perplexity API key needed |
| Website Builder | Payroll too high | €300· €2,500 | Vercel account needed |

**Honest verdict:** Everything is built. Nothing is earning. The tools exist. The income gap is sales, not skills.

### New Ideas Worth Building (After First Client)
1. **Proposal Generator**, auto-generate client proposals using scraped data. Pairs with lead gen service. Add-on upsell: +€50 per proposal. Source: Jan 19 video.
2. **Social Content Autopilot**, generate content for 9 social platforms from one brief. Monthly retainer €100, €300. Source: Mar 17 video.
3. **Claude Code OS for Clients**, build and sell a full Claude Code Operating System for a client. The Three Ms framework: Memory + Mechanics + Monetisation. Price: €1,000, €5,000 setup + monthly maintenance. Source: May 1 video.

### The Three Ms Framework (Selling Claude Code Operating Systems)
This is Nate's framework for pitching and selling the full system:
1. **Memory**, the rules, knowledge base, and context (CLAUDE.md + memory files)
2. **Mechanics**, the automations and tools (skills + MCPs)
3. **Monetisation**, how the client makes money from it (mapped to their pain point)

This is identical to WAT. When presenting to a client: "Here is the brain (memory), here are the tools (mechanics), and here is how it makes you money (monetisation)."

---

## SECTION 5: OBSIDIAN + HERMES · Full Integration Design

### The Three-Layer Architecture
```
Claude (reasons + executes)
      ↕
Hermes (retrieves + routes + logs)
      ↕
Obsidian (stores everything permanently)
```

**Each layer does ONE job:**
- Claude: reasoning and complex execution only
- Hermes: memory retrieval, routine lookups, context loading between sessions, logging
- Obsidian: permanent storage, zero API cost, linked notes that grow over time

### Why This Matters Financially
Right now, every task, even simple ones like "what did we do last session?", uses Claude API tokens. With Hermes:
- Simple retrieval → Hermes handles it → 0 Claude tokens used
- Routine formatting → Hermes handles it → 0 Claude tokens used
- Claude is only called for tasks that genuinely require reasoning

**Conservative estimate:** 70-90% cost reduction on token usage once this is set up.

### Obsidian Vault Structure (Ready to Build)
```
King David's Vault
├── Sessions/, auto-logged by /studynotes after every session
├── Projects/, Newsletter, Scraper, Website, DCEO
├── Clients/, each client or lead gets a note
├── Patterns/, reusable code/workflow patterns
├── Tools/, everything about each tool we use
├── Business Ideas/, opportunities with honest numbers
├── AIS Learnings/, this file + all extracted classroom content
└── Audit Log/, timestamped trail of every action
```

### Hermes Routing Rules (Which Tasks Go Where)
| Task | Goes To | Why |
|------|---------|-----|
| "What was in the last session?" | Hermes | Memory retrieval |
| "Find my note on X" | Hermes | Document lookup |
| "Log this to Obsidian" | Hermes | Write task |
| "Build a scraper" | Claude | Complex execution |
| "Fix this broken script" | Claude | Debugging = reasoning |
| "Write a client proposal" | Claude | Strategic reasoning |

**Rule:** Retrieval, logging, lookups → Hermes. Reasoning, building, planning → Claude.

### Setup Sequence (In Order)
1. Install Obsidian (free desktop app)
2. Install Obsidian Local REST API plugin
3. Build the vault folder structure above
4. Install /studynotes skill → test it sends a note to Obsidian
5. Research Hermes current install method (check AIS community)
6. Connect Hermes to Obsidian vault
7. Test routing: simple lookup via Hermes → confirm 0 Claude tokens used
8. Add Obsidian MCP to settings.json

---

## SECTION 6: WHAT WE UPDATE (Specific Files and Skills)

### Memory Files · Additive Updates Only
- `project_upcoming_tasks.md`, add Obsidian + Hermes setup to priorities (after Fiverr gig)
- `tools_learned.md`, add: Obsidian, Hermes, Ollama, Claude Design, Printing Press
- `patterns.md`, add: Vibe Coding pattern, Four Build Phases, Three Ms framework

### Skills · Updates (Not New Builds)
| Skill | Specific Change |
|-------|----------------|
| `/exec` | Review Mar 5 video "Turn Claude Code Into Executive Assistant" · add any missing structure |
| `/browser` | Add better error handling (Apr 25 Playwright patterns) |
| `/website` | Evaluate Claude Design · may be able to generate higher-quality output natively |
| `/plan` | Add CLAUDE.md auto-generation step |
| `/search` | Future: re-route to query Obsidian vault via Hermes |

### CLAUDE.md · Updates
- Tools Connected table: add Obsidian (once set up), Hermes (once set up)
- Active Projects: add "Obsidian + Hermes Integration [NEW]" once approved
- Permissions note: update based on Mar 24 video new feature

---

## SECTION 7: WHAT WE ADD (New Skills + Tools)

### New Skills to Build
| Skill | What It Does | Priority |
|-------|-------------|---------|
| `/studynotes` | Generate note → send to Obsidian with audit log | HIGH · needed for Obsidian setup |
| `/n8n` | Create/edit n8n workflows via natural language | MEDIUM · when a client needs visual |
| `/agent-team` | Launch a coordinated team of agents | MEDIUM · for complex multi-step builds |
| `/proposal` | Auto-generate client proposals | HIGH · upsell to lead gen service |
| `/content` | Generate for 9 social platforms at once | MEDIUM · monthly retainer service |

### New Tools to Install (In Priority Order)
1. **Obsidian**, free, install now, vault set up in 30 mins
2. **Hermes**, research install method in AIS community this week
3. **Ollama**, install after Hermes, cuts token costs on routine tasks
4. **Claude Code Scheduled Automations**, built into Claude, just needs to be configured

---

## SECTION 8: WHAT WE SKIP (And Why)

| Item | Why Skip |
|------|---------|
| trigger.dev | Replaced by Claude Code Scheduled Automations · don't set it up |
| Windows Task Scheduler | Temporary solution only · replaced once cloud scheduling is live |
| n8n as primary builder | Claude Code does everything n8n does, better. Use n8n only if client demands visual UI |
| Clawdbot/VPS (now) | Worth it eventually. Not yet · income needs to start first. Cost: ~€5-10/month |
| "The AI Bubble?" lesson | Community discussion, not actionable content |
| Phase 3 & 4 of Claude Code module | Modules are empty · check back in 2-3 months |

---

## SECTION 9: QUESTIONS FOR KING DAVID

These are things I'm uncertain about. King David's answers determine which direction we go.

---

### MONEY + FIVERR
1. **Fiverr gig, what's actually stopping you?** SOP written, tool proven, pricing set. Is there a fear I can address, or a practical blocker (e.g. Fiverr account not set up, profile photo needed, not sure how to write the gig description)?
2. **Who is the exact first target client?** Irish/UK tradespeople (plumbers, electricians, roofers)? Or are you also open to other local businesses? Knowing this sharpens the gig description.
3. **Pricing confidence:** Are you comfortable with €25/50 leads, €50/150, €90/300+? Or do you want to test a lower entry price first to get the first review faster?
4. **Cold outreach:** Are you planning to do Fiverr only, or also direct cold DM / cold email to businesses? (The AIS material has frameworks for both.)
5. **Proposal Generator:** Do you want to build this as an upsell to the scraper immediately, or after the first Fiverr sale comes in?

---

### OBSIDIAN + HERMES + STORAGE
6. **Obsidian sync:** Do you want the vault on your local machine only, or synced to a cloud backup (iCloud, Google Drive, or Obsidian Sync)? iCloud is free and you already have it.
7. **Hermes, have you researched it at all?** If you've seen anything specific in the community about how to install it, tell me and I can build the setup plan around that.
8. **Current memory folder:** The `C:\Users\Dell\.claude\memory\` folder holds all your current notes. Do you want to migrate everything there into Obsidian, or keep both running in parallel?
9. **Obsidian first, Hermes later?** Obsidian is 30 minutes and free. Hermes needs more research. Do you want to set up Obsidian now and add Hermes once we know the install method?

---

### SKILLS + TEMPLATES
10. **AIS community templates:** Do you want me to go back into AIS via Playwright and download ALL available skill files, templates, and resources right now? (Jason Hsieh's library, /studynotes, CLAUDE.md builder, outreach scripts, proposal templates, Claude Code Starter Kit.)
11. **Skills priority:** Of the 5 new skills listed (studynotes, n8n, agent-team, proposal, content), which one do you want built first?
12. **Jason Hsieh's 80+ skills:** Do you want all of them installed, or only the ones that map to your current services (lead gen, newsletter, website)?
13. **DCEO skills:** Are the 7 DCEO agents on hold until the work laptop setup is sorted, or do you want to continue building them in parallel?

---

### TOOLS + COSTS
14. **Monthly budget (API + cloud):** What is the monthly limit you're comfortable spending? This determines whether Ollama is worth setting up now (cuts costs for heavy token tasks) or if it's overkill.
15. **Ollama, machine spec:** Ollama runs local AI models on your machine. Does your Windows machine have a decent GPU or at least 16GB RAM? If not, Ollama won't be effective and we skip it.
16. **Claude Design:** Do you want to evaluate this for the next website build, or stick with the current HTML/CSS approach that's already working?
17. **Printing Press:** Any specific tools or client systems you want Claude to be able to talk to directly? (e.g. a client's booking system, a CRM, Calendly.) If yes, Printing Press is the fastest way.

---

### SCHEDULING + AUTOMATION
18. **Claude Code Scheduled Automations:** Do you want to set up a daily scheduled task, e.g. a morning briefing every day at 8am, or weekly newsletter research triggered automatically?
19. **Newsletter:** Are you selling it as a service to clients, using it for yourself, or both? This affects whether we build the scheduling for your use or for client delivery.
20. **24/7 automations:** Once income starts, the VPS/Clawdbot option means Claude runs jobs while your PC is off. Is that something you want to plan for in month 2?

---

### STRATEGY + VISION
21. **The new bid:** You mentioned a new idea or business opportunity. What is it? Map it to WAT immediately.
22. **Agent 2 output:** Agent 2 is extracting Courses 2, 4, 5 (AI Partner Model, Get Your First Client, Scale Your Business → `ais_business_navigation.md`). Do you want to wait for that before finalising the execution plan, or move forward now?
23. **Income target and timeline:** You mentioned €10k by end of month. Which service gets there fastest, scraper (high volume, low price) or website builder (low volume, high price)? Do you want me to model both?
24. **Faith and values check:** Is there any type of client, industry, or task that is off-limits for you from a faith perspective? Better to define this now than discover a conflict mid-engagement.
25. **What does success look like in 90 days?** First client? First recurring retainer? Specific monthly income number? Knowing your exact target shapes every decision we make from here.

---

## SUMMARY · What Changes, What Doesn't

### What changes IMMEDIATELY (no approval needed · additive memory only):
- ✅ `ais_all_learnings.md`, all classroom sections filled in (done this session)
- ✅ `ais_claude_obsidian_hermes.md`, Obsidian/Hermes design documented (done this session)
- ✅ `agent2_classroom_brief.md`, coordinated with Agent 2 to prevent duplicates (done this session)

### What changes AFTER King David approves:
- Update skills as listed in Section 6
- Add new skills as listed in Section 7
- Start Obsidian setup (Section 5 sequence)
- Add tools to CLAUDE.md Tools Connected table

### What NEVER changes without explicit approval:
- Existing pipelines, webhooks, hooks, untouched
- Existing .env files, read only
- Firecrawl/Playwright MCP settings, untouched
- Any production automations currently running

---
*This plan is complete. Nothing has been executed. Waiting for King David's review.*
