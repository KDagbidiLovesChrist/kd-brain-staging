# King David AI Ecosystem · The Whole Restaurant

*Last updated: 2026-05-17*

---

```
═══════════════════════════════════════════════════════════════════
  KING DAVID AI ECOSYSTEM, THE WHOLE RESTAURANT
═══════════════════════════════════════════════════════════════════

  FRONT OF HOUSE  (what King David + clients trigger)
  ───────────────────────────────────────────────────
  /scrape      /newsletter   /website    /browser    /exec
  /research    /content      /proposal   /cold-email /agent-team
  /orchestrate /search       /save       /recover    /context
  /skool-post  /studynotes   /monetize

                        ↕  WAT handoff layer  ↕
         Workflow → Agent → Tool → Skill → MONEY

  THE KITCHEN  (agents working in the shared background environment)
  ───────────────────────────────────────────────────────────────────
  ┌──────────────────────────────────────────────────────────────┐
  │         ORCHESTRATOR  (Head Chef, reads master_prompt.md)   │
  │   reads subagent_registry.md → dispatches → merges → delivers│
  └────┬──────────┬──────────┬──────────┬──────────┬────────────┘
       │          │          │          │          │
  Scraper      Writer     Browser  Researcher  Memory
  Agent        Agent      Agent    Agent       Agent
 (Firecrawl) (Claude)  (Playwright)(Perplexity)(Obsidian)
       │          │          │          │          │
     leads    content      data     research   vault read/write
       └──────────┴──────────┴──────────┴──────────┘
                                 ↓
                    + Publisher · Builder · Drive · Exec · Lead agents
                                 ↓
                    SHARED ENVIRONMENT (one host, all agents inherit)
                    ├── CLAUDE.md  ├── memory\  ├── knowledge\
                    ├── commands\  ├── brand_assets\  └── handoffs\

  THE PANTRY  (tools + APIs powering the kitchen)
  ───────────────────────────────────────────────────
  ✅ Firecrawl MCP          ✅ Playwright MCP
  ✅ Anthropic API           ✅ Gmail SMTP
  ✅ Claude Agent SDK        ✅ Scheduled Automations
  ✅ Google Drive MCP        ✅ Obsidian REST API (port 27124)
  ⏳ Perplexity API key     ⏳ GitHub account
  ⏳ Vercel CLI              ⏳ Brave Search key
  ⏳ Gmail App Password      ⏳ Hermes (AIS community install TBD)

  THE DINING ROOM  (income outcomes)
  ───────────────────────────────────────────────────
  Lead gen scraper     →  €25, 90 per delivery  (Fiverr, ready to publish)
  Newsletter service   →  €50, 200/month        (per business client)
  Website builder      →  €300, 2,500 per site  (needs Vercel account)
  AI consultancy       →  €500, 15,000/project  (dtransform pipeline)
  Retainer             →  €500, 2,000/month     (ongoing management)
  AI for Dummies       →  B2C video/course     (after first income flowing)

═══════════════════════════════════════════════════════════════════
```

---

## Environment Architecture

```
LOCAL FILES (main branch, source of truth)
C:\Users\Dell\.claude\
├── CLAUDE.md              Master brain, identity, rules, projects
├── memory\                Persistent context across sessions
│   ├── MEMORY.md          Index of all memories
│   └── [topic].md         Individual memory files
├── knowledge\             RAG knowledge base
│   ├── ais_all_learnings.md
│   ├── ais_business_navigation.md
│   ├── ais_claude_obsidian_hermes.md
│   ├── patterns.md
│   ├── clients.md
│   ├── tools_learned.md
│   └── ecosystem_architecture.md  ← this file
│   (niche_plumbers_dublin.md → moved to _archive\ 2026-07-04, niche pivoted away)
├── commands\              All skill SOPs (WAT workflows)
│   ├── master_prompt.md   Architect file, shared agent brain
│   ├── subagent_registry.md  Standing army registry
│   ├── orchestrate.md     Head Chef SOP
│   └── [skill].md         Individual skill files
├── brand_assets\          Brand guidelines + bio copy
├── handoffs\              Session saves + recovery packets
└── plans\                 Approved implementation plans

OBSIDIAN VAULT (active queue, living knowledge)
REST API: localhost:27124 (SSL bypass)
Skill: /studynotes
Role: session learnings, client notes, project tracking
Written to by: Memory Agent after every task
```

---

## The WAT Chain (how every problem becomes money)

```
Goal described
     ↓
Workflow  →  markdown SOP in commands\
     ↓
Agent     →  Orchestrator reads registry, picks agents, dispatches
     ↓
Tool      →  MCP / API executes (Firecrawl, Playwright, Claude, etc.)
     ↓
Skill     →  /command triggers the whole chain in one word
     ↓
   MONEY
```

---

## Four Delivery Metrics

| Metric | Standard |
|--------|----------|
| Less time | Faster than manual · parallel agents win |
| More money | Every output is billable or income-generating |
| Better quality | Multi-agent beats single-agent on the same brief |
| WOW factor | Someone cold sees it and says "wow, okay" · if not, redo it |
