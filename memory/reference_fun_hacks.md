---
name: reference-fun-hacks
description: "Power tricks, hacks, and shortcuts for getting the most out of Claude Code. Based on Nate Herk's course Chapter 23 + discovered techniques."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Claude Code · Fun Hacks & Power Tricks

The tricks that make Claude Code feel like a superpower instead of just a chat tool.
These are the things most people don't know about.

---

## HACK 1: Ultrathink (Deep Reasoning Mode)

**The trick:** Add the word "ultrathink" anywhere in your message.

**What happens:** Claude activates extended thinking, much deeper reasoning, more
angles considered, edge cases caught. The difference between a standard answer and a
genuinely excellent one.

**When to use:**
- Hard architecture decisions ("ultrathink, should I build X as one script or three?")
- Complex debugging ("ultrathink, why is this failing on that specific site?")
- Strategy questions ("ultrathink, what's the best pricing model for this client?")
- Anything where being wrong costs time or money

**Real example:**
> "ultrathink, design me an agent team architecture for the newsletter + lead gen service"

vs.

> "design me an agent team architecture for the newsletter + lead gen service"

The first gets a genuinely thought-through design. The second gets a generic answer.

**Note:** Uses more tokens. Only fire ultrathink when depth matters.

---

## HACK 2: @File Tagging (Direct Context Injection)

**The trick:** Type `@` followed by a filename to inject that file directly into your message.

**Why it's powerful:** Instead of saying "look at my brand guidelines," you type
`@brand_guidelines.md` and Claude reads the exact file, right now, as part of your prompt.

**Examples:**
```
Build me a newsletter about the Irish property market @brand_guidelines.md @newsletter_sop.md
```
```
Debug this script @scrape_leads.py, it's failing on page 3
```
```
Write a client proposal based on @discovery_sop.md and @clients.md
```

**Best practice (from Nate's course):** Before asking Claude to build anything that represents
you publicly, always tag `@brand_guidelines.md`. Every newsletter, every website, every proposal
should start with Claude reading your brand first.

---

## HACK 3: Model Switching Mid-Session

**The trick:** Use `/model` to switch Claude models without starting a new session.

**Why it matters:** Different models have different strengths. You can use cheap/fast models
for simple tasks and powerful models for hard problems, all in the same session.

**The smart workflow:**
1. Start with Sonnet (balanced, good for most things)
2. Hit a hard problem → switch to Opus for that specific task
3. Back to Sonnet for regular work
4. Simple formatting or summarisation → switch to Haiku (fastest, cheapest)

**Cost impact:** Haiku costs a fraction of Opus. Using the right model for the task
saves significant money on longer sessions.

---

## HACK 4: Plan Mode → Bypass Mode Workflow

**The trick:** Always start in Plan Mode. Switch to Bypass only after reviewing.

**Why it's powerful:** Plan Mode forces Claude to show you EXACTLY what it's going to do
before it does anything. You catch problems in the plan, not in the execution.

**The workflow Nate uses (and what you should do):**
1. Switch to Plan Mode before describing your task
2. Tell Claude what you want (can be vague, Claude will ask clarifying questions)
3. Claude comes back with a plan, read it carefully
4. Make any corrections ("change X", "don't do Y", "use Z instead")
5. Switch to Bypass Mode
6. Tell Claude to execute, it works autonomously until done

**Result:** You get control AND speed. You review once, then let Claude run.

---

## HACK 5: /compact Continuation

**The trick:** When context gets long, use `/compact` instead of starting over.

**Why it matters:** Starting a new session = explaining everything again. /compact
summarises what's happened and keeps going, you lose nothing meaningful.

**Power move:** After /compact, say: "Continue from where we left off, we were building
[X] and had just finished [Y]." Claude picks up cleanly.

---

## HACK 6: Multi-Task in One Message

**The trick:** Ask Claude to do multiple independent things in a single message.

**Why:** Claude can run multiple tool calls simultaneously. Asking for 5 things in one
message is often faster than 5 separate messages.

**Example:**
> "Three things: 1) Read the newsletter workflow and tell me if there's anything missing.
> 2) Check if the .env file has all required keys. 3) Tell me the current status of the
> scraper project."

