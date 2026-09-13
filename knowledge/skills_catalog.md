---
name: skills-catalog
description: Full service catalog, every skill King David can offer a client, what it solves, and what it costs. Read by /search when a client asks "can you do X?"
---

# Skills Catalog · King David's Service Library

When a client asks "can you do X?", Claude reads this file first.
Match their problem to a skill. If no match, check if it can be built in 1, 2 hours.

**The rule:** Every skill = a product on a shelf. Check the shelf before building anything new.

---

## HOW TO USE THIS CATALOG

1. Client describes their problem
2. Match to a skill below (exact or closest)
3. If match found → run the skill, show them the output
4. If no match → can it be built in 1, 2 hours? If yes, quote custom build price
5. Generate proposal using the ROI pitch formula from knowledge\patterns.md

---

## LIVE SKILLS · Available Right Now

### /scrape · Lead Generation
**Problem it solves:** "I'm not getting enough customers / leads"
**What it delivers:** 100, 300 verified local business leads (name, phone, email, address) as CSV
**Pricing:**
- Starter: €150, 100 leads, one city, delivered in 24 hours
- Growth: €250, 300 leads, any city, verified + sorted
- Retainer: €120/month, 100 fresh leads every month, automated
**Best for:** Plumbers, electricians, cleaners, landscapers, solicitors, any Irish/UK trade
**Demo:** Run /scrape → show them a sample of 10 leads from their city

---

### /newsletter · Email Automation
**Problem it solves:** "I'm not staying in touch with my customers / losing repeat business"
**What it delivers:** Researched, written, and sent newsletter on any topic to any list
**Pricing:** €50, 200/month per client (recurring)
**Best for:** Any business with a customer list, trades, consultancies, gyms, clinics
**Demo:** Run /newsletter on their niche → show them a finished HTML email
**Blocker:** Needs Perplexity API key + Gmail App Password to go live

---

### /website · Website Builder
**Problem it solves:** "I don't have a website / my website is outdated"
**What it delivers:** Full HTML/CSS/JS website, live URL via Vercel
**Pricing:** €300, 2,500 per site · €100, 300/month maintenance
**Best for:** Any business without a professional web presence
**Demo:** Build a sample page in 30 minutes, show them the live URL
**Blocker:** Needs Vercel account to deploy

---

### /exec · Executive Assistant
**Problem it solves:** "I'm overwhelmed / I can't keep track of everything"
**What it delivers:** Daily briefing across Faith, Finances, Health, Work, Projects, 5 parallel agents
**Pricing:** Internal use only (not sold as a service yet)
**Note:** Foundation for building and selling Claude Code OS systems to clients (/os-builder)

---

### /browser · Browser Automation
**Problem it solves:** "I spend hours on repetitive web tasks"
**What it delivers:** Automates any browser task, form filling, data extraction, clicking, navigating
**Pricing:** Custom quote based on task complexity (€200, 1,000 setup + retainer)
**Best for:** Any business with repetitive web-based admin work
**Demo:** Record their repetitive task, show it automated

---

### /monetize · Client Discovery
**Problem it solves:** Internal, helps us find and close clients
**What it delivers:** Discovery → ROI calculation → proposal → expansion playbook
**Pricing:** Internal use

---

## PLANNED SKILLS · Building After First Client

### /proposal · Client Proposal Generator
**Problem it solves:** Speeds up closing deals
**What it delivers:** 1-page tailored proposal: problem, solution, ROI, price, timeline
**ETA:** After first paying client (test with PT engagement first)

---

### /cold-email · Outreach Automation
**Problem it solves:** Need to reach businesses at scale
**What it delivers:** Personalised cold email/DM for any business type using the Solution-First Formula
**ETA:** Alongside /proposal

---

### /content · Social Content Autopilot
**Problem it solves:** "I don't have time to post on social media"
**What it delivers:** Content for 9 social platforms from one brief, monthly retainer
**Pricing:** €100, 300/month
**ETA:** After first paying client
**Source:** Mar 17, 2026 Nate Herk video

---

### /os-builder · Claude OS for Clients
**Problem it solves:** Businesses want AI but don't know how to set it up
**What it delivers:** Full Claude Code Operating System built for a client (memory + mechanics + monetisation)
**Pricing:** €1,000, 5,000 setup + monthly maintenance
**ETA:** After income starts, high-value play
**Source:** May 1, 2026 video, Three Ms framework

---

### /studynotes · Obsidian Bridge
**Problem it solves:** Session knowledge gets lost between conversations
**What it delivers:** Auto-sends structured notes to Obsidian vault with audit log
**ETA:** After Obsidian is installed (30 min setup, free)

---

### /agent-team · Multi-Agent Coordinator
**Problem it solves:** Complex tasks that need multiple agents running in parallel
**What it delivers:** Launches a coordinated team of agents from one command
**ETA:** This session (prerequisite: /exec multi-agent already done)

---

### /voice-agent · Lead Qualification Bot
**Problem it solves:** "I can't call every enquiry back fast enough"
**What it delivers:** Voice bot that calls and qualifies every new lead automatically
**Pricing:** €200, 500 setup + retainer
**ETA:** Future, ElevenLabs + Cal.com integration needed
**Source:** Jan 12, 2026 Nate Herk video

---

## CLIENT MATCH TABLE (Quick Reference)

| Client Says | Match Skill | Quote |
|-------------|-------------|-------|
| "I need more leads" | /scrape | €150-250 + €120/mo |
| "I need a website" | /website | €300-2,500 |
| "I need to reach my customers" | /newsletter | €50-200/mo |
| "I waste hours on the same tasks" | /browser | Custom €200-1,000 |
| "I need content for social media" | /content | €100-300/mo |
| "Can you do all of the above?" | Combined package | €500-1,500 + retainer |
| "We need a full AI system" | /os-builder | €1,000-5,000 + maintenance |
| Custom request | Build it | 10-20% of annual savings to client |

---

## WHEN YOU DON'T KNOW HOW TO DO SOMETHING

If a client asks for something not in this catalog, use the **Multi-Agent Consensus** approach:

### Step 1 · Launch 3 Research Agents in Parallel
Don't guess. Send agents to different sources simultaneously:

| Agent | Where It Searches | What It Looks For |
|-------|------------------|-------------------|
| Agent 1 | Web (Brave Search / WebSearch) | Best current approach, docs, tutorials |
| Agent 2 | AIS knowledge base (`/search`) | What we already know internally |
| Agent 3 | AIS YouTube database | Nate Herk video covering this problem |

All 3 run at the same time. Main agent synthesizes consensus from all findings.
**If 2 of 3 agree → that's the answer. If all 3 conflict → flag to King David.**

### Step 2 · Build an MVP
Minimum version that proves it works, 1, 2 hours max.
Not perfect. Just enough to demonstrate the outcome to the client.

### Step 3 · Demo It
Show the client the output, not the code or the process.
"Here's what I built. Here's what it does for your business."

### Step 4 · Document It
Add the working pattern to `knowledge\patterns.md`.
Permanent inventory, next time anyone asks, the answer is already there.

### Step 5 · Scale It
MVP → tested skill → portfolio proof → priced service in the catalog above.

**The loop:** Search (consensus) → MVP → Demo → Document → Scale.
Every unknown becomes a known. Every problem solved once = solved forever.

---

## THE PITCH (memorise this)

"I help [business type] save [X hours/week] by automating [specific task].
I've done this for [social proof]. Want me to show you how it works for your business?"

For Irish tradespeople:
"I help plumbers in Dublin stop losing leads. I build automated systems that follow up with
every enquiry instantly. Want to see how it works?"
