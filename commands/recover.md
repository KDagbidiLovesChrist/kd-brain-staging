# /recover · Session Recovery Skill

**Trigger:** User types `/recover` OR says "where were we", "catch me up", "what were we doing", "what was I doing", "what's the status", "recap", "I cleared the conversation", "context lost"
**Purpose:** Read the latest saved state and give King David a complete briefing so he can pick up exactly where he left off, no re-explaining needed

---

## STEP 1 · Find the latest handoff
Look in `C:\Users\Dell\.claude\handoffs\` for files matching `*_save.md`, these are the detailed saves from the /save skill.
Sort by file modification time. Read the most recently modified one fully.

If no `*_save.md` file exists, read the most recently modified file of ANY type in the folder, it will be an auto-generated packet with project status and upcoming tasks.

---

## STEP 2 · Read key memory files
Always read these regardless of what the handoff says:
- `C:\Users\Dell\.claude\memory\MEMORY.md`, check the index for anything flagged or new
- `C:\Users\Dell\.claude\memory\project_upcoming_tasks.md`, what was planned next
- `C:\Users\Dell\.claude\memory\user_profile.md`, who this is and how they work

Then read the memory files most relevant to what the handoff says was happening:
- If a DCEO project was active → read `memory\project_dceo_work_ai.md`
- If newsletter or scraper work was happening → read those project files
- If a new skill was being built → read the relevant project file

---

## STEP 3 · Read CLAUDE.md Active Projects
Open `C:\Users\Dell\.claude\CLAUDE.md` and read the Active Projects section.
Note which projects are COMPLETE, UPDATED, PENDING, or BROKEN.

---

## STEP 4 · Deliver the Recovery Briefing

Present in this exact format, plain English, no jargon, no long paragraphs:

```
══════════════════════════════════════════════
RECOVERY BRIEFING, [Date/time of last save]
══════════════════════════════════════════════

WHERE WE LEFT OFF
─────────────────
[2-3 sentences. Plain English. What was happening, what were we building, where in the process were we.]

WHAT WAS COMPLETED
──────────────────
• [bullet]
• [bullet]
• [bullet, if nothing completed, say "No tasks completed in last recorded session"]

THE ONE THING TO DO FIRST
──────────────────────────
→ [Single specific action. Not "continue the project", exact and actionable.
   Example: "Post the Fiverr gig for the lead gen scraper, €25/50 leads, €50/150 leads"]

ACTIVE PROJECTS STATUS
───────────────────────
1. [Project name], [status badge], [one line on where things stand]
2. [Project name], [status badge], [one line]
(list all projects from CLAUDE.md Active Projects)

MONEY PROGRESS
──────────────
[What income-generating work is live, pending, or in progress. Specific numbers if known.]

ANYTHING URGENT OR FLAGGED
───────────────────────────
[Any warnings, broken items, deadlines, or things that need attention. "None" if nothing flagged.]

══════════════════════════════════════════════
Ready to continue. What would you like to do?
══════════════════════════════════════════════
```

---

## WHEN TO RUN /recover
- **First thing at the start of any new session**, before any other task
- After accidentally clearing the conversation
- When returning after days away
- Any time King David asks "where were we" or context feels lost
- When a new Claude Code session is opened and context needs restoring

## NOTE
If the last handoff was an auto-generated file (no `/save` was run), the briefing will still work, it will pull from CLAUDE.md project statuses and the upcoming tasks memory file. It will be less detailed but still useful.

Always end with: "Ready to continue. What would you like to do?", so King David knows recovery is complete and can continue working.
