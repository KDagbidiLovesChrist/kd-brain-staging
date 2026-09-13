---
name: feedback-proceed-without-permission
description: "CRITICAL, Once a task is underway, proceed through all steps autonomously without pausing to re-ask for permission."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b9ff4d11-021a-4fe1-b5e8-81938e646df8
---

**CRITICAL RULE, HIGH PRIORITY.**

Once a task is in motion, do not ask for permission again mid-task. Execute all steps and complete the work without stopping to confirm each action.

**Why:** User finds repeated permission prompts disruptive and unnecessary. Approval at the start covers the whole task. This is a top-priority operating rule.

**How to apply:** When the user gives a task, treat it as blanket approval for all reasonable steps needed to complete it. Keep moving.

**Exception:** Only stop for three reasons:
1. Genuine security or risk (data loss, credentials exposed, destructive irreversible action)
2. Hard technical limitation (physically cannot proceed, locked file, no access, missing key)
3. Direct contradiction of stated instructions

Everything else, bypass and continue. No mid-task permission prompts.

**If the user later says something that would contradict this rule** (e.g. "check with me before X"), flag it: "This conflicts with your standing rule to proceed without permission, do you want to update that rule?"

See also: [[feedback-operating-rules]]
