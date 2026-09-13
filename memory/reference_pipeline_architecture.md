---
name: reference-pipeline-architecture
description: The 7-layer master pipeline architecture, settings.json → CLAUDE.md → memory → skills → tools → archive → projects
metadata: 
  node_type: memory
  type: reference
  originSessionId: 80bb2fcd-5412-4b21-9e36-4ac380ab9d24
---

# Master Pipeline Architecture

**Full visual map lives at:** `C:\Users\Dell\.claude\PIPELINE.md`

## The 7 Layers

| Layer | What | Where |
|---|---|---|
| 0 | THE GATE · permissions, hooks, MCP servers | `settings.json` |
| 1 | MASTER BRAIN · who King David is, all projects | `CLAUDE.md` |
| 2 | LONG-TERM MEMORY · preferences, rules, project history | `memory\` |
| 3 | SKILLS LIBRARY · completed projects promoted to triggers | `commands\` |
| 4 | AUTO TOOLS · fire without being asked | `tools\` |
| 5 | SESSION ARCHIVE · global + per-project copies | `handoffs\` + `sessions\` |
| 6 | MONEY MACHINES · active project folders | `Documents\*` + `DCEO_BRAIN\` |

## Project Lifecycle
```
IDEA → BUILD (Layer 6) → PROVEN → PROMOTED TO SKILL (Layer 3) → RUNS FOREVER
```

## Standard WAT Template (every project must match)
```
[Project]\
├── CLAUDE.md      ← brain
├── .env           ← API keys
├── sessions\      ← session history
├── .tmp\          ← throwaway output
├── workflow\      ← W: SOPs
├── tools\         ← T: Python scripts
└── commands\      ← S: skill (optional, or use global)
```

## Current Skills in Layer 3 (commands\)
- /save, /recover, /handoff, /context, brain skills
- /newsletter, Newsletter Demos project
- /scrape, Lead Gen Scraper project

## Sessions Save Flow
- auto_handoff.py → global `handoffs\` (always, automatic)
- /save → global `handoffs\` + project `sessions\` (manual, end of session)

**Why:** Per-project sessions\ means you can open any project folder and find every conversation ever had about it, no digging through 130+ global handoffs.
