# AIS+ · Claude, Obsidian & Hermes Development Notes
**Source:** AI Automation Society Plus (Skool)
**Date extracted:** 2026-05-16
**Purpose:** Everything from AIS+ specifically relevant to upgrading Claude, setting up Obsidian vault, and integrating Hermes. Development-focused. Used to build the upgrade plan.

---

## CLAUDE CODE UPGRADES · KEY VIDEOS TO STUDY

These are the videos from the database most directly relevant to upgrading Claude, skills, memory, and system architecture. Starred = highest priority.

| Date | Title | Why It Matters |
|------|-------|---------------|
| Jan 14, 2026 | Claude Code is Better at n8n than I am ⭐ | Claude Code replacing n8n · confirms our direction |
| Jan 21, 2026 | Master 95% of Claude Code in 36 Mins ⭐ | Complete beginner guide · check for anything we missed |
| Jan 25, 2026 | Agentic Workflows Just Changed AI Automation Forever ⭐ | Core agentic workflow patterns to adopt |
| Jan 27, 2026 | Set Up Clawdbot on a VPS in Minutes ⭐ | Clawdbot = Claude running on VPS 24/7 · key for deployment |
| Jan 28, 2026 | 100 Hours Testing Clawdbot vs Claude Code ⭐ | Honest verdict: when to use VPS vs local Claude Code |
| Feb 7, 2026 | How I'd Teach a 10 Year Old to Build Agentic Workflows ⭐ | Plain-English explanation of agentic patterns |
| Feb 20, 2026 | The EASIEST Way to Host Your Claude Code Agents ⭐ | Hosting/deployment options for Claude agents |
| Feb 27, 2026 | Master 95% of Claude Code Skills in 28 Minutes ⭐ | Skills system deep dive · update our /skills |
| Mar 5, 2026 | Turn Claude Code Into Your Executive Assistant in 27 Mins ⭐ | Upgrade /exec skill · direct relevant |
| **Mar 12, 2026** | **Build & Sell with Claude Code (10+ Hour Course) ⭐⭐** | **THE MAIN COURSE · full system build + sell methodology** |
| Mar 23, 2026 | How to Build Claude Agent Teams Better Than 99% of People ⭐ | Agent team design patterns · upgrade multi-agent setup |
| Mar 24, 2026 | Claude Code Just Dropped Memory 2.0 ⭐ | Memory system upgrade · directly relevant to our memory/ folder |
| Mar 24, 2026 | STOP Using Bypass Permissions, Use This New Feature Instead ⭐ | Update how we handle permissions in settings.json |
| Apr 2, 2026 | 18 Claude Code Token Hacks in 18 Minutes ⭐ | 18 ways to cut token costs · apply to our system |
| **Apr 4, 2026** | **Ollama + Claude Code = 99% CHEAPER ⭐⭐** | **Ollama = local model runner, cuts API costs by 99% for routine tasks** |
| Apr 8, 2026 | I Tested Claude's New Managed Agents ⭐ | Managed Agents feature · understand before adopting |
| **Apr 14, 2026** | **Claude Code Finally Gave Us Scheduled Automations ⭐⭐** | **Scheduled automations = replaces trigger.dev need · study this** |
| Apr 20, 2026 | How to Manage Your Claude Limits Better Than 99% of People ⭐ | Session limit management · practical for daily use |
| Apr 25, 2026 | Claude Code + Playwright Automates Literally Anything ⭐ | Playwright patterns · upgrade /browser skill |
| Apr 27, 2026 | 32 Claude Code Hacks in 16 Mins ⭐ | 32 hacks · scan for anything not in our system |
| **May 1, 2026** | **Build & Sell Claude Code Operating Systems ⭐⭐** | **"Three Ms framework" for building+selling OS · maps to WAT** |
| May 3, 2026 | I Tried 100+ Claude Code Skills. These 6 Are The Best ⭐ | The 6 skills businesses PAY for · prioritise these |
| May 8, 2026 | Overwhelmed By AI? Just Copy My Tech Stack ⭐ | Nate's S/A/B/C tier stack · map against ours |
| May 12, 2026 | Multi-Agent Building In Claude Code Somehow Got Easier ⭐ | New agent view · upgrade multi-agent workflow |
| May 12, 2026 | Every Level of Claude Explained in 21 Minutes ⭐ | 5 levels of Claude · know which level we're at |
| May 15, 2026 | I Tested 3 Ways to Deploy Claude Agents ⭐ | 3 deployment options · choose the right one for King David |

### KEY DISCOVERIES FROM VIDEO DATABASE

**Clawdbot**, Claude running on a VPS 24/7 (not just local). This is the "always-on" version of Claude Code. Jan 27 + Jan 28 videos explain setup and honest comparison.

**Ollama**, Run local AI models (like Llama) on your own machine. When paired with Claude Code, it handles cheap/routine tasks while Claude handles reasoning. Result: 99% cost reduction on token-heavy tasks.

