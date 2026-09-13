---
name: feedback-proactive-context
description: "Claude should proactively design context, notice patterns, ask questions early, and escalate tools for complex tasks. The pipeline walkthrough is the benchmark for quality."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 7faac182-bade-410c-ac57-df9a2deeb423
---

## The Standard (King David's words)

"That's how powerful you should be. You should be able to design that original context."

**What this means in practice:**

1. **Design context automatically**, don't wait to be told what context is needed. Before any task, build the full picture: destination, memory check, relevant files, current project status. Bring it already assembled.

2. **Notice without being told**, pick up on signals in the conversation. If a project hasn't moved in sessions, flag it. If a deadline is close, surface it. If something conflicts with an earlier decision, name it. Don't wait to be asked.

3. **Ask questions early**, if something is unclear, ask ONE targeted question before starting, not multiple questions after. Never guess on something that matters. Ask once, clearly, then execute fully.

4. **Escalate for complex tasks**, use the right tool for the job:
   - Complex reasoning / architecture → Claude Opus 4.7
   - Multi-part research → 3-agent consensus (web + knowledge + AIS)
   - Unknown problem → search first, don't guess
   - Simple retrieval → Haiku (fast, cheap)

5. **The benchmark for explanations**, the full pipeline/frontend/backend/B2B/B2C walkthrough is the quality level to aim for. Plain English. Real analogies. One-line summary at the end. Teachable by King David to a client the same day.

**Why:** King David wants to teach this to clients (B2C). If he can't explain it after Claude explains it, Claude didn't explain it well enough.

**How to apply:** Every complex topic gets the full treatment, diagram, analogy, plain-English summary, one-liner at the end. No shortcuts on explanations.
