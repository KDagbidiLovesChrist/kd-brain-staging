---
name: feedback_dceo_brain_privacy_boundaries
description: "Hard boundaries between King's personal home-brain and shared DCEO_BRAIN; enforce at file level, not assumption"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 99fc6207-9b74-4fbb-9a83-086916c18c2a
  modified: 2026-08-30T20:16:03.901Z
---

# DCEO Brain Privacy Boundaries

**Date Set:** 2026-08-30  
**Triggered by:** Found extensive personal home-brain content (personal projects, personal paths, personal money tracking) mixed into shared DCEO_BRAIN lifecycle skills (save.md, context.md)

## The Rule

**DCEO_BRAIN files are shared across all DCEOs and must NEVER contain:**
- Personal home-brain paths (C:\Users\Dell\.claude\* references)
- Personal projects (AIS Challenge, Newsletter, Lead gen, Fiverr gigs, Money Progress, etc.)
- Personal work tracking (upcoming tasks, personal habits)
- Personal learning references

**Why:** The DCEO_BRAIN folder may eventually be cloned/shared with other Amazon DCEO team members. King's personal business data must never bleed into shared files. This is a hard privacy and data-hygiene boundary.

## How to Apply

When writing or updating ANY file in DCEO_BRAIN (especially in `commands\lifecycle\` and `memory\`):
1. **Read the file before editing** to check if personal content has already leaked in
2. **Only reference paths** that start with `C:\Users\<workuser>\.claude\DCEO_BRAIN\` or relative paths within DCEO_BRAIN root
3. **Only reference projects** that are DCEO-work-related (shift status, patterns learned, procedures)
4. **Remove personal references immediately** if found during editing (examples: AIS Challenge status, Money Progress, Fiverr gig status, personal memory file paths)
5. **If unsure:** keep only DCEO-work scope; when in doubt, it belongs in the home brain, not here

## Examples of What STAYS OUT

❌ "AIS Challenge Status"  
❌ "Money Progress" (personal income tracking)  
❌ `C:\Users\Dell\.claude\memory\project_wat_newsletter.md`  
❌ References to Fiverr gigs, lead gen projects, personal business  
❌ Personal "upcoming tasks" (only DCEO work tasks belong here)

## Examples of What STAYS IN

✓ Email patterns learned during DCEO shifts  
✓ Incident types and how they were resolved  
✓ Escalation procedures used for DCEO work  
✓ Shift handover templates and procedures  
✓ `C:\Users\<workuser>\.claude\DCEO_BRAIN\knowledge\*` paths  
✓ DCEO work status tracking (tickets handled, risks flagged, etc.)

## Verification Trigger

If King notices personal content has leaked back in, the entire file should be rewritten to be DCEO-work-scoped (as was done with save.md and context.md on 2026-08-30).