**Claude Code Scheduled Automations** (Apr 14), Built-in scheduling in Claude Code itself. May replace the need for trigger.dev entirely.

**Claude Code Operating Systems** (May 1), "Three Ms framework" = a structured way to build and sell Claude-based systems. Very aligned with our WAT framework.

**The 6 Skills Businesses Pay For** (May 3), Critical for monetisation. Study before updating Fiverr gig.

### Patterns to adopt:
- **Vibe Coding:** Always describe the outcome, never the steps. Claude proposes plan → approve → build → test.
- **Four Build Phases:** Plan → Approve → Build → Test/Optimize, enforce this in every skill.
- **Enhancement before addition:** Before building anything new, run the 3-question check: error handling, output quality, user experience. 
- **Pain-point framing:** Lead every sales interaction with one of the three universal pain points: leads, hiring, payroll.
- **Portfolio = proof, not showreel:** Every build must have live demo + problem statement + real numbers.

### Skills to update:
| Skill | What to Change |
|-------|---------------|
| `/exec` | Mar 5 video: "Turn Claude Code Into Executive Assistant" · review for structure upgrades |
| `/browser` | Apr 25 video: Playwright patterns · error handling improvements |
| `/website` | Evaluate Claude Design integration · may upgrade output quality significantly |
| `/plan` | Add CLAUDE.md builder pattern from community · auto-generate project CLAUDE.md |
| `/search` | Route to Obsidian vault via Hermes once Obsidian + Hermes are set up |

### Skills to add:
| Skill | Source | What It Does |
|-------|--------|-------------|
| `/studynotes` | Community member pattern | Generate structured note → send to Obsidian with audit log |
| `/n8n` | Module 4 Phase 1 Lesson 1.4 | Create/edit n8n workflows via natural language |
| `/agent-team` | Mar 23 video | Build and launch multi-agent teams from one command |
| `/proposal` | Jan 19 video | Auto-generate client proposals using scraped data |
| `/content` | Mar 17 video | Generate content for 9 social platforms on autopilot |

---

## OBSIDIAN VAULT · DESIGN
*(Based on /studynotes community pattern + community posts)*

### Folder structure:
```
Obsidian Vault (King David's Brain)
├── Sessions/           ← every Claude session → auto-note via /studynotes
├── Projects/           ← one note per project (Newsletter, Scraper, Website, DCEO)
├── Clients/            ← one note per client or lead
├── Patterns/           ← reusable code patterns and workflow templates
├── Tools/              ← notes on every tool (Firecrawl, Playwright, n8n, etc.)
├── Business Ideas/     ← income opportunities, assessed with real numbers
├── AIS Learnings/      ← everything from AIS classroom and YouTube
└── Audit Log/          ← auto-generated by /studynotes, every session logged
```

### Links and connections:
- Every note links to related notes using `[[Note Name]]` syntax
- /studynotes skill auto-links new notes to existing ones by topic
- Clients link to → Projects link to → Patterns (tools used)
- AIS Learnings link to → Projects (where each lesson is applied)
- Sessions link to → Audit Log (timestamped trail of all activity)

### How Obsidian gets populated (the flow):
1. Claude generates content (note, learning, pattern, client update)
2. /studynotes skill formats it and sends via Obsidian Local REST API
3. Note lands in the correct folder with links auto-generated
4. Audit log entry created automatically

---

## HERMES INTEGRATION
*(Based on community posts, Hermes discussion thread)*

### What Hermes Is
Hermes is a persistent AI agent that runs alongside Claude. Think of it as the "memory keeper", it handles all the retrieval and routine lookups so Claude can focus purely on reasoning. It's not a plugin; it runs as its own process.

King David's framing: **Claude = the brain. Hermes = the tank (support/memory). Obsidian = the vault.**

### Setup steps (to research · not confirmed yet):
1. Install Hermes (exact installer TBD, check community for current method)
2. Connect Hermes to Obsidian vault via Local REST API
3. Set routing rules: which request types go to Hermes vs Claude
4. Test: ask Hermes to retrieve a session note from Obsidian → verify it comes back correctly
5. Integrate into CLAUDE.md: add Hermes as a tool in the Tools Connected table

**Note:** Before setting up, confirm with community which router to use, OpenRouter (cheaper, routes to best available model) or a specific model. Community leans toward OpenRouter for routine tasks.

### Which tasks route to Hermes vs Claude:
| Task Type | Route To | Why |
|-----------|---------|-----|
| "What was in the last session?" | Hermes | Memory retrieval · no reasoning needed |
| "Find my note on Firecrawl patterns" | Hermes | Document lookup · Obsidian query |
| "What's the status of Project X?" | Hermes | Context loading · read and return |
| "Build me a scraper for plumbers" | Claude | Complex reasoning + tool execution |
| "Fix this broken script" | Claude | Debugging = reasoning |
| "Write a proposal for this client" | Claude | Strategic reasoning + generation |
| "Log this session to Obsidian" | Hermes | Write task · no reasoning |
| "Summarise today's work" | Claude | Synthesis = reasoning |

