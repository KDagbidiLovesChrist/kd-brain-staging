---
name: knowledge-patterns
description: Reusable code patterns, workflow patterns, and approaches that have worked in King David's projects. Grows with every session. Queried by /search skill.
---

# Patterns Knowledge Base

This file grows automatically. Every time a pattern works well, it gets logged here.
The /search skill reads this file before answering pattern-related questions.

**How to add:** After a successful build, add an entry using the format below.
**How to query:** Type `/search [what you're looking for]`

---

## FORMAT FOR NEW ENTRIES

```
## [Date] · [Short Title]
**Category:** [Code Pattern / Workflow Pattern / Architecture Pattern]
**Situation:** [what problem was being solved]
**What worked:** [the solution or pattern]
**Code/Template:** [if applicable, include the key code or structure]
**Reuse when:** [what situation would call for this again]
```

---

## EXISTING PATTERNS

### 2026-05-12 · Firecrawl Lead Scraper Pattern
**Category:** Code Pattern
**Situation:** Scraping business directories (Golden Pages, Yelp) for contact info
**What worked:**
- Use `firecrawl_scrape` with `formats: ["markdown"]` to get clean text
- Parse markdown with regex to extract: business name, phone (Irish format: 08X or 01-XXX), email
- Deduplicate on phone number (most reliable unique identifier for tradespeople)
- Export with pandas to CSV + Excel in one pass
**Code:**
```python
# Key extraction pattern for Irish business directories
import re
phone_pattern = r'(?:08[0-9]|01|02[0-9]|04[0-9]|05[0-9]|06[0-9]|07[0-9]|09[0-9])[\s\-]?[0-9]{7,8}'
email_pattern = r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}'
```
**Reuse when:** Any Irish/UK lead scraping job

---

### 2026-05-15 · Newsletter HTML Email Pattern
**Category:** Code Pattern
**Situation:** Generating HTML emails that render correctly in Gmail, Outlook, Apple Mail
**What worked:**
- Use inline CSS (not stylesheets, email clients strip them)
- Table-based layout for maximum compatibility
- Max width 600px, centered
- Font: Arial/Helvetica (safe fonts only)
- Test with a real send before confirming as working
**Key structure:**
```html
<table width="100%" cellpadding="0" cellspacing="0">
  <tr>
    <td align="center">
      <table width="600" cellpadding="0" cellspacing="0">
        <!-- content here -->
      </table>
    </td>
  </tr>
</table>
```
**Reuse when:** Any email automation that sends HTML

---

### 2026-05-15 · Gmail SMTP Authentication Pattern
**Category:** Code Pattern
**Situation:** Sending emails via Python with Gmail
**What worked:**
- Use Gmail App Password (not main password), Settings → Security → 2FA → App Passwords
- Use `smtplib` with TLS: `smtplib.SMTP('smtp.gmail.com', 587)`
- Store credentials in .env, never in code
- Use `ssl.create_default_context()` for the TLS connection
**Reuse when:** Any project that needs to send email via Gmail SMTP

---

### 2026-05-15 · WAT Project Structure Pattern
**Category:** Architecture Pattern
**Situation:** Starting any new automation project
**What worked:**
- CLAUDE.md first (brain before code)
- workflow\ SOP before writing any tools (know the steps before coding them)
- Test each tool individually before building the master runner
- Master runner calls tools in sequence with error handling
- .env for all secrets from day one (never retrofitted)
**Reuse when:** Every new project, this is the standard

---

### 2026-05-15 · Python .env Loading Pattern
**Category:** Code Pattern
**Situation:** Loading API keys from .env files safely
**What worked:**
```python
from dotenv import load_dotenv
import os

load_dotenv()  # loads from .env in current directory

api_key = os.getenv("ANTHROPIC_API_KEY")
if not api_key:
    raise ValueError("ANTHROPIC_API_KEY not found in .env file")
```
**Reuse when:** Every Python script that needs API keys

---

---

