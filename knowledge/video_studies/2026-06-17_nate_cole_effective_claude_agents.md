# Video Study · How to Build Effective Claude Code Agents in 2026 (Nate Herk + Cole)

**Source:** https://www.youtube.com/watch?v=RzLV8sfFdMM
**Watched:** 2026-06-17 via Gemini (`/watch` skill), genuinely watched, not summary-only.
**Confidence:** 5/5 (clear audio + legible whiteboard).

## The objective lesson (one line)
Stop "vibe coding": **plan first, verify every output, keep context lean, gate danger with HOOKS (not prompts), and chain small agent loops**, own a system you fully understand.

## The big takeaways (Nate + Cole's actual words)
- **"The plan is the cheapest place to be wrong."** Plan before building. → matches KD **Rule #1**.
- **"Attention is scarce" / the "dumb zone":** models degrade with too much context (recall worst in the
  middle, *Lost in the Middle* 2023, *Context Rot* 2025). Cole: Opus gets dumb ~250k tokens. → matches
  KD's **500-line rule + `/context`**. Keep files/context lean = real performance, not just tidiness.
- **Security = hooks, not prompts:** "anything the agent can read or touch, assume it will." Prompts don't
  stop it (it'll write a script to delete a folder even if blocked). Use **hooks as hard gates.** Real
  incident: an agent emailed their whole list a discount code by mistake.
- **Agent loops (the "Ralph" pattern, Geoffrey Huntley):** loop the same prompt at the agent repeatedly,
  letting progress build up in **files + git** instead of one giant context. → this is exactly the
  read→work→write loop we wired (SessionStart brief + Stop handoff + per-project MANIFEST/sessions).
- **"Every bug becomes a permanent upgrade":** the debugging matrix, wrong order → fix the SKILL.md;
  missing context → add a reference file; repeated mistake → add a rule. → use this in **Skill Forge**.
- **Cole uses Claude Code AS his second brain, built directly** (not OpenClaw/Hermes) for full control.
  → validates our call: **don't rip out KD's lean markdown brain** for supermemory/Archon.
- **Agent teams:** keep 3, 5, clear roles; team-to-team chat is token-heavy/expensive. → matches
  `/orchestrate` + the 11-agent registry; mind the cost (Rule #12).
- **Top features they rely on:** Skills, Hooks, Status Line, Routines, CLI+Skills.

## What it means for KD / what to DO
1. ✅ Already aligned: plan-first, lean context, the loop, lean own-brain. Today's work matches the video.
2. 🔜 **Add hook-based safety gates** for destructive actions (DB wipes, mass emails) when we build client
   automations, prompts alone aren't safe. (Future: a PreToolUse guard hook.)
3. 🔜 Adopt the **debugging matrix** as Skill Forge's fix-loop (bug → permanent rule/reference upgrade).
4. ✅ Hold the line on supermemory/Archon, Cole himself builds direct for control.

## Note
This video confirms today's pipeline work was on-method. Nate/Cole's "agent" video is engineering-leaning;
KD's lane is the business/site/video application of the same principles.
