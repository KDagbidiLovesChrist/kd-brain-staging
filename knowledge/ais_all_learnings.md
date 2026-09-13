# AIS+ All Learnings · Complete Extract
**Source:** AI Automation Society Plus (Skool)
**Date extracted:** 2026-05-16
**Purpose:** Every valuable piece of information from the AIS+ community, tools, workflows, business ideas, mindset, strategies. Nothing filtered out.

---

## MODULE 1: START HERE

### Milestones Along the Way · The Journey Map
The typical path from 0 to first client:

| Milestone | When | What It Looks Like |
|-----------|------|-------------------|
| Level 3 Unlocked | First 1-2 weeks | Post intro, comment on posts, be helpful. 20 likes = Level 3. Unlocks AI Partner Model module. |
| First Build Completed | Weeks 2-4 | Follow Portfolio course tutorial, finish a real working automation. Doesn't need to be perfect. |
| First Client Conversation | Month 2 | Someone says "yes, I'd pay for that." Outreach materials unlock in month 2. |
| First Paying Client | Months 2-3 | Real money in account. Proof the skill is sellable. |
| First Recurring Partnership | Month 4+ | Client retainer, or AI Partner Model kicks in · recurring revenue, compound growth. |

**Two rules:**
1. No timer, move at your own pace
2. Community accelerates everything, 20 likes gets you to Level 3 faster when you're active

### Track Your Progress
- Mark each lesson complete using the checkmark icon
- Module Summary for "Welcome to AIS+": community for driven professionals to master AI automation and grow alongside like-minded builders. Overview of community structure and how to get the most out of membership.

### Your Journey from 0 to First Client · The 5-Course Roadmap
The entire AIS+ curriculum is structured as 5 courses in a deliberate order:

| # | Course | What It Covers | Access |
|---|--------|---------------|--------|
| 1 | Start Here | Onboarding into community | Open now |
| 2 | AI Partner Model | How your skills create value for businesses (core business model) | Level 3 (~30 min of engagement) |
| 3 | Build Your Portfolio | Foundations + Claude Code tutorials to start building | Open now |
| 4 | Get Your First Client | Step-by-step client landing process | Unlocks at 30 days |
| 5 | Scale Your Business | Operations, lead gen, repeatable engine | Unlocks at 90 days |

**Key facts:**
- Path is intentionally numbered, don't jump around
- Level 3 can be hit in ~30 minutes by posting intro + engaging with posts (20 likes needed)
- Premium membership bypasses ALL gating instantly + unlocks $3M savings vault
- Course 2 (AI Partner Model) is the most important locked one, the core business model

---

## MODULE 3: BUILD YOUR PORTFOLIO

### What Businesses Actually Pay For (The Core Lesson)
Three universal pain points. Every business you ever approach has at least one:
1. **Not enough leads**, they need more customers (→ /scrape, outreach automation)
2. **Hiring too slow**, finding and onboarding staff takes too long (→ screening automation, job posting tools)
3. **Payroll too high**, spending money on tasks a tool can do (→ replace manual work with automations)

**How to use this:** Start every sales conversation by identifying which of these three the business has. Then show them exactly how your automation solves it. Don't pitch features, pitch the problem being solved.

### Client-Ready Portfolio
What makes a portfolio that gets clients (not just impressive to builders):
- 3 to 5 builds minimum, enough to show range, not so many it overwhelms
- Each build needs: **live demo + clear problem statement + real numbers**
  - Live demo: something they can see working, not just a screenshot
  - Clear problem statement: "This automates X so you stop doing Y manually"
  - Real numbers: time saved, cost saved, leads generated, concrete
- Portfolio is a proof document, not a showreel, every piece must link back to one of the three pain points

### Enhancement Philosophy (Critical Mindset Shift)
Enhancement ≠ adding more features. Enhancement = making existing work more reliable and professional.

Three areas of enhancement (in order of priority):
1. **Error handling**, what happens when it breaks? Does it fail gracefully, notify the user, and recover?
2. **Output quality**, is the output clean, formatted, consistent, and client-ready?
3. **User experience**, is it easy to trigger, easy to read results, easy to adjust?

**Why this matters for King David:** Every time you upgrade a skill (/scrape, /newsletter, /website), ask these three questions before calling it done. This is what separates freelancer-grade work from agency-grade work.

### Vibe Coding Framework
How to communicate with Claude to build things right:
- Describe the **outcome** you want, not the steps to take
- Example (wrong): "Write a for loop that iterates over the list and checks each item"
- Example (right): "Scan the list of businesses and flag any that don't have a website"
- Claude asks clarifying questions → you approve the plan → Claude builds → Claude tests
- This is exactly the WAT workflow in practice: W=outcome description, A=Claude reasons, T=Claude builds

---

## MODULE 4: CLAUDE CODE

### PHASE 1: SETUP & FIRST WORKFLOW

**Lesson 1.1, Introduction**
Claude Code is a command-line AI agent. It doesn't just answer questions, it reads files, writes code, runs tools, browses the web, and loops until the job is done. This is the foundation of every automation King David builds.

**Lesson 1.2, Setup**
- Install Claude Code via terminal: `npm install -g @anthropic/claude-code`
- Run `claude` in any folder to start a session
- The model (Sonnet, Opus, Haiku) can be swapped mid-session

**Lesson 1.3, Project + CLAUDE.md**
CLAUDE.md is the "project brain file." It sits in the root of every project folder. Claude reads it automatically at the start of every session in that folder. This is where you put: operating rules, the tech stack, the goal of the project, the persona, any constraints.
- Confirmed: This is EXACTLY the WAT framework King David already uses, Nate teaches it identically
- CLAUDE.md = the W (Workflow layer) of WAT

**Lesson 1.4, n8n MCP Server**
n8n is a visual workflow builder. It can be connected to Claude Code via MCP (Model Context Protocol). When connected, Claude can create, edit, and run n8n workflows using natural language. You describe the workflow → Claude builds it visually in n8n.

**Lesson 1.5, n8n Skills**
Pre-built workflow patterns for n8n, structured as slash commands. These are reusable "recipes", one command runs a whole workflow type (e.g., /n8n-lead-gen, /n8n-email-parse).

**Lesson 1.6, Verify All Tools Connected**
Before running any project: confirm every MCP is listed in settings.json and responding. Quick test: run a simple command that uses each tool (e.g., `read a file` for filesystem, `take a screenshot` for Playwright). If any tool fails, the whole pipeline breaks silently.

**Lesson 1.7, Demo: The Full Cycle**
Watch a complete end-to-end run: user gives goal → CLAUDE.md is read → Claude reasons → tool executes → output delivered. This is the live WAT chain running.

