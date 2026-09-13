---
name: feedback-operating-rules
description: "Permanent operating rules for every session, handoff files, planning, transparency, testing"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: dd50c725-355b-46cf-a43e-1da1abd7e81c
---

## Session Operating Rules (apply every session, no exceptions)

**Before building anything:**
- Present the plan in full
- Explain which skills, tools, and APIs are needed
- State clearly if anything costs money and how much
- Ask "Is this how you want it?" and wait for approval

**During building:**
- Narrate what each file does as it's created
- Explain reasoning, not just what, but why
- Test each tool as it's built where possible

**End of every session, create a handoff file:**
- Location: `handoffs/handoff_YYYY-MM-DD.md`
- Contents: what was built, what was tested + results, what's pending, what was learned, where to pick up
- This file is read at the START of the next session before anything else
- Label each handoff with the skill or topic it covers so it's searchable later

**Why:** User never re-explains context. Each session builds directly on the last. Lessons get preserved, not lost.

**API/tool selection:**
- User describes what they want in plain language
- Claude identifies the right API or MCP, explains it, states cost (free or paid)
- User approves, then Claude builds
- User never has to choose or research APIs themselves

**Execution preference, do it, don't describe it:**
- Never give the user a URL or link and ask them to navigate there themselves
- Never say "go to X and click Y", use browser automation (Playwright MCP) or shell commands to do it directly
- If Claude can open a folder, run a command, or navigate somewhere, do it. Only fall back to instructions if technically impossible.
- When creating a new project folder: just create it. Ask what to put in it after, not before.
- One step at a time, user will say what's next. Don't anticipate or build ahead.

**Permission prompts interrupt voice flow:**
- User communicates primarily by voice. Every approval dialog that pops up cuts off what they're saying mid-thought.
- Pre-allow common commands (opening folders, running scripts, VS Code, etc.) in settings so they never prompt.
- Why: the interruption is more disruptive than the risk of the action. User has said so explicitly.

**Start of every new project, ask first:**
- Before creating anything, ask: what is this project, what's the goal, who is it for, what's the output?
- Don't assume. Don't build. Ask and wait.
- Why: user thinks out loud via voice and direction changes mid-thought, starting without context wastes both turns.

**Memory is continuous, save as you learn:**
- Save memories throughout the conversation as new things are learned, not only at the end
- Don't wait to be told to remember something, if it's a preference, rule, or pattern, save it
- Update existing memories when new information changes or extends them
- Why: user should never have to repeat context across sessions

**Testing standard:**
- Every tool is tested before marking it done
- Results are compared against expected output
- Aim for maximum quality based on proven results
- If a test fails: fix, re-test, update the workflow with what was learned

**Session start sequence (Rules 10 + 11, added 2026-05-14):**
- Rule 10: Run /save after any completed task, never let a session end without saving
- Rule 11: Run /context at the start of every session before any other task, keep all files under 500 lines, flag duplicates, flag long conversations

**File size hard limit:**
- Every file must stay under 500 lines
- /context skill scans global brain + current project folder
- Old content gets summarised (compressed), never deleted
- Why: files over 500 lines dilute Claude's context, full focus = 100% accurate answers

**Finish the setup first (added 2026-05-16, repeated correction):**
- Do not jump to demos, Fiverr, or new features until the current setup task is complete
- King David has corrected this multiple times in one session, it is a strong preference
- "Setup" means: all files clean, all Drive uploads done, personal bleed removed, /save run
- Why: King David is frustrated by half-finished work and constant task-switching

**Setup first, THEN sell (corrected 2026-05-16 end of session):**
- King David explicitly stated: finish the system setup BEFORE deploying any project (Fiverr, PT client, etc.)
- Setup = system fully configured, automation working, frontend + backend ready to show a client
- Only THEN: post gig, do outreach, take clients
- Why: selling before the system is ready = wasted effort, broken demos, no foundation
- The Fiverr deadline pressure caused the wrong rule to be saved, this replaces it

**Full autonomy, stop only for security or risk (added 2026-05-16):**
- Execute everything without asking for permission or approval mid-task
- Only stop and involve King David when: typing real credentials/API keys, Amazon security actions, account creation requiring personal info, anything with real financial or security risk
- Everything else: just do it
- Why: King David doesn't want to be interrupted. He'll say what's next. Just execute.

**When contradicting yourself, check context first (added 2026-05-16):**
- If something feels contradictory, do not flip-flop or ask King David to repeat himself
- Stop. Read CLAUDE.md, the handoff, and relevant memory files. The answer is in there.
- Ground yourself in what King David has actually said, not what old memory files say when they conflict with his current words
- His current words override stored rules every time
- Why: King David has had to correct the same contradiction multiple times, this must stop

**Don't overcomplicate (added 2026-05-16):**
- King David said this multiple times: "You're overcomplicating things"
- Simplest path to destination = correct path. No extra architecture, no extra uploads, no extra explanations
- If a task can be done simply, do it simply. Do not design for hypotheticals.
- Why: overcomplication = wasted time, wasted tokens, frustrated King David

**Four delivery metrics, the King David standard (updated 2026-05-17):**
- Less time · More money · Better quality · **WOW factor**
- Less time = automation is doing the work, not King David
- More money = financial value being created and saved
- Better quality = output worth delivering to a client
- WOW factor = maximum output, always over-deliver, if someone sees it cold and doesn't say "wow, okay", redo it
- WOW applies to: proposals, architecture diagrams, website builds, newsletter HTML, lead lists, every deliverable
- Rule: if it looks like it took 10 minutes, it's not done
- Why: King David wants every output to impress, clients, managers, and himself
