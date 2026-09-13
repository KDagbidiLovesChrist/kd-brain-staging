# AIS YouTube Teaching Plan
**Source:** Nate Herk YouTube database (87 videos, extracted 2026-05-16)
**Purpose:** What King David should learn from YouTube, in what order, and why

---

## Section 1: The Big Picture · What YouTube Teaches as a System

If you step back and look at all 87 videos together, one direction is crystal clear:

**Nate Herk has moved away from n8n and is fully committed to Claude Code.**

Here is the timeline of that shift, in plain terms:

- January 2026: Still using n8n but starting to compare it to Claude Code. Makes a video called "Claude Code is Better at n8n than I am."
- February 2026: Building beautiful websites with Claude Code alone. Hosting agents online. No n8n needed.
- March 2026: Publishes his 10+ hour flagship course, "Build & Sell with Claude Code." This is THE signal.
- March 21, 2026: Publishes "Stop Learning n8n in 2026... Learn THIS Instead." That is the final word.
- April, May 2026: Every video is Claude Code. Ollama, scheduled automations, Playwright, agent teams, operating systems, deployment options. n8n is gone.

**What is the core stack converging on in 2026?**

| Layer | Tool | What It Does |
|-------|------|-------------|
| Brain | Claude Code | Builds, reasons, writes, and runs everything |
| Browser | Playwright | Automates anything on the web |
| Local models | Ollama | Runs cheap local AI for routine tasks |
| Memory | Claude Memory 2.0 | Persistent memory across sessions |
| Scheduling | Claude Routines | Cloud-based scheduled automations |
| Deployment | VPS or Cloud | Runs your agent 24/7 |

**What has become outdated?**

- n8n, Still works, but Nate is not teaching it anymore. In 2026, Claude Code does what n8n did, without the visual node-building process.
- Trigger.dev, Still referenced in King David's setup, but Claude's built-in scheduled automations (Apr 14 video) may make this unnecessary.
- Cursor, Has a March video asking "is it worth learning?", the answer seems to be "maybe not if you're already on Claude Code."

**The single most important thing to understand:**

The direction is one tool (Claude Code) that runs everything. Not five tools duct-taped together. Claude Code replaces n8n, replaces trigger.dev, and handles websites, scraping, emails, and agent teams, all from one command line.

This is exactly what King David's WAT framework is built around. He is already on the right track.

---

## Section 2: The 6 Things Businesses Actually Pay For

Source: May 3 video, "I Tried 100+ Claude Code Skills. These 6 Are The Best"

| # | Category | What It Solves for a Business |
|---|----------|------------------------------|
| 1 | Lead generation and scraping | Finding new customers without manual research |
| 2 | Website building | Getting online fast, looking professional |
| 3 | Content and newsletter automation | Staying in front of customers without writing every week |
| 4 | Proposal and client intake | Winning jobs faster, less admin work |
| 5 | Executive / personal assistant | Organising daily work, email, calendar |
| 6 | Voice agents / appointment booking | Answering calls, booking clients automatically |

**How King David maps against these 6:**

| Skill | King David Has It? | Gap |
|-------|--------------------|-----|
| Lead gen scraping | YES · /scrape, working, on Fiverr | Needs Fiverr gig actually posted |
| Website building | YES · /website, working, Vercel | Needs Vercel account finalised |
| Newsletter automation | YES · /newsletter, Perplexity API | Needs paying client |
| Proposal generation | NO | Not built yet |
| Executive assistant | YES · /exec built | Not sold as a service yet |
| Voice agents | NO | Needs ElevenLabs + Cal.com setup |

**Verdict:** King David covers 4 of the 6 services. The two gaps are proposal generation and voice agents. Voice agents require more setup. Proposal generation could be added faster.

**Priority gap to close first:** Proposal generation, it directly helps King David win more clients AND it is a service he can sell to tradespeople who hate writing quotes.

---

## Section 3: The Priority Watch List · Top 10 Videos for King David

Chosen specifically for King David's situation: non-technical, targeting Irish and UK tradespeople and SMBs, services are scraping, websites, and newsletters, working within a budget.

**Video 1, May 3, 2026**
Title: "I Tried 100+ Claude Code Skills. These 6 Are The Best"
Why it matters: This is the business menu. It tells him exactly what to offer on Fiverr and to local businesses.
What to apply: Update Fiverr gig descriptions. Add any missing service to skill list.

**Video 2, May 1, 2026**
Title: "Build & Sell Claude Code Operating Systems (2+ Hour Course)"
Why it matters: The "Three Ms framework" maps directly to his WAT framework. Watching this could sharpen how he pitches WAT to clients.
What to apply: Compare Three Ms to WAT. Use the language from this video in Fiverr proposals.

