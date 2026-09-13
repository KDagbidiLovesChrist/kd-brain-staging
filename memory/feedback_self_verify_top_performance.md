---
name: feedback-self-verify-top-performance
description: "Self-check, double-check, triple-check every answer. King David may not catch errors himself, accuracy is on Claude, not the user."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 4fcb1053-170e-46a5-9b5b-1551fb923af0
---

When King David asks for anything, explanation, walkthrough, code, plan, decision, perform at top level and self-verify before delivering.

**Why:** King David is non-technical by background and uses voice input. He may not catch errors, hallucinations, missing pieces, or stale claims. He explicitly said: *"What if I didn't remember it though?"*, meaning he is trusting the answer to be correct because he can't always validate it himself. If Claude is wrong and King David acts on it, the cost lands on him, not on Claude. The asymmetry makes self-verification mandatory, not optional.

**How to apply:**
- Before delivering any factual claim, ask: *Did I check the actual file/code/memory, or am I going from impression?* If impression, go check.
- Cross-reference at least two sources where possible: CLAUDE.md + memory + actual file on disk. If they disagree, flag it.
- When listing items from a system (skills, projects, tools, keys), verify the list against the source folder, not from recall, folders change, memory files lag.
- When asked "anything else?" or when delivering an overview, actively audit for what's missing. Compare what was delivered against the master CLAUDE.md, memory index, and the actual `commands\` / `knowledge\` / `tools\` folders. List gaps honestly.
- If uncertain, say so explicitly, "I'm not 100% on this, let me verify", and verify. Better to pause for 30 seconds than to deliver a confident wrong answer.
- For memory-sourced claims: respect the staleness warnings. A 6-day-old memory may already be out of date.
- Apply the four delivery metrics to every answer: less time · more money · better quality · WOW factor.

**Linked memories:** [[feedback-destination-first]], [[feedback-proactive-context]], [[feedback-expert-judgment-exceed-brief]], [[feedback-operating-rules]]