### 2026-05-16 · Solution-First Sales Formula (AIS Business Navigation)
**Category:** Workflow Pattern, Client Acquisition
**Situation:** Approaching any business (Irish/UK SMBs, tradespeople, SaaS, PT clients)
**What worked:** Lead with the problem they have, not the technology you use.

**The Formula:**
"I help [business type] save [X hours/week] by automating [specific task].
I've done this for [social proof]. Want me to show you how it works for your business?"

**For Irish tradespeople specifically:**
"I help plumbers/electricians/builders in Dublin stop losing leads.
I build automated systems that follow up with every enquiry instantly.
Want to see how it works?"

**NEVER say:** "I build AI agents" / "I do AI automation" / "I use n8n/Claude"
**ALWAYS say:** The outcome the client gets, not the tool you used to build it.

**Reuse when:** Every client conversation, every Fiverr gig description, every cold email

---

### 2026-05-16 · Value-Based Pricing Formula (AIS Lesson 10)
**Category:** Workflow Pattern, Pricing
**Situation:** Setting prices for any automation service

**The Calculation:**
1. Ask: "How many hours/week does your team spend on [problem]?"
2. Multiply: Hours × hourly cost = weekly cost
3. Multiply by 52 = annual cost of the problem
4. Your price = 10, 20% of the annual cost

**Example for a plumber:**
- Spends 5 hrs/week chasing leads manually
- At €25/hr = €125/week = €6,500/year
- Your automation price: €650, €1,300 (pays for itself in 5, 10 weeks)

**Fiverr pricing (translated):**
- 100 leads → plumber potentially earns €2,000, €5,000 from them
- Your price: €150 starter (7.5% of low-end value) = justified
- Monthly retainer €120 → client keeps getting value every month

