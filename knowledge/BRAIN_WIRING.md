# Brain wiring: RAG · Memory · File Pipeline · Setup guides (moved from CLAUDE.md 2026-07-04 reorg)

## RAG Knowledge Base (Grows Over Time)
- **Location:** `C:\Users\Dell\.claude\knowledge\`
- `patterns.md`, code patterns that worked (scraping, email, auth, WAT)
- `clients.md`, client tracking template (Fiverr buyers, paid clients)
- `tools_learned.md`, notes on every API, tool, MCP used
- **How it works:** `/search` reads these files before answering, Claude gets smarter with every session

---

## Memory System
- **Location:** `C:\Users\Dell\.claude\memory\`
- **Index:** `MEMORY.md`, read at the start of every session
- **Reference files:** tokens, commands, APIs, MCPs, sub-agents, agent teams, GitHub, Google, fun hacks, project template

---

## File System Pipeline
```
MASTER BRAIN (this file)
          |
    ______|_______________________________________
    |         |          |          |            |
brand_    memory\    knowledge\  commands\   DCEO_BRAIN\
assets\  (who I am)  (RAG base) (54 skills)  (work brain)
    |
    ↓ read by all projects


WAT PIPELINE (every idea becomes money):
==========================================

  You describe a goal
        |
        ↓
  Workflow, markdown SOP (the steps, the rules)
        |
        ↓
  Agent, Claude reads SOP, reasons, decides
        |
        ↓
  Tool, Python / MCP / API (does the actual work)
        |
        ↓
  Skill, /command (one word triggers everything)
        |
        ↓
      MONEY


PROJECTS (each has its own CLAUDE.md + WAT chain):
====================================================

  Newsletter Demos\       Scrapers - Copy\      Website Builder\       CV Tailor\
  ─────────────────       ────────────────      ────────────────       ──────────
  /newsletter skill       /scrape skill         /website skill         /cv-tailor skill
  Perplexity research     Firecrawl scrape      HTML/CSS build         4-agent pipeline
  Gmail sends email       /browser fallback     Vercel deploys         anti-AI tone QA
  Any topic, any niche    Fiverr €25, €90        €300, €2,500/site       €20, 50/CV resale


WORK BRAIN (Orcha, separate from personal):
==============================================

  DCEO_BRAIN\ (7 agents)
  ├── email\, triage, categorise, respond
  ├── operations\, briefings, handovers
  ├── risk\, risk assessment, ticket routing
  ├── admin\, calendar, file management
  └── knowledge\, grows with every task (auto)
  Runs on AWS Bedrock, Amazon pays all costs


MEMORY SAVE PIPELINE:
======================

  Session ends → /save fires
        |
        ↓ routes to:
  memory\ → user prefs, project status, rules
  knowledge\ → patterns, client notes, tools
  CLAUDE.md → badge updates, new projects
  handoffs\ → full session snapshot
        |
        ↓
  Next session → /recover → full briefing, ready
```

---

## External Setup Guides (When Ready)
| Tool | Guide Location |
|------|---------------|
| Brain bootstrap (clone → working) | `knowledge\BRAIN_BOOTSTRAP.md` |
| GitHub + git | `memory\reference_github_worktrees.md` |
| Vercel deployment | `memory\reference_mcps.md` + `/deploy` skill |
| trigger.dev scheduling | `commands\deploy.md` |
| Google CLI (Gmail API) | `memory\reference_google_cli.md` |
| Perplexity API key | Get from perplexity.ai/settings/api → add to .env |
| Brave Search MCP | `memory\reference_mcps.md` |

## Pipeline Reference
- **Full map:** `C:\Users\Dell\.claude\PIPELINE.md`

## File Size Rule
- **Hard limit:** 500 lines per file, no exceptions
- Use `/context` to scan and fix files approaching the limit