**Video 3, Apr 4, 2026**
Title: "Ollama + Claude Code = 99% CHEAPER"
Why it matters: He is spending real money on Claude tokens. Ollama lets him run a free local model for cheap tasks and only use Claude for hard reasoning work.
What to apply: Identify which automations are "routine" vs "reasoning." Consider Ollama when scale demands it.

**Video 4, Apr 14, 2026**
Title: "Claude Code Finally Gave Us Scheduled Automations"
Why it matters: If Claude Code has built-in scheduling, he may be able to retire Windows Task Scheduler and trigger.dev entirely.
What to apply: Test Claude routines for newsletter scheduling. If reliable, retire the Task Scheduler script.

**Video 5, May 15, 2026**
Title: "I Tested 3 Ways to Deploy Claude Agents (Here's When to Use Each)"
Why it matters: He needs to choose the right deployment path without overbuilding. This video gives a clear decision framework.
What to apply: Pick ONE deployment method that fits his budget and scale right now.

**Video 6, Apr 25, 2026**
Title: "Claude Code + Playwright Automates Literally Anything"
Why it matters: He already has Playwright connected via /browser. This teaches patterns to get more out of it.
What to apply: Upgrade the /browser skill with any new patterns learned.

**Video 7, Apr 27, 2026**
Title: "32 Claude Code Hacks in 16 Mins"
Why it matters: 32 hacks in 16 minutes. Even if only 10 apply, that is 10 improvements in 16 minutes. High ROI per minute.
What to apply: Pick the 5 most applicable hacks and add them to settings.json or CLAUDE.md.

**Video 8, Apr 20, 2026**
Title: "How to Manage Your Claude Limits Better Than 99% of People"
Why it matters: He has hit context limits mid-session. This video gives practical ways to avoid running out mid-task.
What to apply: Add limit management techniques to his operating rules.

**Video 9, Mar 24, 2026**
Title: "Claude Code Just Dropped Memory 2.0"
Why it matters: His entire system is built on memory files. If Memory 2.0 changes how Claude stores information, he needs to know.
What to apply: Check if Memory 2.0 changes anything about memory/ folder or CLAUDE.md structure.

**Video 10, May 8, 2026**
Title: "Overwhelmed By AI? Just Copy My Tech Stack"
Why it matters: This is Nate's curated S/A/B/C tier tool list. King David does not need to try every tool, he just needs the top ones.
What to apply: Compare Nate's S-tier tools to what King David uses. Add what is missing. Remove what is rated low.

---

## Section 4: What to Build Next · Based on YouTube Trends

**What are businesses paying for in 2026?**

| Trend | King David's Status | Action |
|-------|-------------------|--------|
| Content automation at scale | Has /newsletter | Extend it · offer social media content as upsell |
| Voice agents for lead capture | Not built | Hold · requires ElevenLabs + Cal.com setup |
| Better websites | Has /website | Upgrade with Nano Banana 2 patterns when ready |
| Proposal automation | Not built | BUILD THIS · high demand, fast to sell |
| Multi-agent OS | Has WAT framework | This is the premium offer · not yet packaged for clients |

**The 2 new things worth adding to King David's service menu:**

**Add 1, Proposal/Quote Generator (/quote skill)**
What it is: A skill that takes a client's job details and generates a professional quote automatically.
Why it fits: He already scrapes tradespeople. A quote generator is the single highest-value thing he could hand them.
Effort to build: Medium, uses Claude to fill a template with job-specific details.
Price to sell: €150, 300 one-time setup, or €50/month as a service.

**Add 2, Social Content Autopilot (newsletter upsell)**
What it is: Extend /newsletter to also generate 5 social posts per week from the same research.
Why it fits: Same research pipeline, more output, justifies 30, 50% higher monthly fee.
Effort to build: Low, modification of what already exists.
Price to sell: Bundle with newsletter at €100, 200/month.

---

## Section 5: Cost Reduction Opportunities

### Ollama · 99% Cheaper (Apr 4 video)

**What is it?**
Ollama runs AI models directly on your own laptop for free. Think of it like this: Claude is your senior consultant, expensive, brilliant, handles the hard stuff. Ollama is your intern, free, handles the simple, repetitive work.

**Examples of what Ollama handles:**
- Formatting a CSV file
- Summarising a document
- Generating a basic first draft
- Any task where the output just needs to be "good enough"

**Examples of what Claude still handles:**
- Complex reasoning
- Code debugging
- Planning a new system
- Writing that needs to sound good

**Is Ollama right for King David right now?**
Not yet. Reasons:
- Requires technical setup
- Current Claude token spend is not at crisis levels
- The 99% saving only shows up at scale (hundreds of tasks per day)

