---
name: feedback-use-subagents
description: Always use subagents/multi-agents when it improves efficiency, and explain when and why each time
metadata: 
  node_type: memory
  type: feedback
  originSessionId: e121412d-5c8e-4a05-b37b-541a617c7179
---

Use subagents proactively whenever they improve speed, quality, or scale. Do not wait to be asked.

**Why:** King David confirmed on 2026-05-16, he wants Claude to use multi-agents automatically and to narrate the moment when they are being used, so he learns by seeing it happen in real work, not just theory.

**How to apply:**
- When spawning a subagent, say so in one line: what it is doing and why it's faster/better than doing it alone
- Highlight the moment clearly, e.g. "Spinning up a parallel agent to do X at the same time as Y, this saves time because..."
- Common triggers for subagents in King David's workflow:
  - Scraping multiple cities at once → parallel scraper agents
  - Researching + writing at the same time → one agent researches while main agent writes
  - Large codebase exploration → Explore agent so main context stays clean
  - Any task with 3+ independent steps that don't need each other's output first
- Always explain WHY it was the right call at that moment, King David learns by watching, not by reading theory
