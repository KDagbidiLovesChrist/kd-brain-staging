# AIS Classroom Master · All Extracted Resources
**Hard limit:** 300 lines | **Last updated:** 2026-06-21
**Sub-files:** ais_pdfs.md · ais_json_configs.md · ais_workflows.md

---

## TRANSCRIPT LIBRARY (full lesson transcripts)
- **Location:** `knowledge\ais_resources\transcripts\`, **128 transcripts** (Claude Code course
  P1, P4, Build Portfolio + Agent Zero, 10-hr course, Business Talks, TrueHorizon $211k deal,
  community/membership videos).
- **Backlog status (2026-06-21):** harvested classroom drained, `loom_full_extraction.tsv` =
  **104 done / 1 pending**; the 1 "pending" is a known fathom dedup false-positive (already on disk).
- **Latest add, 2026-06-21:** `ais_backlog_drain_2026-06-21.md`, the final 7 community/membership
  videos summarised. 💰 highlights: post a **"Gem"** = $20 + visibility · **539-tool discount vault**
  (annual perk: Bolt.new 1yr free, Notion 6mo free…) · AIS+ pricing is **grandfathered** (don't
  casually cancel).
- **🔥 NEW MODULE, 2026-06-21:** **"Get Your First Clients"** (17 lessons, Nate's newly-unlocked
  module). Captured + transcribed (`transcripts/loom_FIRSTCLIENTS_01..17_*.md`) + a grounded 18-agent
  breakdown. **READ FIRST: `first_clients_MASTER_breakdown_2026-06-21.md`** (through-line, system in
  order, scripts to steal, numbers cheat-sheet, King's 5-move action plan). Per-lesson detail:
  `first_clients_lessons_{01-06,07-12,13-17}_2026-06-21.md`. Core thesis = **get ONE piece of proof
  (free first project → case study), warm outreach FIRST then Upwork, win on volume (Rule of 100), and
  the tailored Loom is the #1 differentiator.**
- **🔥 MODULE, 2026-06-21:** **"The AI Partner Model"** (6 lessons). Captured + transcribed
  (`transcripts/loom_AIPARTNER_*.md`) + grounded breakdown. **`ai_partner_MASTER_breakdown_2026-06-21.md`**
  + `ai_partner_lessons_breakdown_2026-06-21.md`. Core thesis = **don't sell chatbots/builds, become the
  "AI Transformation Partner" who finds where AI makes a business more money** (3 ways: more revenue,
  upsell, cut cost) → **price on value, take a monthly retainer.** Math: $3-5k/mo retainers, ~25% of
  project clients upgrade to retainer, 1-2 retainers = $5k/mo. (Stats are Nate's US-agency claims, not
  King's results.)
- **🔥 MODULE (relevant subset), 2026-06-21:** **"Build Your Portfolio"**, 49 lessons, ALL already on
  disk; broke down the 12 relevant ones (portfolio/positioning 1-5 + paid business discovery 6-12) →
  **`build_portfolio_relevant_breakdown_2026-06-21.md`** + 2 per-lesson files. Skipped 37 technical/
  personal/build lessons (proven reason). Core = **proof beats knowledge (3-5 real builds = past 90%),
  no niche yet, lead with "here's one I built"; then the paid Opportunity-Map discovery (Time/Income
  lens → SOP audit → Business ICE → live Blueprint).**
- **📑 FULL-CLASSROOM SWEEP:** `ais_classroom_module_status_2026-06-21.md`, every module's relevance
  decision. Done = First Clients + AI Partner + Build Portfolio(relevant). Skipped w/ reason = Claude
  Code (technical, already distilled), Start Here / Member Perks / Community / Archived (admin), Live
  Call Recordings (118 calls, not pipeline-accessible). Locked = Scale.

---

## WHAT WAS FOUND IN THE CLASSROOM

| Source | Type | Content | File |
|--------|------|---------|------|
| Lesson 1.4 (Skool) | PDF | n8n MCP setup checklist | ais_pdfs.md |
| GitHub czlonkowski/n8n-mcp | JSON/.env | Full env template + Docker env | ais_json_configs.md |
| GitHub czlonkowski/n8n-mcp | Config | Claude Code settings.json block | ais_json_configs.md |
| GitHub czlonkowski/n8n-mcp | Prompt | CLAUDE.md rules for n8n workflows | ais_json_configs.md |
| Lessons 2.1-2.3 (Skool) | Workflow | Email agent + indexer patterns | ais_workflows.md |
| Lesson 3.1 (Skool) | Framework | Enhancement philosophy (error/quality/UX) | ais_workflows.md |

**What was NOT found:** Downloadable JSON workflow files in the classroom, lessons are video-only. The JSON configs live in GitHub.

---

## TOP 5 THINGS TO APPLY NOW

**1. Add n8n-mcp to Claude Code** (takes 2 minutes)
Add to `C:\Users\Dell\.claude\settings.json`:
```json
"n8n-mcp": { "command": "npx", "args": ["n8n-mcp"] }
```

**2. Fill the .env for n8n integration**
Need: `N8N_API_URL` + `N8N_API_KEY` (from n8n Settings → API)
Templates in: `ais_json_configs.md`

**3. Use n8n-mcp's 2,352 templates before building any workflow**
Hosted free: dashboard.n8n-mcp.com (100 calls/day)
Command: `npx n8n-mcp`

**4. Apply Enhancement Philosophy to every existing skill**
Order: error handling → output quality → user experience

**5. Use Vibe Coding for all builds**
Describe OUTCOME not CODE, Claude plans, you approve, Claude builds

---

## KEY NUMBERS TO REMEMBER

| Metric | Value |
|--------|-------|
| n8n nodes documented | 1,650 |
| n8n workflow templates | 2,352 |
| GitHub stars | 21k |
| Free tier (hosted) | 100 calls/day |
| Node.js required | Yes (LTS from nodejs.org) |
| n8n paid plan required | Yes (for API key) |

---

## ECOSYSTEM MAPPING · HOW THIS CONNECTS

```
AIS Classroom Resources
        |
        ↓
n8n-mcp (GitHub) ──→ Claude Code settings.json ──→ /n8n skill (build next)
        |
        ↓
2,352 templates ──→ query before building any workflow
        |
        ↓
.env template ──→ C:\Users\Dell\.env.master ──→ N8N_API_URL + N8N_API_KEY
        |
        ↓
Workflow patterns ──→ upgrade /scrape, /newsletter, /website
```

---

## QUICK KEYWORD TRIGGERS (for /ais skill)
- `/ais setup` → Show n8n-mcp installation steps
- `/ais env` → Show the .env template
- `/ais config` → Show Claude Code settings.json block
- `/ais workflow` → Show workflow translation patterns
- `/ais enhance` → Show Enhancement Philosophy checklist
- `/ais numbers` → Show key metrics table
- `/ais map` → Show ecosystem mapping diagram
