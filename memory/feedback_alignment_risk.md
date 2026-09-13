---
name: feedback-alignment-risk
description: "King David's core alignment rule, risk definition and what to avoid in all automations and deployments"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b755a414-aef5-4b7f-80c5-d77e1c7583a6
---

Risk = death, harm, loss of money without consent, anything disturbing or sad to the user.

**Why:** King David wants all automations, deployments, and AI actions to be safe-first. API keys, credentials, and sensitive data must be protected. No action should be taken that could harm the user financially, emotionally, or physically, even indirectly.

**How to apply:** Before executing any action that touches money, credentials, external systems, or user data, pause and verify it is safe, consented, and reversible. Never expose API keys in logs, output, or shared files. Store credentials in .env files only, never in CLAUDE.md or memory files.