**Rule of thumb:** Retrieval, logging, and lookups → Hermes. Reasoning, building, and planning → Claude.

---

## TOOLS & STACK · CLAUDE-RELEVANT

### Confirmed current tools (as of 2026-05):
| Tool | Status | Verdict |
|------|--------|---------|
| Claude Code | Active · core of everything | S-tier · irreplaceable |
| Firecrawl MCP | Active · scraping tool | S-tier · keep |
| Playwright MCP | Active · browser control | S-tier · keep |
| Gmail SMTP | Active · email delivery | A-tier · keep |
| Anthropic API | Active · Claude reasoning | S-tier · keep |
| n8n | Referenced throughout module | B-tier · useful for visual workflows, not replacing Claude Code |
| Windows Task Scheduler | Active · local scheduling | C-tier · replace with Claude Code Scheduled Automations |

### Tools to adopt:
| Tool | Priority | What It Does | Cost |
|------|---------|-------------|------|
| Obsidian | HIGH | Permanent knowledge vault · linked Markdown notes | Free |
| Hermes | HIGH | Persistent agent · routes tasks away from Claude | TBD |
| Ollama | MEDIUM | Run local AI models · 99% cheaper for routine tasks | Free (local) |
| Claude Code Scheduled Automations | HIGH | Built-in scheduling, replaces trigger.dev need | Included in Claude |
| Printing Press | MEDIUM | Wrap any service as Claude-callable tool in 10 min | TBD |
| Claude Design | MEDIUM | Branded HTML/PDF/visual output · upgrades /website | Included in Claude |
| Clawdbot / VPS | LOW (future) | Claude running 24/7 without leaving PC on | VPS cost ~$5-10/mo |

### Tools to skip (outdated or not relevant):
| Tool | Why Skip |
|------|---------|
| trigger.dev | Claude Code Scheduled Automations replaces this need |
| n8n as primary builder | Claude Code handles this better · use n8n only if visual UI is required by client |
| Windows Task Scheduler | Replaced by Claude Code cloud scheduling once that's set up |

---

## BUSINESS IDEAS · RELEVANT TO KING DAVID'S SETUP

### Ideas Confirmed by AIS Content
All mapped to King David's existing services and the three pain points (leads / hiring / payroll):

| Idea | Pain Point | Revenue Model | Effort |
|------|-----------|--------------|--------|
| Lead Gen Scraper (EXISTING) | Not enough leads | €25· €90/run Fiverr | DONE · post the gig |
| Newsletter Automation (EXISTING) | Payroll too high | €50· €200/month retainer | Built · needs keys |
| Website Builder (EXISTING) | Payroll too high | €300· €2,500 per site | Built · needs Vercel |
| Proposal Generator | Payroll too high | Add-on to lead gen or standalone €50· €150/proposal | Build from Jan 19 video |
| Social Content on Autopilot | Payroll too high | €100· €300/month retainer | Build from Mar 17 video |
| Voice Agent (sales/booking) | Hiring too slow | €200· €500 setup + retainer | Medium effort · ElevenLabs + Cal.com |
| Claude Code OS (for clients) | All three | €1,000· €5,000 setup | High effort · Three Ms framework |

### The "Three Ms" Framework for Selling (from May 1 video)
Build + Sell Claude Code Operating Systems using this structure:
1. **Memory**, the knowledge base and rules (CLAUDE.md + memory files)
2. **Mechanics**, the workflows and automations (skills + tools)
3. **Monetisation**, how the client makes money from it (mapped to pain points)

This is identical to the WAT framework. When selling to a client, present their new system as: "Here is your memory (the brain), here are the mechanics (the tools), and here is how you make money from it."

---

## JSON / CONFIG UPDATES NEEDED
*(to execute only after King David approves, no changes without approval)*

### settings.json changes pending:
1. **Permissions update**, Mar 24 video: "STOP Using Bypass Permissions, Use This New Feature Instead." There is a newer, safer way to handle permissions than bypass mode. Review settings.json after watching this video.
2. **Obsidian MCP**, when Obsidian is set up, add the Obsidian Local REST API plugin as an MCP server entry
3. **Hermes routing**, if Hermes uses an API endpoint, add it to settings.json as a tool

### .env files to update:
| File | Keys Needed |
|------|------------|
| `Newsletter Demos\.env` | PERPLEXITY_API_KEY, ANTHROPIC_API_KEY, Gmail App Password |
| Future Obsidian `.env` | OBSIDIAN_API_KEY (from Local REST API plugin) |

### Safety note:
These are config updates, not pipeline changes. They do not touch any existing automation flows. Each one is independent, can be done one at a time, in any order, without risk.
