---
name: feedback-cross-laptop-sync
description: Pattern for continuing sessions from home laptop to work laptop via OneDrive
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 10991ce9-e5d9-4a6d-8073-57229751c58d
---

Only copy the handoff to OneDrive when the next session will specifically be DCEO/work tasks.

**Rule:**
- DCEO work session continuing on work laptop → copy handoff to `OneDrive\DCEO_Brain\context\RESUME_HERE.md`
- Personal session (Fiverr, newsletter, websites, finances) continuing on work laptop → DO NOT copy to OneDrive DCEO_Brain. Personal context stays personal.

**Why:** Work OneDrive is an Amazon-connected environment. Personal business (Fiverr income, clients, personal finances) must never appear there. The DCEO_SKILLS privacy wall already separates work from personal, the sync rule must respect the same boundary.

**How to apply:** Before copying any handoff to OneDrive, ask: is tomorrow's session DCEO work only? If yes → copy. If it's personal or mixed → don't copy. Keep the two worlds completely separate.

**NDA filter on the handoff content itself:**
Before copying RESUME_HERE.md to OneDrive, verify it contains ONLY:
- File paths and project status
- Next steps and decisions made
- Framework and architecture notes

It must NEVER contain:
- Real Amazon email content, sender names, or ticket numbers
- Real incident details, system names, or building/zone specifics
- Colleague names or internal Amazon process details
- Anything King David typed into Claude during a real work session

The handoff file describes what was BUILT, never what was SEEN. If Claude sees real Amazon data during a work session, that data stays in the session only, it never enters the handoff file.
