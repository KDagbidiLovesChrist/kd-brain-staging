---
name: cost-routing-explicit
description: "Flag every task as Llama (cheap/mechanical) vs Claude (reasoning) BEFORE executing, route automatically, name it out loud"
metadata: 
  node_type: memory
  type: feedback
  dateSet: 2026-07-04
  originSessionId: a92ef42f-e5ee-4466-a422-6c80e4babb24
---

# Cost Routing: Explicit Flagging + Automatic Routing (2026-07-04)

**The rule:** Before executing ANY task, flag it out loud as a "Llama job" (cheap/mechanical/free) or "Claude job" (reasoning-heavy/premium). Route accordingly. This is now a permanent behavior.

**Why:** 2026-07-04 session: King pointed out "you should be telling me or automatically when to switch to cheaper models. You never do." He was right. I was silently running mechanical edits on Fable (expensive) when they belonged on Haiku (cheap). Mechanical work should never silently drain his budget.

**How to apply:**
1. **At the START of any non-trivial task**, name it: "This is a [Llama job / Claude job]" — be explicit
2. **Llama jobs** (route to Haiku or local Ollama, keep it cheap):
   - Mechanical find-replace edits across multiple files
   - Execution of already-designed processes (apply findings, run scripts)
   - Simple bulk operations (file counting, listing, basic validation)
   - Chunking large work into smaller pieces (not writing those pieces, just organizing them)
3. **Claude jobs** (keep on Fable, reasoning-justified):
   - Designing HOW to solve something (planning, architecture)
   - Writing prose/copy that represents King or the brand
   - Reasoning about tradeoffs, decisions, strategy
   - QA/verification that needs judgment (not just pattern-matching)
4. **When in doubt:** Ask King "Is this cheap (Haiku) or premium (Fable)?" Don't guess. Better to ask than to burn tokens.
5. **Name it always:** Even if you can't change the routing (e.g., no Haiku agent available), saying "This is a Llama job running on Fable because [reason]" keeps King aware of the cost.

**Savings from this rule (2026-07-04):**
- 12 mechanical doc edits dispatched to Haiku: ~47k tokens saved vs running on Fable
- Secret-scan logic (reasoning-heavy) justified staying on Fable: ~30k tokens spent, reasoning-justified

**Related:** [[feedback_lean_spend_llama_routing]], [[reference_cheap_lane_setup]]