---

### PHASE 2: MASTERING CLAUDE CODE

**Vibe Coding Framework**
The single most important mindset shift in the entire module:
- Old way: describe the code you want written
- Vibe Coding way: describe the **outcome** you want achieved
- Claude asks clarifying questions, proposes a plan, then builds
- This matches the WAT approval workflow perfectly

**Four Build Phases (Non-Negotiable)**
Every build follows this exact sequence:
1. **Plan**, Claude proposes an approach, asks questions
2. **Approve**, King David reads plan, says yes (or adjusts)
3. **Build**, Claude executes fully, no mid-task stops
4. **Test/Optimize**, Claude verifies output, loops if needed

**Skills System**
Skills = reusable slash commands backed by markdown instruction files.
- Every skill is a markdown file in the `commands\` folder
- Triggered by `/skill-name` in Claude Code
- Community member Jason Hsieh built 80+ skills and shares them via a `/submit-skill` system
- Key insight: Skills grow over time. The more you build, the more powerful the system becomes.
- King David already has 12 skills, this confirms the direction is right

**MCP Servers**
MCP = Model Context Protocol. Each MCP server gives Claude a new capability (browser control, web search, file access, calendar, etc.).
- Found via: MCP directories (mcp.run, smithery.ai)
- Connected via: settings.json
- Active ones for King David: Firecrawl, Playwright, Gmail
- Pending: Brave Search, GitHub, Google Calendar

**Agentic Workflows**
The difference between a chatbot and an agent:
- Chatbot: answers questions and stops
- Agent: receives a goal, plans, takes actions, handles obstacles, loops until done
- Key properties: autonomous decisions, handles ambiguity, adapts to changing conditions
- This is what Claude Code is, an agent, not just a chatbot

---

### PHASE 3 & PHASE 4 · NOT YET AVAILABLE
These modules (Hosting & Deployment, Building Frontends) exist in the sidebar but contain no lessons. Coming soon. Check back in future sessions.

---

## MODULE 7: MEMBER PERKS

### What's Included
- Tool discounts and partner deals for AIS members (check the module directly for current codes, they change)
- **$3M Savings Vault**, unlocked with Premium membership. A collection of tools, templates, and deal codes that Nate values at $3M combined. Premium bypasses ALL course gating instantly.
- Community resources: templates, scripts, swipe files shared by members
- Access to live calls + recordings
- Access to the Skool post leaderboard (engagement = Level 3 faster)

### Key Unlock: Level 3
- 20 likes on your posts/comments = Level 3
- Level 3 unlocks: Course 2 (AI Partner Model), the core business model
- Can be hit in ~30 minutes by posting intro + engaging with posts
- Premium membership bypasses this gating completely

---

## COMMUNITY RESOURCES

### Claude Code Project Starter Kit
GitHub repo maintained by AIS community. Contains:
- Boilerplate CLAUDE.md templates
- Pre-built agents folder structure
- Skills (slash commands) pre-written
- Ready to fork and adapt for any project
- Saves 2-3 hours of setup per new project

### Nate Herk YouTube Database (Google Sheets)
Full database of all 87 videos with summaries, linked from the classroom.
URL: https://docs.google.com/spreadsheets/d/1h5k7vAAXl5_f4VtguDkHwCCy-S-dd7RfG3-rUiMxfPw
Already extracted into `ais_all_learnings.md` under the YouTube section.

### Community Shared Skills Library
Members share their custom skills in the community posts. Best ones:
- **/studynotes**, sends formatted notes to Obsidian with audit logs (author: community member, name not recorded)
- **CLAUDE.md builder**, auto-generates a CLAUDE.md file for any new project
- **/submit-skill**, Jason Hsieh's system for submitting skills to a shared library

### Other Resources
- Pinned post templates for outreach (cold DM, cold email)
- Client onboarding checklist
- Proposal deck template (pairs with Jan 19 video on proposal automation)

---

## LIVE CALL RECORDINGS

60+ recordings available in the classroom. Topics covered include:
- Client acquisition deep dives
- Live builds (watch Nate build real automations start to finish)
- Q&A sessions (members ask about pricing, outreach, tech issues)
- Tool comparisons (n8n vs Claude Code, Clawdbot vs local, etc.)
- Income reports and case studies from community members

**How to use:** Search recordings by topic when you hit a specific problem (e.g., "I can't close clients" → find the client acquisition call). Don't try to watch all 60+, use them as a reference library when stuck.

---

---

## NATE HERK · FULL YOUTUBE VIDEO DATABASE

**Source:** Google Sheets database linked from AIS community classroom
**Total videos:** 87 (Q1 2026: 50 | Q2 2026: 37)
**Sheet URL:** https://docs.google.com/spreadsheets/d/1h5k7vAAXl5_f4VtguDkHwCCy-S-dd7RfG3-rUiMxfPw

### Q1 2026 (Jan· Mar)

| Date | Title | Summary |
|------|-------|---------|
| Jan 5, 2026 | Once You Know This, Building RAG Agents Becomes Easy in n8n | Core RAG concepts that make building agents in n8n click |
| Jan 7, 2026 | I Built a New AI System in 3 Hours (and got paid $1650) | Live build of a paid AI system in 3 hours, start to finish |
| Jan 12, 2026 | I Built a Voice Agent That Calls Every New Lead (n8n + Vapi) | Automated voice agent that calls and qualifies every new lead |
| Jan 14, 2026 | Easiest Way to Migrate n8n Workflows Between Accounts (cloud to self-hosted) | Step-by-step n8n workflow migration between cloud and self-hosted |
| Jan 14, 2026 | Claude Code is Better at n8n than I am (Beginner's Guide) | Using Claude Code to build and manage n8n workflows from scratch |
| Jan 16, 2026 | Build ANYTHING with Claude Code & n8n (Beginner's Guide) | Build full apps and automations with Claude Code and n8n |
| Jan 19, 2026 | I Built an AI System That Automates My Proposals (n8n + Gamma) | AI system that auto-generates client proposals using n8n and Gamma |
| Jan 19, 2026 | How I INSTANTLY Generate Proposal Decks with n8n AI Agents | Instantly generate polished proposal decks with n8n AI agents |
| Jan 21, 2026 | Master 95% of Claude Code in 36 Mins (as a beginner) | Complete beginner's guide to Claude Code, setup through advanced usage |
| Jan 22, 2026 | I Will Never Fix Another n8n Workflow (Claude Code) | Let Claude Code auto-detect and fix broken n8n workflows |
| Jan 25, 2026 | Agentic Workflows Just Changed AI Automation Forever! (Claude Code) | How agentic workflows with Claude Code are changing AI automation |
| Jan 27, 2026 | Set Up Clawdbot on a VPS in Minutes (no mac mini) | Set up Clawdbot on a VPS without needing a Mac Mini |
| Jan 28, 2026 | 100 Hours Testing Clawdbot vs Claude Code (honest results) | Honest comparison after 100 hours testing Clawdbot vs Claude Code |
| Jan 30, 2026 | I Turned Clawdbot Into the Ultimate Personal Assistant | Turn Clawdbot into a personal assistant that handles everything |
| Feb 1, 2026 | Is n8n Dead? | Honest take on whether n8n is still relevant in 2026 |
| Feb 4, 2026 | How to Sign Your First AI Automation Client in 7 days (With Proof) | Proven framework to sign your first AI client in 7 days |
| Feb 7, 2026 | How I'd Teach a 10 Year Old to Build Agentic Workflows (Claude Code) | Agentic workflows explained simply enough for a 10 year old |
| Feb 11, 2026 | Turn Any Website Into LLM Ready Data INSTANTLY | Convert any website into clean, LLM-ready data instantly |
| Feb 14, 2026 | How a College Student Made $500k with Cold Email (Exact Framework) | Exact cold email framework a college student used to make $500k |
| Feb 16, 2026 | How to Sign AI Workflow Clients (With 0 Followers) | How to land AI workflow clients starting with zero followers |
| Feb 19, 2026 | Building Beautiful Websites with Claude Code Is Too Easy | Build stunning websites with Claude Code, no design skills needed |
| Feb 20, 2026 | The EASIEST Way to Host Your Claude Code Agents | Simplest way to host and deploy Claude Code agents online |
| Feb 23, 2026 | From Zero to Your First Agentic AI Workflow in 26 Minutes (Claude Code) | Build your first agentic AI workflow from scratch in 26 minutes |
| Feb 25, 2026 | I Can Actually Watch My AI Agents Work Now | Watch AI agents work in real-time with new observability tools |
| Feb 25, 2026 | Claude Code Just Added What Everyone Wanted (Remote Control) | Claude Code's new remote control feature for managing agents |
| Feb 27, 2026 | Master 95% of Claude Code Skills in 28 Minutes | Master Claude Code skills system in 28 minutes, complete guide |
| Feb 27, 2026 | The NEW Nano Banana 2 + Antigravity Destroys Every AI Image Tool | Nano Banana 2 + Antigravity outperforms every AI image tool |
| Mar 3, 2026 | The NEW Nano Banana 2 + Claude Code = $10k Websites | Build $10k-quality websites with Nano Banana 2 and Claude Code |
| Mar 5, 2026 | Turn Claude Code Into Your Executive Assistant in 27 Mins | Set up Claude Code as a full executive assistant in 27 minutes |
| Mar 5, 2026 | Claude Code Skills Just Got Even Better | Latest improvements to Claude Code's skills system |
| Mar 6, 2026 | Cursor Automations Clearly Explained (worth learning?) | Cursor Automations explained clearly, worth learning or not |
| Mar 7, 2026 | Claude Code 2.0 Is Finally Here | Everything new in Claude Code 2.0, the biggest update yet |
| Mar 7, 2026 | This New Claude Code Feature is a Game Changer | Game-changing new Claude Code feature explained step by step |
| Mar 8, 2026 | How to Build $10,000 Agentic Workflows (Claude Code Tutorial) | Build premium agentic workflows worth $10,000 with Claude Code |
| Mar 10, 2026 | Google's New Tool Just 10x'd Claude Code | Google's new tool supercharges Claude Code productivity by 10x |
| Mar 11, 2026 | I Taught Claude Code to Play Tetris... It Broke the World Record | Claude Code learns to play Tetris and beats the world record |
| Mar 11, 2026 | Google's New Model + Claude Code Just Changed RAG Forever | Google's new model + Claude Code transforms RAG forever |
| **Mar 12, 2026** | **Build & Sell with Claude Code (10+ Hour Course) ⭐** | **Comprehensive 10+ hour course on building and selling with Claude Code · THE MAIN COURSE** |
| Mar 17, 2026 | Generate Content for 9 Socials on Autopilot with Claude Code | Auto-generate content for 9 social platforms with Claude Code |
| Mar 21, 2026 | Stop Learning n8n in 2026...Learn THIS Instead | Why you should learn Claude Code instead of n8n in 2026 |
| Mar 23, 2026 | How to Build Claude Agent Teams Better Than 99% of People | Build Claude Code agent teams better than 99% of people |
| Mar 23, 2026 | This $100M AI App Just Changed Software Forever | How a $100M AI app is changing the software landscape forever |
| Mar 24, 2026 | Claude Code Just Got Another Huge Upgrade | Claude Code's latest major upgrade and what's new |
| Mar 24, 2026 | Claude Code Just Dropped Memory 2.0 | Claude Code's new Memory 2.0 feature explained in depth |
| Mar 24, 2026 | STOP Using Bypass Permissions, Use This New Feature Instead | Better alternative to bypass permissions in Claude Code |
| Mar 26, 2026 | Claude Code + iMessage is Finally Here | Claude Code now integrates with iMessage, full setup guide |
| Mar 28, 2026 | Gemini 3.1 Flash Live Just Changed Voice Agents Forever | Gemini 3.1 Flash Live transforms voice agent development |
| Mar 28, 2026 | Claude Code + Paperclip Just Destroyed OpenClaw | Claude Code + Paperclip destroys OpenClaw in head-to-head test |
| Mar 30, 2026 | I've Built 500 AI Workflows, This is What Businesses Want in 2026 | Lessons from 500 AI workflows: what businesses actually want |
| Mar 31, 2026 | Codex Just 10x'd Claude Code Projects | Codex integration makes Claude Code projects 10x more powerful |

### Q2 2026 (Apr· May)

| Date | Title | Summary |
|------|-------|---------|
| Apr 1, 2026 | Claude Code Source Code Just Leaked… 8 Things You Must Do | 8 things you must do after the Claude Code source code leak |
| Apr 2, 2026 | 18 Claude Code Token Hacks in 18 Minutes ⭐ | 18 practical hacks to reduce Claude Code token usage |
| **Apr 4, 2026** | **Ollama + Claude Code = 99% CHEAPER ⭐** | **Use Ollama with Claude Code to cut costs by 99% · KEY cost tool** |
| Apr 5, 2026 | Andrej Karpathy Just 10x'd Everyone's Claude Code | How Andrej Karpathy's techniques 10x'd Claude Code for everyone |
| Apr 6, 2026 | Planning In Claude Code Just Got a Huge Upgrade | Major upgrade to planning mode in Claude Code |
| Apr 8, 2026 | I Tested Claude's New Managed Agents ⭐ | Hands-on test of Claude's new Managed Agents feature |
| Apr 9, 2026 | Claude Just Told Us to Stop Using Their Best Model | Why Claude says to stop using their best model, and what to use instead |
| Apr 11, 2026 | Seedance 2.0 + Claude Code Creates $10k Websites in Minutes | Build stunning websites with Seedance 2.0 looping videos and Claude Code |
| Apr 12, 2026 | Unlock the Next Evolution of Claude Code with One Plugin | Install and use the Superpowers plugin to level up Claude Code |
| Apr 13, 2026 | Claude Code vs Google Antigravity... Which is Better? | Compare Claude Code and Antigravity after 100 hours of real testing |
| **Apr 14, 2026** | **Claude Code Finally Gave Us Scheduled Automations ⭐** | **Set up cloud-based scheduled automations with Claude Code routines** |
| Apr 15, 2026 | Claude + HeyGen Just Changed Content Creation Forever | Build a fully automated video production pipeline using Claude Code, HeyGen, ElevenLabs |
| Apr 16, 2026 | Claude Opus 4.7 Just Dropped... Or Did It Really? | Breakdown of the Opus 4.7 launch and the 4.6 quality controversy |
| Apr 17, 2026 | I Turned Claude Opus 4.7 Into a 24/7 Trader | Autonomous Opus 4.7 trading bot on Claude Code cloud routines placing live Alpaca trades |
| Apr 18, 2026 | Claude Just Changed Video Editing Forever | Two natural-language motion-graphic workflows using Claude Design and Hyperframes |
| Apr 20, 2026 | How to Manage Your Claude Limits Better Than 99% of People ⭐ | Manage Claude Code session limits better than 99% of people |
| Apr 21, 2026 | Claude Design Builds Beautiful 3D Websites Instantly (full course) | Full course on building 3D scroll-driven websites in Claude Design |
| Apr 22, 2026 | OpenAI Image 2 is Nuts. Here are 10 Ways to Use it | 10 practical ways to use GPT Image 2, OpenAI's new top-ranked image model |
| Apr 23, 2026 | Claude + HyperFrames Just Solved Video Editing | End-to-end AI video editing with Claude Code, Video Use, and HyperFrames |
| Apr 25, 2026 | Claude Code + Playwright Automates Literally Anything ⭐ | Automate literally anything on the web with Claude Code and Playwright |
| Apr 27, 2026 | 32 Claude Code Hacks in 16 Mins ⭐ | 32 Claude Code hacks across beginner, intermediate, and advanced tiers |
| Apr 30, 2026 | Claude Design Masterclass: Websites, Videos & More (2 Hours) | Two-hour masterclass on building a complete brand and launch video in Claude Design |
| **May 1, 2026** | **Build & Sell Claude Code Operating Systems (2+ Hour Course) ⭐** | **Build and sell Claude Code Operating Systems with the Three Ms framework** |
| May 3, 2026 | I Tried 100+ Claude Code Skills. These 6 Are The Best ⭐ | The 6 Claude Code skills businesses actually pay for |
| May 4, 2026 | Building Realistic Voice Agents Has Never Been Easier | Build a realistic sales-and-booking voice agent with Claude Code, ElevenLabs, and Cal.com |
| May 5, 2026 | Higgsfield Just Turned Claude Into a Creative Agency | Turn Claude Code into a creative agency with Higgsfield for image and video ads |
| May 6, 2026 | Master 97% of Codex in 1 Hour (full course) | Master 97% of Codex in one hour with a full end-to-end project build |
| May 8, 2026 | Overwhelmed By AI? Just Copy My Tech Stack ⭐ | Steal Nate's S/A/B/C tier AI tool stack and the mindset that keeps it lean |
| May 9, 2026 | Printing Press Just 10x'd Everyone's Claude Code | Turn any service into an agent-native CLI in 10 minutes with Printing Press |
| May 12, 2026 | Multi-Agent Building In Claude Code Somehow Got Easier ⭐ | Claude Code's new agent view turns terminal-tab chaos into one tab |
| May 12, 2026 | Every Level of Claude Explained in 21 Minutes ⭐ | The 5 levels of Claude every user needs to know |
| May 15, 2026 | I Tested 3 Ways to Deploy Claude Agents (Here's When to Use Each) ⭐ | 3 ways to deploy Claude Code agents and when to use each |

---

## COMMUNITY POSTS · HIGH VALUE

### Hermes Discussion Thread
**Post:** "Why are you recommending OpenAI Codex over OpenRouter for Hermes?"
**What was learned:**
- Hermes is an active topic in the community, multiple members using it
- It's a persistent AI agent platform (not a plugin, runs as its own process)
- The debate: OpenAI Codex (powerful but costly) vs OpenRouter (routes to cheapest available model)
- Community consensus: OpenRouter for routine/memory tasks, Codex or Claude for reasoning-heavy tasks
- Relevance: King David wants Hermes as a "tank agent", OpenRouter routing makes sense for cost optimisation

### /studynotes Skill → Obsidian
**Author:** Community member (name not recorded)
**What it does:** 
- Triggered by `/studynotes [topic]`
- Claude generates a structured study note on any topic
- Automatically formats it: title, key concepts, bullet points, links
- Sends the note directly to Obsidian vault via Obsidian's local REST API
- Creates an **audit log**, every note logged with timestamp and topic
- Notes are auto-linked to related existing notes in the vault
**Why it matters for King David:** This is the exact bridge between Claude and Obsidian we want to build. The skill shows the pattern: Claude generates → Obsidian receives → notes auto-link.

### CLAUDE.md Builder
A skill/tool that auto-generates a project CLAUDE.md for any new folder.
- You describe the project in plain English
- The builder creates a CLAUDE.md with: goal, tech stack, operating rules, personas
- Saves 30-60 minutes per new project setup
- Pattern worth adding to /plan skill

### Claude Design (New Tool · May 2026)
Claude Design = Claude's native design mode for building visual outputs.
Capabilities:
- Branded HTML pages (styled, professional)
- PDFs and slideshows
- Interactive walkthroughs
- 3D scroll-driven websites (full course from Nate, Apr 21 video)
- Works with brand colors and assets automatically
**Verdict:** This directly upgrades the /website skill. Instead of plain HTML/CSS, Claude Design can produce agency-quality visual output. Evaluate before next website build.

### Printing Press
**What it is:** A tool that turns any service or API into an agent-native CLI in ~10 minutes.
- You point it at a service (e.g., a booking system, a CRM, a database)
- Printing Press wraps it as a tool Claude Code can call directly
- The service becomes a slash command: `/book-appointment`, `/add-contact`, etc.
**Why it matters:** Anything King David wants Claude to interact with, Fiverr, Calendly, a client's CRM, can be wrapped this way in 10 minutes instead of building custom API integrations.
**Source:** May 9, 2026 Nate Herk video: "Printing Press Just 10x'd Everyone's Claude Code"

---

## 2026-05-23 AIS AUDIT · NEW FINDINGS FROM NATE HERK COMMUNITY POSTS

### ⚡ AIS LIVE · July 11-12, 2026 (Virtual Event) · TIME-SENSITIVE FOR KING DAVID
**Source:** Nate Herk post in AIS+ Announcements, 4 days ago
**URL:** https://www.skool.com/ai-automation-society-plus/heres-how-to-get-your-tickets-to-ais-live
**Registration:** https://app.aiautomationsociety.ai/ais-live/register/
**Quote:** "AIS Live: Real Projects, Real Revenue. Every person on stage has to show their actual work. Actual projects, clients, numbers."

**Format:**
- Day 1: What businesses are actually paying for in 2026, exact projects, industries, deliverable formats
- Day 2: Niche selection, cold outreach that books calls, discovery call that closes, pricing, delivery, retainer conversion
- ~3,000 attendee cap, 3,600+ AIS+ members → first-come basis

**King David's access:**
- IF annual member: FREE VIP ticket ($199 value), just fill out a form. **Check email already.**
- IF monthly member: 50% off with code AISLIVE50
- Annual plan: $699/year (vs $99/month = $1,188, save $489), includes free ticket to every future AIS Live (quarterly)

**Why this matters for King David specifically:**
- He just booked his first client (per AIS+ Wins Recap May 16-22)
- Day 2 content is EXACTLY his current bottleneck (first client → retainer conversion)
- This is the highest-leverage live training available to him right now
- Other AIS+ members at this event = peer network for second-client referrals

---

### Wins Recap Data · Real Numbers From AIS+ Members (May 16-22, 2026)
**Source:** AIS+ Community Wins Recap by Yash Chauhan (community manager), with Nate's reactions
**URL:** https://www.skool.com/ai-automation-society-plus/community-wins-recap-may-16-may-22

**Income proof + replicable tactics from peers this week:**
| Member | Win | Tactic |
|---|---|---|
| Michael Garcia | First big deal closed | Wholesale real estate automation engine: MLS/off-market property pulling, Claude deal scoring, investor pipeline |
| Muhammad Butt | $1,200 project | Gym lead qualifier, sourced via friend referral |
| Josh Holladay | $650 close | Anchored value, learned to ask for more |
| Michael Elliott | 3 client builds | Pushed retainers + care plans (vs flat-fee one-offs) |
| **Kingdavid Agbidi** | **Booked first client** | Built portfolio + chose niche + showed AI solving real problem |
| Emerald Dryad | Real estate gig | 10% profit-share basis |

**Pattern emerging:** Real estate + auto detailing + gym + recurring care plans are repeating themes. King David's locked niche (Dublin plumbers) sits in the same trade-services tier as these wins, confirms niche choice is right.

---

### Case Study #1: Luca Giovinazzo · Auto Detailing Full-Stack Build (€-figure undisclosed but "first big delivery")
**Source:** AIS+ post "🏆 First Client Project Delivered and Live" 2 days ago
**URL:** https://www.skool.com/ai-automation-society-plus/first-client-project-delivered-and-live

**Architecture (replicable template for King David's plumber pitch):**

**Backend stack:**
- n8n as orchestrator
- Google Sheets + Google Drive as the database/storage layer
- Telegram as the client-facing interface
- Resend for transactional email

**Capabilities built:**
1. **CRM/contract intake**, Client photographs a contract via Telegram → AI extracts data → confidence-scores it → writes to sheet (auto-pauses below 80% for manual review) → auto-emails contract to customer
2. **Materials/inventory agent**, Telegram queries to check tank levels, daily low-stock alerts when <30%, immediate alerts at 0% (with timing logic to prevent spam)
3. **Financial reporting**, Weekly Sunday summary (revenue, job count, avg job value), Monday upcoming-jobs preview
4. **Booking funnel**, Google Calendar ↔ Cal.com booking page ↔ custom website (packages, pricing, before/after gallery, quote form, FAQ, custom domain)
5. **Error logging**, All-automation failure catcher → LLM classification → logs + immediate notification to Luca (not silent failures)
6. **ROI tracker**, Execution time saved per run, feeds 30/90/180-day KPI reports for client retention proof

**Pitch tactic:** Did the build FREE in exchange for testimonial + first W. Friend-of-a-friend connection. Built over ~1 month.

**Why this is gold for King David:** This is the exact architecture template for the Dublin plumber pitch. Replace "auto detailing" with "plumbing", same CRM intake (job tickets), same inventory (parts/stock), same financial reports, same booking funnel. Could be a €500-2,000 first paid build.

---

### Case Study #2: Curtis Morgan · Solar Sales Automation (Day 5 in AIS+)
**Source:** AIS+ post "Day 5 in AIS+: AI Implementation in Solar☀️" 4 days ago
**URL:** https://www.skool.com/ai-automation-society-plus/day-5-update-ai-implementation-in-solar

**Key insight Curtis surfaced:** "My real constraint isn't time. It's follow-through on the handful of tasks that drive revenue, outreach + giving feedback to SDRs on appointment-setting. Those are high friction, so they slip first when busy. The point isn't saving minutes, it's removing enough friction that the important work gets done."

**Automations planned (replicable):**
- Outreach prioritisation: builds and ranks call list with context attached + drafts follow-ups → keeps top-of-funnel warm
- SDR coaching agent: analyses SDR appointment-setting performance → generates specific weekly feedback → compounds over months into stronger sales reps
- Post-consultation follow-up: keeps leads warm between meeting and close

**Key lesson:** "The automation itself is the last step. The real work is defining the decision rules first, the prioritisation logic and scoring rubric. Once that's clear, the build is almost the easy part."

**Why relevant for King David:** Confirms that the discovery + rule-definition phase is where most of the value lives, not the build phase. Maps directly to /monetize + /setup_hours SOPs. Add to those skill SOPs: "Spend 60%+ of session time on decision rules with the client, not the build."

---

### Token Dashboard + Session Handoff Skill (Nate Herk)
**Repo:** https://github.com/nateherkai/token-dashboard
**Status:** Listed in audit_log/to_install.md for batched install after audit complete

---

### Glaido Speech-to-Text (Nate's pick)
**URL:** https://get.glaido.com/nate
**Status:** Listed in audit_log/to_install.md, King David is voice-input primary, so this could materially improve session quality


---

## 2026-05-23 AIS+ CLASSROOM AUDIT · FULL COURSE INVENTORY

Captured via Skool's `__NEXT_DATA__` JSON (efficient, no per-lesson navigation needed). Full module trees saved in `AIS_Audit\audit_log\aisplus_classroom_inventory.md`.

### Course-level summary

| Course | Modules | Completed | Status | Min Tier |
|---|---|---|---|---|
| START HERE | 8 | 8 ✅ | done | - |
| The AI Partner Model | 6 | 6 ✅ | done | 2 |
| Build Your Portfolio | 62 | 15 (24%) | 47 modules untouched | - |
| **Claude Code** | **50** | 0 | untouched | - |
| Get Your First Clients | 17 | 0 | 🔒 23 days OR Premium upgrade | 2 |
| Scale | 84 | 0 | 🔒 83 days OR Premium upgrade | 2 |
| Member Perks | 13 | 0 | untouched | - |
| Archived | 142 | 0 | low priority | - |
| Community Resources | 167 | 0 | members' shares | - |
| Live Call Recordings | 82 | 0 | Q&A calls | - |

**Total accessible to King David: ~553 modules** across 8 courses (+ 2 locked for 23/83 days unless Premium upgrade)

### Course IDs (for direct URL navigation)
- Build Your Portfolio: `4d72d7dae6224d698ba6a2ad9dff8aec` (slug: `d99017d2`)
- Claude Code: `936f7b968e6040b090e1817ff0560018` (slug: `bd6b51dc`)
- Member Perks: `1ed863133d7d` (slug: `308fec3a`)
- The AI Partner Model: `c69869fe6f614410ad88146879e007a3`
- START HERE: `37840c35293c4a69878a6ea30fc5e71d`

### Claude Code course structure (50 modules, 4 phases)

**Phase 1, Setup & First n8n Workflow (18 modules):** Claude Code setup, CLAUDE.md, n8n MCP server, n8n Skills, Vibe Coding Framework, Masterclass building/testing, Enhancement Philosophy & Techniques

**Phase 2, Mastering Claude Code (12 modules):** Agentic Workflows, **The WAT Framework** (Module 1.3, ⚠️ flag below), First Agentic Workflow, MCP Servers in Cloud Code, Firecrawl MCP Research, Skills + Skills in Action, Slide Deck Generator, **Token Management** (Module 1.10, relates to prompt caching post), Personal Challenge

**Phase 3, Hosting & Deployment (10 modules):** GitHub, **Trigger Dev** (Nate still teaches it, King David has migrated to Claude Code Scheduled Automations instead), Secrets Management, Scheduled Research Agent Masterclass, Webhook Report Generator, Error Handling

**Phase 4, Building Frontends (8 modules):** Mental Model for Apps, Frontend Tips, **Build My First AI Lead Qualifier App** (directly relevant, King David's `/scrape` skill could pair with this), Authentication & Security Audit, Integrate Stripe Payments, Frontend for n8n Workflow

### Build Your Portfolio course structure (62 modules, 3 macro-sections)

**Macro 1, Why You Need a Portfolio (5 modules):** Why portfolio first, why no niche yet, what businesses pay for, client-ready portfolio anatomy

**Macro 2, Agent Zero / AI Foundations (~33 modules):**
- Large Language Models (6), Intro to AI, Understanding LLMs, Popular LLMs, Open-Source vs Closed-Source, Prompt Engineering
- Data Foundations (5), What is Data, Data Types, What is JSON, Data Processing
- APIs & HTTP Requests (1)
- **RAG & Vector DBs (9 modules)**, RAG, Vector DBs, Embeddings, Dimensions, Real-World Applications, Tokenization, OpenAI Tokenizer, Context Windows ← directly relevant to King David's `/search` skill + Obsidian
- ChatGPT to Autonomous Agents (6), Modern AI, AI Workflows, AI Agents, **AI Voice Agents** (relevant to King David's planned `/voice-agent`), Ethical AI

**Macro 3, "10 Hours to 10 Seconds" (~25 modules):**
- Phase 1: Find Your Personal Leverage (6), Time Lens, Personal Audit, Income Lens, Step-by-Step Test, **ICE scoring** (prioritisation framework)
- Phase 2: Mapping the Steps (7), Process Mapping, Workflow Triggers, Data Sources & Transformation, Integrating AI, Wireframing, **Intro to Context Engineering** ← matches Nate's recent Karpathy video framing
- **Phase 3: Finding Opportunities for Clients (8 modules)** ⭐, DIRECTLY relevant to King David's first-client situation:
  - The Time Lens for Businesses (Productivity Lesson)
  - The Income Lens for Businesses (Growth Lesson)
  - **The SOP Audit: Inventory vs Creation**
  - **Scoring Before Mapping (Business ICE)**
  - **The Live Blueprint: Mapping in the Room** (on-site discovery approach)
  - **Should you charge for the Opportunity Map?**

### Member Perks course (13 modules · partial inventory from sidebar)
Visible top-level lessons:
1. Weekly Contributor Rewards
2. **Become an AIS+ Affiliate 💸**, 20% recurring of every referred member's $99/mo fee, lifetime
3. Represent the Group!
4. The Map Feature
5. **$3M Savings Vault** ← (need to navigate to extract: likely third-party tool discounts/deals)
6. **Lifetime Membership - Level 9** ← (need to navigate)
*Remaining 7 modules are sub-sections, not yet enumerated*

### Discovered constraints
- Most lessons are VIDEO-first. Text extraction only captures the lesson description, not the lesson content.
- Skool's "sortable" UI wrappers block Playwright clicks, bypassable via pointer-event JS dispatch, but inconsistent
- The `__NEXT_DATA__` JSON contains all course/module metadata (titles, descriptions, completion %) but NOT lesson body or video URLs
- Direct URL navigation works once we know course IDs (extracted from JSON)
- To fully audit video content: need a video-transcript extractor pipeline (added to `to_install.md` Item #4)

### ⚠️ WAT Framework attribution issue
- **CLAUDE.md currently says:** "WAT Framework, King David's invention"
- **Reality discovered:** Nate Herk's Claude Code course Phase 2 Module 1.3 is titled "The WAT Framework"
- **Likely true picture:** WAT is Nate's framework. King David learned it from Nate's content and made it his own, but it's not his invention.
- **Action needed:** Either verify Nate's WAT (W=?, A=?, T=?) matches what King David documents (Workflow / Agent / Tool / Skill), OR reframe attribution in CLAUDE.md and `reference_wat_framework.md` from "your invention" to "Nate Herk's framework adopted into your system"
- **Risk if not fixed:** Pitching WAT to clients as "my framework" when it's Nate's = bad form and easy to disprove
- **Surfaced to:** `AIS_Audit\audit_log\to_review.md`

---

## 2026-05-23 CLASSROOM AUDIT (continued) · Live Call Recordings + Community Resources

Same `__NEXT_DATA__` JSON extraction approach. Two more courses fully inventoried; Archived (142 modules) skipped per relevance filter.

### Live Call Recordings (82 modules · Nate Q&A + guest speakers)

**🎤 Guest Speakers (13 calls):** Dan Martell, Cole Medin, **Max Tkacz** (n8n founder), Devin Kearns, Mark Kashef, Zubair Trabzada, Nick Sonnenberg, **Bart Veldhuizen** (n8n), Ahmed Mukhtar, The AI Automators, Zeb Evans, Rex Manchester, Nate Herk (in another community).

**⭐ TrueHorizon AI - $211k Deal series (5 modules)**, Real case study of a $211k AI deal:
- Part 1: Scoping & Discovery
- Part 1 Bonus Extra Session
- Part 2: Project Management
- Part 3: Modern Sales Pipeline
- **🎁 THAI Discovery Call SOP** ← reusable template

**💬 Q&As (50+ sessions)**, Most King-David-relevant:
- What service/product to offer
- Building Trust in Outreach
- What's the problem you're solving
- Discovery Calls and Niching Down
- First Consulting Call
- Quality Assurance and Client Communication
- Conducting an AI Audit
- Framing AI Automation Offers
- AI Automator Mindset
- High Impact, Low Effort
- Business Consulting and AI
- Claude Code or n8n?
- Claude Context Management
- AI Second Brain
- Member Wins

### Community Resources (167 modules · peer-shared gold)

**Agent Skills (6 modules):** Skill Builder, Excalidraw Diagrams, Excalidraw Style Images, **Nano Banana 2** (= KIE_AI), Nate's Frontend Design, **Video to Website** (King David already has `/video-to-website`)

**💎 Earn $ With GEMS (4 modules):** Business Gems, Thoughtful Gems, Techy Gems

**🌟 Wins (6 modules):** $60k Deal, $35k in 2 Weeks, $25k Deal, First AI Automation Client, First Project in 10 Days, First Automation

**⭐ Nate's AI Business Talks (16 modules):** Most King-David-relevant tactical money lessons:
- Building Agents... Now What?
- $1,200 in 2 Hours
- Sell AI Workflows (w/o Agency)
- 4 Agents for $23k Total
- Live $6k Agent Sale
- Why No One is Buying
- **Stop Selling Agents, Sell Solutions** ← important positioning
- How I'd Make Money with AI in 2026
- AI Isn't Hard. It's Misunderstood.
- Becoming an AI Consultant
- **Your First Client** ← directly relevant (King David just booked first)
- **Pricing Workflows** ← directly relevant
- Learning n8n in 2026
- $2,600 in 2 Hours
- Delivering n8n Projects
- $1,650 in 3 Hours

**Client Case Study Vault:** Jose M Lopes (1 so far)

**Community Builds (7 modules), real n8n workflows ready to study:**
Procurement Automation · Outbound Vapi Agent · Meal Plan Generator · Personalized Paint Protection Guide · Film Crew Booking · **Lead Qualifier** (= King David's wheelhouse) · **Lead Generator w/ Google Maps Scraper** (directly parallel to `/scrape`)

**💸 Discount Codes (9+ tools):** Airtop · Apify · Blotato · **Firecrawl** (you use it, likely member discount!) · Hostinger VPS · Lindy · Twitter Scraper · Poppy AI

**Identifying n8n Sales (5-part series):** How to find n8n sales opportunities, direct money play

**Useful Resources (7 modules):** Agentic Design Patterns (Google CTO guide), RAG Reranking, Claude Code Quick Reference, Beginner's Guide to MCP, Mac vs PC, Claude Code Project Starter Kit, Claude Cowork

**n8n Templates (60+ dated templates, 2025-2026)**, partial list of high-relevance ones:
- Gamma Proposals
- Outbound Lead Qualifier ← directly relevant
- RAG Pipelines · RAG Pipeline 2.0 · Reranking RAG Agent · First RAG Agent
- Inbox Manager · Inbox Management AI Agent · Customer Support Email AI Agent
- Resume Screening System
- Scraping Emails From Maps · Google Scraping Agent (LinkedIn Profiles) · Apify Scraping · Firecrawl Search and Scrape
- Newsletter System · Newsletter Creation Agent Team
- ElevenLabs Voice · Voice Travel Agent · Personal Assistant (with Voice Input/Output)
- Invoice AI Agent
- Simple AI Lead Nurturing
- HITL (Human in the Loop) · Human in the Loop Sales Team · Human in the Loop Calendar Agent
- Agent Swarm · Multi Agent System · Agentic RAG · 4 Agentic Frameworks
- JARVIS · Ultimate Personal Assistant · Personal Assistant 2.0
- 25 n8n Hacks
- 17 Nodes to Master
- Browser Agent · Twitter/X Scraper
- AI Marketing Team · Long Form Content Automation · Faceless Shorts Machine
- (50+ more dated entries)

**Guides📝 (4):** n8n Licensing, n8n + Google Setup, You're Building Agents Now What, **$1,200 for a 2-Hour Build** (written guide)

**AI Terms (5 levels):** Beginner-to-advanced AI glossary

**The Daily Node (7 modules):** Per-node n8n tutorials (Webhook, Form Trigger, Schedule Trigger, Manual Trigger, Chat Trigger, Error Trigger)

### Archived (SKIPPED) · 142 modules
Skipped per relevance filter ("Older content that's no longer part of the main path. Optional to explore."). If anything specific from Archived ever surfaces as needed, navigate directly via course ID `43176449c96e47b4b6743e1564ac5c13`.

---

## 2026-05-23 · WAT FRAMEWORK ATTRIBUTION CORRECTED

Per King David's own confirmation: *"I learned from Nate, so that's why I took his WAT framework."*

- WAT = **Nate Herk's framework**, taught in AIS+ Claude Code Phase 2 Module 1.3
- King David adopted it from Nate's content
- CLAUDE.md and `memory\reference_wat_framework.md` updated 2026-05-23 with correct attribution
- When pitching to clients: attribute to Nate ("Nate Herk's WAT framework I use to structure every automation")


---

## 2026-05-23 · VIDEO TRANSCRIPTS EXTRACTED (Loom + Fireflies)

Built a Loom transcript pipeline (yt-dlp + faster-whisper local + imageio-ffmpeg), runs fully offline, no paid APIs. Successfully transcribed 8 Loom AIS+ lessons + 2 Fireflies meeting recordings.

### KEY EXTRACT · Claude Code 1.3 "The WAT Framework" (Nate's video, confirmed via transcript)

Direct quote: "We use the WAT framework, where W stands for workflows, A stands for agent, and T stands for tools."

- Workflows = "instruction files written in markdown" (SOPs Claude reads)
- Agent = "Claude Code itself...the brain" (project manager that delegates to tools)
- Tools = "Python scripts that actually do the work. Each tool is going to have one specific job"
- Self-improvement loop: agent runs workflow → finds error → fixes tool → updates workflow file so error never repeats
- CLAUDE.md = "the onboarding document"

Confirmation: King David's WAT framework IS Nate's framework, taught in this video. Already corrected in CLAUDE.md + reference_wat_framework.md.

### KEY EXTRACT · Claude Code 1.10 "Token Management" (Nate's video)

**5 Cloud Code Prompting Patterns:**
1. Define the GOAL, not the steps. Tell agent WHAT you want, not HOW. Agent figures out the steps.
2. Be specific about the output. Vague: "make me a report" → Specific: "create a PDF report with executive summary, 3 competitor profiles, and recommendation section." Include file format, structure, naming, where to save.
3. Use plan mode first for non-trivial work. Approve plan → switch to bypass permissions → execute.
4. Give feedback, not corrections. Bad: "that is wrong, redo it." Good: "I liked this structure, but the tone is too formal." Agent learns + updates the workflow for next time.
5. Treat the agent like an expert. You are the manager, not the developer. "I want X. Ask me anything. Figure out the best approach."

**Context Rot:**
- The more you talk in a single session, the worse Claude gets. Not a bug, how attention mechanisms work.
- Past 60% context usage → model starts making mistakes it wouldn't have made before
- Context Threshold Strategy:
  - 0, 50% SAFE, work freely
  - 50, 70% YELLOW, start thinking about /compact
  - 70, 85% ORANGE, run /compact proactively
  - 85%+ RED, run /clear, start fresh

**/clear vs /compact:**
- /clear = full reset. Use when switching tasks OR when quality degrades.
- /compact = smart summary. Use while still in same task but context climbing.

**5 Token-Saving Strategies:**
1. One task per session. /clear when done.
2. Define "done" with specific endpoint (e.g., "exactly 75 profiles"). Otherwise agent loops endlessly.
3. Use skills for specialized workflows. Don't bloat CLAUDE.md.
4. Disable unused MCP servers. Each adds tool definitions to every session's context.
5. Keep CLAUDE.md lean. Under 500 lines. Only include what applies to EVERY session.

Direct application to King David:
- CLAUDE.md is 373 lines, OK under cap
- ONBOARDING.md is 530+ lines, OVER cap, trim needed
- 5 MCP servers active (playwright, firecrawl, brave-search, github, n8n-mcp), disable any not in active use
- Use /clear between major task pivots (e.g., between AIS audit and Orcha deploy)

### KEY EXTRACT · TrueHorizon $211k Deal Anatomy (Fireflies Parts 2 + 3)

Real deal: $211k annual contract with mid-sized insurance company. Presented by Milan Tahliani (co-founder of TrueHorizon AI). Grew to 10 FT employees since January; 20+ enterprise/SMB implementations completed.

**Deal Structure:**
- Agent-by-agent deployment model
- Ongoing development included in base monthly fee (not separate change-orders)
- Value-based pricing (focus on demonstrating ROI + client cost savings)

**Technical Architecture:**
- Document processing automation: CSV/Excel/PDF/API/SQL inputs → AI-powered data extraction into standardized schemas
- Dynamic routing to compliance/underwriting/legal teams based on business logic
- Drop zone portal with drag-and-drop interface
- A/B testing of foundational models
- Comprehensive logging + audit trails for regulatory compliance

**5-Phase Delivery Workflow:**
1. Kickoff → 2. Architecture & Roadmapping → 3. Development → 4. Delivery & Handoff → 5. Deployment

**Tools Used:**
- ClickUp (6 task categories: Inbox / Product Backlog / Current Priorities / In Progress / Review / Done)
- Sprint-based 1, 2 week cycles
- Loom video documentation requirement for developers
- Automated batch QA using LLM as judge before production deployment

**Pricing & Sales:**
- Value-based pricing emphasized
- ROI as key decision factor
- Budget discovery via relationship-building (not direct asks)

**Hiring:** High-impact performers expected to generate 5, 10x their monthly salary

**Compliance:** SoC2 + ISO 27001 for specific industries. AWS Bedrock for local model hosting when client requires data sovereignty.

### KEY EXTRACTS · Build Portfolio Phase 3 Loom transcripts (6 lessons done, 1 in retry)
- Intro to Phase 3, transcribed
- The Time Lens for Businesses, transcribed
- The Income Lens for Businesses, transcribed
- The SOP Audit: Inventory vs Creation, transcribed
- Scoring Before Mapping (Business ICE), transcribed
- The Live Blueprint: Mapping in the Room, transcribed
- Should you charge for the Opportunity Map?, retry-batch running

Each transcript is in knowledge/ais_resources/transcripts/loom_AIS_PLUS_BP3_*.md.

### Gaps from this audit (honest list)
- Nate's "Your First Client" + "Pricing Workflows" + "Stop Selling Agents" lessons, YouTube embeds, lazy-loaded, couldn't extract IDs without click-to-play. Defer to manual retry.
- TrueHorizon Discovery Call SOP, empty body, no embed visible.
- Pages 2-67 of Nate's historical posts, out of scope this session.
- ~16 other Nate Business Talks videos in Community Resources, out of scope.

### Tools installed for this audit
- yt-dlp (PyPI), Loom + Fathom downloader
- faster-whisper (PyPI), local CPU transcription, int8 quantized base model (~142MB)
- imageio-ffmpeg (PyPI), provides ffmpeg binary without system install
- Custom script: tools/transcript_extractor/loom_transcript.py, supports Loom + Fathom URLs

All fully local, no paid APIs, no auth, no telemetry.
