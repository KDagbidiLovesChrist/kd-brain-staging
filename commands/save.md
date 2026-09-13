# /save · Session Save Skill

**Trigger:** User types `/save` OR says "save session", "save my progress", "save that", "save it", "save what we've done"
**Purpose:** Save everything learned this session to the right places so nothing is ever lost, even if the conversation is cleared

---

## STEP 1 · Audit the session
Before saving anything, mentally review the full conversation:
- What tasks were completed?
- What decisions were made?
- What new things were learned about King David, his projects, or how he works?
- What files were created or changed?
- What is the single most important next step?

If nothing meaningful happened this session worth saving, say so clearly, but still write the handoff file with that note.

---

## STEP 2 · Route learnings to the right files

Use this routing table. For EACH learning from this session, identify where it belongs and write it there. Do not rewrite files that have nothing new, only touch files that need updating.

| Type of learning | Target file |
|---|---|
| King David stated a preference about how I should behave | `C:\Users\Dell\.claude\memory\user_profile.md` · append |
| A project moved status (PENDING → COMPLETE, etc.) | `C:\Users\Dell\.claude\memory\project_[name].md` AND update the badge in `memory\ACTIVE_PROJECTS.md` + the one-line dashboard in CLAUDE.md (post-reorg 2026-07-04) |
| A brand new project was discussed or started | Create `C:\Users\Dell\.claude\memory\project_[name].md` with YAML front matter. Add to MEMORY.md index. Add to `memory\ACTIVE_PROJECTS.md` + a one-liner in CLAUDE.md's dashboard |
| A permanent rule about how sessions should run | `C:\Users\Dell\.claude\memory\feedback_operating_rules.md` · append |
| A correction about proceeding, pausing, executing | `C:\Users\Dell\.claude\memory\feedback_proceed_without_permission.md` or `feedback_always_execute.md` |
| A DCEO work email type was handled + pattern learned | `C:\Users\Dell\.claude\DCEO_BRAIN\knowledge\email_patterns.md` (LAPTOP-ONLY: DCEO_BRAIN lives outside the synced brain) · append in standard format. FLAG FOR GOOGLE DRIVE SYNC. |
| A new DCEO incident type or response was discussed | `C:\Users\Dell\.claude\DCEO_BRAIN\knowledge\incident_patterns.md` (LAPTOP-ONLY: DCEO_BRAIN lives outside the synced brain) · append. FLAG FOR GOOGLE DRIVE SYNC. |
| A DCEO ticket type or resolution approach was learned | `C:\Users\Dell\.claude\DCEO_BRAIN\knowledge\ticket_patterns.md` (LAPTOP-ONLY: DCEO_BRAIN lives outside the synced brain) · append. FLAG FOR GOOGLE DRIVE SYNC. |
| A DCEO escalation procedure was discussed or refined | `C:\Users\Dell\.claude\DCEO_BRAIN\knowledge\escalation_procedures.md` (LAPTOP-ONLY: DCEO_BRAIN lives outside the synced brain) · append. FLAG FOR GOOGLE DRIVE SYNC. |
| A new DCEO work procedure or protocol was learned | Create new file in `C:\Users\Dell\.claude\DCEO_BRAIN\knowledge\`. FLAG FOR GOOGLE DRIVE SYNC. |
| AIS Challenge moved to a new day / day completed | `C:\Users\Dell\.claude\memory\_archive\project_7day_challenge.md` (challenge COMPLETE, archived) · update day status |
| Amazon / Orcha / DCEO Brain progress | `C:\Users\Dell\.claude\memory\project_dceo_work_ai.md` · update |
| Newsletter project update | `C:\Users\Dell\.claude\memory\project_wat_newsletter.md` · update |
| Lead gen scraper update | `C:\Users\Dell\.claude\memory\project_scraper_leadgen.md` · update |
| What to do next session was agreed | `C:\Users\Dell\.claude\memory\project_upcoming_tasks.md` · REPLACE content with updated priority list |
| A framework or reference was explained and is worth keeping | `C:\Users\Dell\.claude\memory\reference_[topic].md` · create or update |

### Routing rules:
- If a project status changed, update BOTH the memory file AND the badge in `memory\ACTIVE_PROJECTS.md` (+ the one-line dashboard in CLAUDE.md — post-reorg 2026-07-04, full histories no longer live in CLAUDE.md)
- If a new memory file is created, it must also be added to MEMORY.md index
- If nothing in a file changed, leave it untouched
- Memory files use this YAML front matter format:
```
---
name: kebab-case-name
description: "One-line summary"
metadata:
  type: project  (or user, feedback, reference)