Claude handles all three in parallel. You get answers to all three at once.

---

## HACK 7: Ambiguous Prompts Work (Let Claude Ask)

**The trick:** You don't need to have everything figured out before you start. Give Claude
a rough idea and let it ask questions.

**Why:** Claude in Plan Mode will identify what it needs to know. It's better at asking
the right questions than you are at guessing what to specify upfront.

**Nate's example from the video:**
> "I want to build a newsletter automation. Research, HTML, pretty. Help me figure out the
> tech stack and what I haven't thought of."

That's all he said. Claude came back with 3 specific questions. By answering those 3
questions, the whole plan was defined. No technical knowledge required.

**Your version:**
> "I want to build [thing]. Help me figure out how to do it and what I haven't thought of."

Claude will do the rest.

---

## HACK 8: Skill Stacking

**The trick:** Skills work better when they reference each other. A skill can tell Claude
to read another file or run another skill as part of its workflow.

**Example:** The /exec skill references brand_guidelines.md. The /monetize skill references
the Digital Transform Consultancy SOPs. The /newsletter skill references the SOP + brand.

**Why:** Each skill becomes smarter by inheriting from others. The system compounds.

---

## HACK 9: The /clear + /recover Combo

**The trick:** When you want a completely fresh session but don't want to lose context:
1. Run /save (save everything)
2. Run /clear (wipe the whiteboard)
3. In the new clean session, run /recover (read everything back)

**Result:** Clean slate for Claude's working memory, but all your knowledge, projects,
and context are immediately restored. It's like restarting a computer, clears RAM but
keeps your files.

---

## HACK 10: Sub-agent Briefing Quality

**The trick:** The quality of a sub-agent's output = the quality of your briefing.

When Claude spawns another Claude to handle a task, that sub-agent starts with zero
context, it only knows what the briefing tells it. Vague briefing = vague result.

**Good sub-agent briefing includes:**
- Exactly what you need (not "research this topic" but "find 5 competitors in the Irish
  lead gen market, their pricing, their USP, and any gaps")
- What format you want back
- What NOT to do
- How long the response should be

**Result:** Sub-agents that work like specialists, not generalists.

---

## HACK 11: Status Line Customisation

**The trick:** The status line at the bottom of Claude Code can show custom information.

**Default:** Shows model name and context usage %
**Can show:** Current project name, session goal, key reminder, anything useful

**How to set it:** Use the /statusline-setup skill.

**King David suggestion:** Set it to show the current active project + context usage.
Example: "Newsletter Build | 45% context"

---

## FUTURE HACKS
*These sections will be filled in as more of the course transcript becomes available:*

- [ ] GitHub Worktree hacks (Chapter 22 content)
- [ ] Browser automation shortcuts (Chapter 19 content)
- [ ] Agent team orchestration tricks (Chapter 18 content)
- [ ] RAG optimisation techniques (Chapter 10 content)
- [ ] Deployment speed tricks (Chapter 7 content)

---

## QUICK REFERENCE

```
DEEP THINKING:  Add "ultrathink" to any message
FILE INJECTION: Type @filename to include a file directly
MODEL SWITCH:   /model, Haiku (fast/cheap) / Sonnet (balanced) / Opus (powerful)
WORKFLOW:       Plan Mode → review → Bypass Mode → execute
CONTEXT SAVE:   /compact (keep going) or /clear → /recover (fresh start)
MULTI-TASK:     Ask for multiple things in one message, Claude handles in parallel
AMBIGUOUS OK:   Give rough idea → Claude asks the right questions in Plan Mode
```