**Live worked example (King David's calculation):**
- Client wastes 2 hours/week on manual task
- Their time costs €50/hour
- 2 hrs × 4 weeks = 8 hours/month × €50 = **€400/month wasted**
- Annual cost = €400 × 12 = **€4,800/year**
- Your price: **€300 one-time** → client recoups in under 1 month
- Retainer option: **€120/month** → client still saves €280/month net every month
- Year 1 net saving for client: €4,800 - €300 = **€4,500 profit**

They say yes because the numbers prove themselves. You don't sell. The math sells.

**Reuse when:** Any client pricing conversation, any proposal

---

### 2026-05-16 · ROI Pitch Template (AIS Cold Outreach Script)
**Category:** Workflow Pattern, Outreach
**Situation:** Cold email / DM to any local business

**Template:**
Subject: Saving [Business Name] time on [specific task]

Hi [Name],

I came across your business while researching [trade] in [city].

I help [trade type] stop losing leads by building automated systems that follow up
with every enquiry instantly, so you never lose a customer because you were on a job.

I recently did this for a personal trainer in Dublin and it saved them 3+ hours a week.

Would you be open to a quick 15-minute call to see if something similar works for you?

David

**Discovery call opener:**
"Before I tell you anything about what I do, can you tell me what's taking up the
most time in your business that you wish you could get back?"

**Closing language:**
"Based on what you've told me, I'd build [X] which would [specific outcome].
The investment is [price]. Happy to get started this week, want to move forward?"

**Reuse when:** Any cold outreach, email, DM, Fiverr message, in-person

---

---

### 2026-05-16 · Claude Model Selection Strategy
**Category:** Architecture Pattern, Cost Optimisation
**Situation:** Any time a task is handed to Claude or a sub-agent, pick the right model for the job

**The three models (current as of 2026-05):**
| Model | ID | Speed | Cost | Use For |
|-------|-----|-------|------|---------|
| Haiku 4.5 | `claude-haiku-4-5-20251001` | Fastest | Cheapest | Retrieval, formatting, simple lookups, memory reads |
| Sonnet 4.6 | `claude-sonnet-4-6` | Balanced | Mid | Most tasks · building skills, research, proposals, writing |
| Opus 4.7 | `claude-opus-4-7` | Slowest | Most expensive | Complex reasoning, architecture, high-stakes decisions |

**The rule:** Default to Sonnet. Drop to Haiku for routine/retrieval. Escalate to Opus only when reasoning quality matters.

**In multi-agent teams:**
- Research sub-agents → Haiku (fast, cheap, just retrieving)
- Main synthesis agent → Sonnet (reasoning over findings)
- Architecture / strategy decisions → Opus (when accuracy is critical)

**Claude Agent SDK:** Build agents programmatically using the Anthropic SDK.
Use when you need agents that run outside Claude Code, e.g. scheduled cloud routines,
client-facing automations, or agents embedded in a product.
Skill: `/claude-api` (already available in Claude Code)

**Reuse when:** Any multi-agent build, any cost-optimisation decision, any SDK project

---

### 2026-05-16 · Multi-Agent Consensus Research Pattern
**Category:** Architecture Pattern, Research + Decision Making
**Situation:** Any time the answer is unknown, complex, or needs to be accurate before acting

**The Pattern:**
Don't guess. Don't use one source. Spawn multiple agents in parallel, each searching a different source. Main agent reads all findings and synthesizes the consensus answer.

**Agent split (standard research team):**
| Agent | Source | What It Searches |
|-------|--------|-----------------|
| Agent 1 | Web (Brave Search / WebSearch) | Current best practices, tutorials, docs |
| Agent 2 | AIS Knowledge Base (/search) | What we already know from classroom + YouTube |
| Agent 3 | AIS YouTube database | Nate Herk videos relevant to the problem |

All 3 run at the same time. Main agent waits, reads all 3 responses, finds consensus.
If 2 of 3 agree → that's the answer. If all 3 conflict → flag to King David.

**Why this works:**
- Parallel = faster than sequential (3x speed)
- Multiple sources = catches errors one source would miss
- Consensus = higher confidence before acting
- Cost-efficient: sub-agents use minimal tokens on focused searches

**When to use:**
- Hitting a technical blocker not already in patterns.md
- Evaluating a new tool or API before installing
- Deciding between two approaches (e.g., Hermes vs direct Claude)
- Any time accuracy matters before building something

**Reuse when:** Unknown problem, technical decision, tool evaluation, approach comparison

---

## 2026-05-23 · Prompt Caching for Claude Code Session Limits
**Category:** Workflow Pattern / Cost Optimisation
**Situation:** Claude Code sessions on Opus 4.7 with `effortLevel: max` burn tokens fast. Default behaviour resets the prompt cache more often than necessary, blowing through session limits prematurely.
**What worked (per Nate Herk's video, 2026-05-21):** Prompt caching can save Claude Code 300M+ tokens per week automatically when handled correctly. The 80/20:
- **Cache HITS** are nearly free (10% of normal token cost). The expensive part is the initial cache WRITE.
- Habits that PROTECT the cache (keep hits coming): keep the system prompt / CLAUDE.md / loaded skills stable within a session; avoid bouncing between projects mid-session.
- Habits that QUIETLY RESET the cache (avoid): editing CLAUDE.md mid-session, switching settings.json mid-session, clearing and re-loading large files, /clear without /save first.
- Companion tool: Nate's free **Token Dashboard** at `https://github.com/nateherkai/token-dashboard`, visualises token consumption + cache hit/miss rates per session. See `AIS_Audit\audit_log\to_install.md` for install plan.
**Code/Template:** *Specific habit list to be extracted by watching the actual video, this entry is a stub from the post description only. Full habits TODO when video watched.*
**Reuse when:** Daily Claude Code work, especially on Opus 4.7 + max effort. Anyone hitting session limits before completing a project task.
**Source:** https://www.skool.com/ai-automation-society/new-video-the-one-habit-that-doubles-your-claude-code-session-limit
**Status:** STUB, full extraction pending. King David's call whether to watch the video and complete this entry, and whether to install the Token Dashboard repo.

---

*New patterns added by /save after each session where a new pattern is discovered.*
