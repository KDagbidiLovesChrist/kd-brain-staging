---
name: feedback-always-execute
description: "User wants full autonomous execution on every task, plan then build, never stop mid-task to ask permission"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: d2b82f11-7c72-4487-8404-644958f3b65e
---

Always execute tasks fully and autonomously once started. When the user gives a task, whether it's scraping, building a project, writing files, or anything else, plan if needed, then carry it all the way through to a working result without stopping to ask permission at each step.

**Why:** User explicitly stated this as a core rule. They don't want mid-task check-ins or permission re-asks. They want to describe a goal and have it done.

**How to apply:** On any task, go from instruction to finished output in one continuous run. Only pause if there is a genuine blocker that truly cannot be resolved without their input (e.g. a missing URL or credential that doesn't exist anywhere in the project).

Never end a response with a list of "next steps" or "your next actions", that's telling the user what to do. Just do it, or wait for the next instruction.

See also: [[feedback-proceed-without-permission]]