---
```

---

## STEP 3 · Update the Active Projects dashboard (post-reorg 2026-07-04)
Open `C:\Users\Dell\.claude\memory\ACTIVE_PROJECTS.md` (full histories) AND `C:\Users\Dell\.claude\CLAUDE.md` (one-line dashboard).
For every project whose status changed this session:
- In ACTIVE_PROJECTS.md: update the status badge `[NEW]` / `[UPDATED]` / `[COMPLETE]` / `[PENDING]` / `[BROKEN]` + the description
- In CLAUDE.md: keep only the ONE-LINE entry current (do not re-grow CLAUDE.md; the 94-line lean file is deliberate)
- Leave sections that did not change completely untouched

---

## STEP 4 · Update MEMORY.md index
Open `C:\Users\Dell\.claude\memory\MEMORY.md`.
- If any new memory files were created in Step 2, add them to the index (one line, under 150 chars)
- If any existing entries are now outdated, update the description to reflect current state
- Keep every entry as: `- [Title](filename.md), one-line hook`

---

## STEP 5 · Write the handoff file
Write a detailed handoff to:
`C:\Users\Dell\.claude\handoffs\handoff_[YYYY-MM-DD]_[HH-MM]_save.md`

Use this exact format:
```
# Session Save · [DATE] [TIME]
**Saved by:** /save skill
**Project open:** [which folder/project was active]

## What Was Accomplished This Session
[Specific bullet list, concrete, what was built, written, decided. No vague summaries.]

## Decisions Made
[Key choices made this session, what was chosen and why]

## Files Created or Changed
[Full paths, one per line, brief note on what each one is]

## Memory Files Updated
[List which memory files were touched and what was added or changed]

## Money Progress
[Status of income-generating projects, Fiverr gig, newsletter, leads. Be specific.]

## AIS Challenge Status
[Day X complete / Day X in progress / what's left]

## The ONE Thing To Do First Next Session
[Single most important action, exact and specific, not vague. Example: "Post the Fiverr gig for lead gen scraper at €25/50 leads"]

## Notes
[Anything else worth knowing, warnings, blockers, time context, unfinished threads]
```

---

## STEP 6 · Confirm to King David
After all saves are done, output this summary:

```
SAVED ✓
─────────────────────────────────
Memory files updated:
  • [list each file that was changed]

Handoff written:
  • handoffs/handoff_[DATE]_[TIME]_save.md

DCEO work brain files updated:
  • [list any DCEO_BRAIN\knowledge\ files that were changed, or "none this session"]

Google Drive sync needed:
  • [list files that need re-uploading to Drive, or "none this session"]
  • Drive location: drive.google.com → My Drive → DCEO_Brain → knowledge\

ONE thing to do first next session:
  → [the specific next action]
─────────────────────────────────
```

---

## WHEN TO RUN /save
- After any completed task
- When King David says "save", "save that", "save my progress", "done for now", "that's it"
- At the end of every session, always, without exception
- Any time context might be lost (before clearing, before switching project)

## IMPORTANT
- Never save vague or empty notes. Be specific.
- Never skip the handoff file, it is what /recover reads next session.
- Never skip the confirmation message, King David needs to see what was saved.
- If there is truly nothing new to save, write the handoff file anyway noting the session was light, and confirm that nothing was changed.
