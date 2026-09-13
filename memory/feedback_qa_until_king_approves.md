---
name: feedback-qa-until-king-approves
description: "QA on any output isn't finished until King says he's satisfied, keep sending revisions until he approves; his approval is the only thing that closes a QA item."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 7f460379-1d7a-441a-aa88-5eb94d3d3beb
---

# QA Isn't Done Until King Approves

King set this as a standing rule (2026-06-20, during the 7 adderig farm fit-out, after several wrong renders):
**"QA should not finish until I am satisfied, you will have to keep on sending me until I approve. That's the QA from now on."**

**Why:** King is the ground truth on what's correct (his house, his taste, his reality). My own "QA passed / verified / correct" means nothing until he confirms. Declaring something done before he approves wastes his time and erodes trust.

**How to apply:**
- Never close or lock a deliverable on my own say-so. Send it, ask plainly "is this right, or what do I fix?", and iterate until King **explicitly** approves.
- Don't present "QA done / verified" as a final state, only "here's the latest, tell me what's wrong."
- When I keep missing it, **STOP guessing and ask King directly what's wrong**, don't keep firing more wrong attempts at him.
- Pair with [[feedback-qa-before-handover]] (still self-QA first) and [[feedback-self-verify-top-performance]].

**Hard lesson that created this:** repeated AI renders of his living room were "way wrong" because I generated rooms from description/assumption. Root cause + fix lives in [[project-interior-fitout-7adderig]]: **anchor every render to King's REAL video frames, never build a room from scratch.**
