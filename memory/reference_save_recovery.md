---
name: reference-save-recovery
description: "How the /save and /recover skills work, the routing table, and what auto_handoff.py does at session end"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 6f964ee4-5853-4922-a11d-d4847ec0d5bc
---

# Save & Recovery System

## The Problem This Solves
When a conversation is accidentally cleared, or a new session opens, context is lost. This system ensures nothing is ever truly lost, every session's learnings are saved to the right files so /recover can restore full context instantly.

## The Three Components

### 1. /save skill (`commands/save.md`)
**Trigger:** User types `/save` or says "save session", "save my progress", "save that"
**What it does:**
- Audits what was accomplished in the session
- Routes learnings to the right memory/skill files (see routing table below)
- Updates the Active Projects badges if any project changed (post-reorg 2026-07-04: full badges in `memory/ACTIVE_PROJECTS.md`, one-line dashboard in CLAUDE.md)
- Keeps MEMORY.md index in sync if new files were created
- Writes a detailed handoff file: `handoffs/handoff_YYYY-MM-DD_HH-MM_save.md`
- Confirms what was saved to King David

**When to run:** After any completed task. At the end of every session. Any time context might be lost.

### 2. /recover skill (`commands/recover.md`)
**Trigger:** User types `/recover` or says "where were we", "catch me up", "context lost"
**What it does:**
- Reads the latest `*_save.md` handoff file
- Reads key memory files (upcoming tasks, user profile, relevant project files)
- Reads CLAUDE.md Active Projects section
- Delivers a structured Recovery Briefing with: where we left off, what was completed, the ONE thing to do first, active project statuses, money progress, anything urgent

**When to run:** First thing at the start of any new session. After clearing conversation. Whenever context feels lost.

### 3. auto_handoff.py (`tools/auto_handoff.py`)
**Trigger:** Automatic, runs every time the session stops (Stop hook in settings.json)
**What it does:**
- Reads CLAUDE.md to extract Active Projects section
- Reads `memory/project_upcoming_tasks.md`
- Finds the most recent `*_save.md` file and references it by name
- Writes `handoffs/handoff_YYYY-MM-DD_HH-MM_auto.md` with project statuses + upcoming tasks
- If no /save was run: includes a WARNING and still captures project state from files

**This is the safety net.** Even if /save is never run, the auto packet has enough to give a useful (if less detailed) /recover briefing.

---

## Routing Table · Where Learnings Go

| Type of learning | Target file |
|---|---|
| User preference / how King David works | `memory/user_profile.md` |
| Project status changed | `memory/project_[name].md` + `memory/ACTIVE_PROJECTS.md` badge + CLAUDE.md one-liner |
| New project started | Create `memory/project_[name].md`, add to MEMORY.md + ACTIVE_PROJECTS.md + a CLAUDE.md one-liner |
| Permanent operating rule | `memory/feedback_operating_rules.md` |
| Rule about proceeding / executing | `memory/feedback_proceed_without_permission.md` or `feedback_always_execute.md` |
| DCEO email pattern learned | `DCEO_BRAIN/knowledge/email_patterns.md` |
| New DCEO procedure/protocol | New file in `DCEO_BRAIN/knowledge/` |
| AIS Challenge day completed | `memory/_archive/project_7day_challenge.md` (COMPLETE, archived) |
| Upcoming task priorities agreed | `memory/project_upcoming_tasks.md` (replace content) |
| Reference / framework explanation | `memory/reference_[topic].md` |

---

## Degradation Behaviour (if /save not run)
- /recover still works, reads auto packet + CLAUDE.md + upcoming tasks
- Briefing is less detailed (no session-specific accomplishments or decisions)
- WARNING appears in the auto packet so the gap is visible
- The system degrades gracefully, never fails silently

---

## File Naming Convention
- Detailed save: `handoffs/handoff_YYYY-MM-DD_HH-MM_save.md`
- Auto recovery packet: `handoffs/handoff_YYYY-MM-DD_HH-MM_auto.md`
- Both are preserved, never overwritten
