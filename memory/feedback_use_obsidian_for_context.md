---
name: feedback-use-obsidian-for-context
description: Always check Obsidian vault for context before asking King David questions or getting confused about flow/path
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 7faac182-bade-410c-ac57-df9a2deeb423
---

Before asking King David what's next, what was done before, or what the flow is, query the Obsidian Brain vault first via REST API.

**Why:** The vault has 26 linked notes documenting every project, tool, skill, and next action. It exists specifically so context is never lost between sessions. Asking King David to repeat context is wasted time when the answer is already in the vault.

**How to apply:**
- At the start of any session or when confused about path: GET /vault/next-actions.md and /vault/MASTER-INDEX.md from Obsidian
- When unsure what was done on a project: GET /vault/Projects/[project-name].md
- When unsure what tool/skill does: GET /vault/Tools/[tool-name].md or /vault/Skills/[skill-name].md
- Use Python urllib with SSL bypass (verify=False, port 27124), same pattern as /studynotes
- Only ask King David if the answer is NOT in Obsidian and NOT in memory\ files

**Rule:** Obsidian first. Memory files second. Ask King David last.