Revisit when: King David has multiple clients running automations simultaneously and the monthly Claude API bill starts hurting.

### 18 Token Hacks (Apr 2 video)

Key categories to apply immediately:

1. Shorter prompts, Less context sent = fewer tokens burned.
2. CLAUDE.md discipline, Only put active, needed information in CLAUDE.md. Bloated files burn tokens on every session.
3. Context compaction, Use /compact and /clear to reset heavy sessions before they drag.
4. Skip redundant reads, Do not tell Claude to re-read files it already read. Use @filename tagging precisely.
5. Targeted sub-agents, Give sub-agents only the context they need. Do not send the full CLAUDE.md to every sub-agent call.

### Session Limit Management (Apr 20 video)

1. Start heavy tasks early in the session, Do complex builds when the context window is clean.
2. Save before you approach limits, Run /save before a session gets heavy.
3. Use /compact proactively, When a session goes past 100 messages, /compact compresses without losing the thread.
4. Split large tasks across sessions, Do not try to build an entire skill in one session.
5. Use sub-agents for parallel work, Sub-agents run in their own context windows, so they do not eat from the main session's limit.

---

## Section 6: Deployment and Hosting Options

### Clawdbot on VPS (Jan 27 video)
Claude Code running on a cloud server 24/7, even when your laptop is off.
**King David's situation:** Not needed yet. Local + Claude routines is enough for now.

### Scheduled Automations (Apr 14 video) · MOST IMPORTANT
Claude Code now has built-in scheduling called "routines." You set a schedule and Claude Code runs your skill automatically in the cloud, no trigger.dev, no Windows Task Scheduler, no VPS needed.

**Action:** Test Claude routines with the newsletter automation. If reliable, retire Windows Task Scheduler script.

### 3 Deployment Options (May 15 video)

| Option | What It Is | When to Use |
|--------|-----------|-------------|
| Option 1 | Local (your laptop) | Testing, personal use |
| Option 2 | Claude cloud routines | Scheduled tasks, client automations |
| Option 3 | VPS (Clawdbot-style) | Always-on, complex agent teams |

**King David now:** Option 1. Move to Option 2 as soon as Claude routines are tested and confirmed working.

---

## Section 7: What We Skip and Why

| Video | Skip Reason |
|-------|------------|
| Jan 5 · Building RAG Agents in n8n | n8n deprecated in King David's stack |
| Jan 14 · Migrate n8n Workflows | n8n-specific |
| Jan 19 · Generate Proposal Decks with n8n | n8n-specific |
| Jan 22 · Never Fix Another n8n Workflow | n8n-specific |
| Feb 27 · Nano Banana 2 Image Tool | Image tool comparison, not a service King David sells |
| Mar 10 · Google's New Tool | Too technical to apply immediately |
| Mar 11 · Claude Code Plays Tetris | Entertainment, no commercial application |
| Mar 11 · Google Model Changed RAG | Advanced RAG · not a priority yet |
| Mar 26 · Claude Code + iMessage | Apple-only, not part of King David's client offering |
| Mar 28 · Gemini Flash Live Voice | Voice agents are a future service · skip until basics are in place |
| Mar 28 · Claude Code + Paperclip | Competitive comparison, no actionable outcome |
| Apr 1 · Source Code Leaked | News event, not actionable |
| Apr 5 · Andrej Karpathy 10x'd | Advanced technique, not immediately applicable |
| Apr 9 · Stop Using Best Model | Model selection nuance · not urgent |
| Apr 11 · Seedance 2.0 Websites | Upgrade material for later, not urgent |
| Apr 15 · Claude + HeyGen | Video production pipeline · not King David's current service |
| Apr 16 · Opus 4.7 Launch | Model launch news, not actionable |
| Apr 17 · Opus as 24/7 Trader | Trading bot · outside King David's business model |
| Apr 18 · Claude Changed Video Editing | Video editing service · not in lineup |
| Apr 21 · Claude Design 3D Websites | Advanced design · revisit at Month 3+ |
| Apr 22 · OpenAI Image 2 | Not part of King David's tool stack |
| Apr 23 · HyperFrames Video Editing | Video editing · not in lineup |
| Apr 30 · Claude Design Masterclass | Premium design · revisit at Month 3+ |
| May 4 · Building Voice Agents | Future service · needs ElevenLabs setup first |
| May 5 · Higgsfield Creative Agency | Ad creative agency · not King David's focus |
| May 6 · Master Codex | Code tool, not for non-technical service delivery |
| May 9 · Printing Press | Advanced CLI · revisit when more comfortable with deployment |

---

*This document covers all 87 YouTube videos. Skool classroom content is extracted separately and combined in ais_upgrade_plan.md.*
