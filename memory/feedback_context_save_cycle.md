---
name: feedback-context-save-cycle
description: "When context feels heavy or long, proactively suggest /save → /clear → /recover before it becomes critical"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: e121412d-5c8e-4a05-b37b-541a617c7179
---

When a session is running long and context is getting heavy, proactively flag it and suggest the save/clear/recover cycle. Don't wait for King David to notice.

**Why:** King David asked (2026-05-16) for automatic save/clear/recover at 70% context. This can't be automated via hooks (no context % event exists, and /save /clear /recover are Claude commands not shell scripts). The closest equivalent is proactive flagging.

**How to apply:**
- When conversation feels very long (many tool calls, long outputs, lots of back and forth), say: "Context is getting heavy, want me to /save, /clear, and /recover so we stay sharp?"
- Always run /save BEFORE suggesting /clear, never clear without saving first
- After /recover, continue the exact task from where we left off
- The Stop hook (auto_handoff.py) already auto-saves on session end, so nothing is ever fully lost
- Claude Code's built-in compaction also handles overflow automatically
