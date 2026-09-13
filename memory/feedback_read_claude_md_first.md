---
name: feedback-read-claude-md-first
description: "Always read CLAUDE.md before starting any task, it defines the agent's identity and operating framework (WAT)"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: d5c2adf0-7ced-479d-91cd-5d182caaf15f
---

Always read `CLAUDE.md` at the start of every task before planning or executing anything.

**Why:** The user explicitly requires this. CLAUDE.md defines the WAT framework (Workflows, Agents, Tools) which is the agent's identity and operating context. Every task must be framed within that architecture.

**How to apply:** First tool call of any new task = `Read c:\Users\Dell\Documents\Newsletter Demos\CLAUDE.md`. Then plan/act within the WAT structure: check `tools/` for existing scripts, reference `workflows/` for SOPs, use `.env` for credentials.
