# Subagent Registry · The Standing Army

> ⚡ **2026-07-04 upgrade (gap A2):** the army is becoming REAL `.claude/agents/` definitions in `agents/` (repo root = `.claude` on the laptop). Live so far: **scout** (haiku, cheap research) · **writer** (sonnet, King's voice) · **qa-verifier** (adversarial /qa-master) · **accountant** (haiku, /money lens) · **memory-keeper** (sonnet, /save routing). Claude auto-dispatches these by description; the rest of the 12 migrate as they prove needed. This prose registry stays as the doctrine doc.


**Trigger:** Read by orchestrator before every task. Read by any agent that needs to delegate.
**Environment:** All agents share ONE environment, same local files, same knowledge base, same WAT framework.
**Active queue:** Obsidian vault (port 27124) captures learnings as agents work.

---

## Shared Environment (all agents inherit this)
```
C:\Users\Dell\.claude\
├── CLAUDE.md              ← identity, rules, active projects
├── memory\                ← persistent context across sessions
├── knowledge\             ← RAG files, AIS learnings, patterns, clients
├── commands\              ← all skill SOPs (this file lives here)
├── brand_assets\          ← tone, colors, copy
└── master_prompt.md       ← architect file, read before any client task
```
Obsidian vault → active queue for session notes and learnings (REST API, port 27124)

---

## Standard Handoff (every agent returns this)
```
Agent: [name]
Task: [what was requested]
Output: [the result]
Status: success | partial | failed
Cost: [tokens in / tokens out · model] (added 3 Sep 2026, ruling 33: build time has a ceiling too; the per sitting ceiling and the monthly envelope live in tools/logos_lanes.py)
Next: [recommended next step or agent]
```

---

## The Standing Army

> **Status column (added 2026-08-07):** LIVE / PARTIAL / BROKEN / DORMANT, borrowed from Klarnow's own audit language (Goodness Dada). This is a **different axis from the Tier Ledger** (`_ops/SKILL_TIER_LEDGER.md`), Tier measures trust *earned over time*; Status measures whether it *works right now*. A T4 skill can still show BROKEN if something regressed. Status is a manual, point-in-time read (dated per row), refreshed whenever it's touched or at `/save`, not a live monitor. Don't trust an old date without re-checking.

| Agent | Skill | Tool | Fire When | Status |
|-------|-------|------|-----------|--------|
| **Scraper** | `/scrape` | Firecrawl MCP | Need leads, data, or prices from any website | 🟢 LIVE (2026-08-07, MCP connected + used this session) |
| **Browser** | `/browser` | Playwright MCP | Need to click, fill forms, screenshot, or post to a web platform | 🟢 LIVE (2026-08-07, MCP connected this session) |
| **Writer** | `/content` `/proposal` `/cold-email` | Anthropic API | Need copy, proposals, emails, posts, or SOPs written | 🟢 LIVE (always available, Claude itself) |
| **Researcher** | `/research` | Perplexity API | Need deep web research, market intel, facts | 🟢 LIVE (2026-08-07, per `knowledge/TOOLS_CONNECTED.md` ready-free list; not freshly re-tested this session) |
| **Memory** | `/learn` + `/search` | the `.claude` vault (direct files) | Need to save or retrieve from the knowledge vault (`/studynotes` retired 2026-07-02) | 🟢 LIVE (direct file access, no external dependency) |
| **Newsletter** | `/newsletter` | Perplexity + Gmail SMTP | Research any topic → write → send as HTML email | 🟡 PARTIAL (2026-08-01, research half works; the SMTP app-password send path is BROKEN, use the OAuth `token.json` path instead per `memory/project_connect_everything.md`) |
| **Publisher** | `/skool-post` | Playwright + Skool | Post to AIS Skool community | ⚪ DORMANT (2026-08-07, confirmed cause: no Skool browser profile ever existed, and `browser_door.py` had no "skool" entry, both true gaps, not staleness. The site entry is now added; still needs King: `python tools/browser_door.py login skool`) |
| **Builder** | `/website` | Anthropic + Vercel CLI | Build and deploy a client website from templates | 🟢 LIVE (2026-08-07, Website Sales Engine active, 146 demos) |
| **Drive** | internal | Google Drive MCP | Upload, organise, or share files | 🟢 LIVE (2026-08-07, King re-ran `google_auth.py`; all 5 scopes confirmed in `token.json` AND a real Drive API call succeeded, returning actual files. Still needs, separately: flip the OAuth consent screen to "In production" in Google Cloud Console, or this regresses again in 7 days like it has twice before) |
| **Exec** | `/exec` | 5 parallel sub-agents | Morning briefing · faith, finances, health, work, projects | 🟢 LIVE (2026-08-07, verified: all 5 dependency memory files exist and are populated, `project_income_targets.md`, `project_dceo_work_ai.md`, `project_upcoming_tasks.md`, CLAUDE.md. Never broken, just not recently fired) |
| **Lead** | `/monetize` | Firecrawl + Writer + Playwright | Discovery → ROI case → proposal → close | 🟢 LIVE (2026-08-07, shares live Website Sales Engine infra) |
| **Accountant** | `/money` | Statement tools + ledger (`Documents\finances\`) | Any money decision · gate a spend, review where it's going, track the loan + Dec review, grow it. Advisory only · never touches the bank. | 🟢 LIVE (2026-08-07, July plan locked, active) |
| **Ingest** | internal (24/7 P1) | `tools\daily_ingest.py` + headless claude | Fires itself 07:30 daily · files `inbox\` + refreshes the phone feed. Pings King only on failure. | 🟢 LIVE (24/7 Engine confirmed live) |
| **Nightly** | internal (24/7 P1) | `tools\nightly_review.py` | Fires itself 02:00 daily · writes the nightly truth page + refreshes the living face. | 🟢 LIVE (24/7 Engine confirmed live) |
| **Auditor** | internal (24/7 P1) | `tools\weekly_audit.py` + Gmail | Fires itself Sat 08:00 · week report + humanised email to King's inboxes. | 🟢 LIVE (24/7 Engine confirmed live) |
| **Radar** | internal (24/7 P2) | `tools\revenue_radar.py` + headless claude | Fires itself daily · proposes money moves with numbers into `_ops\REVENUE_QUEUE.md`. King approves or kills; nothing outward without him. | 🟢 LIVE (24/7 Engine confirmed live) |
| **Aide** | `/aide` | the whole brain (reads live state) | King opens any door and says `/aide` · his personal AI: God-first greeting, the one next faithful move, takes his short words (approve #N · script X/10 · rest). Prep-only hands; everything outward asks first. | 🟢 LIVE (2026-08-07, Voice Aide QA passed) |

---

## Money-First Priority
When multiple agents could handle a task, prefer the one that generates income fastest:
```
/scrape → /newsletter → /website → /monetize → /cold-email → /proposal
```

---

## Faith Filter (all agents apply this before any output)
Off-limits: gambling, alcohol, adult content, deception, fake reviews, scams.
Eastern Orthodox values apply to every client and every deliverable. No exceptions.
