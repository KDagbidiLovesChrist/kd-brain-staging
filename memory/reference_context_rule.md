---
name: reference-context-rule
description: "500 line hard limit per file, /context skill scans global + project scope, summarise old content to keep context clean"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 6f964ee4-5853-4922-a11d-d4847ec0d5bc
---

# Context Quality Rule

## The Rule
Every file in the system must stay under **500 lines**. This is a hard limit, not a guideline.

**Why it matters:** Claude reads files fully. A 1000-line file splits Claude's attention across too much content. A 400-line file gets full focus. Full focus = 100% accurate answers. Bloated files = diluted answers.

## The /context Skill
**Auto mode:** Runs at the start of every session (Rule 11 in CLAUDE.md), scans files, flags issues, waits for approval before fixing.
**Deep mode:** Triggered by `/context`, full review of content quality, semantic duplicates, detailed diagnosis before any changes.

## What Gets Scanned
- **Global brain:** `C:\Users\Dell\.claude\`, all .md files in memory\, commands\, DCEO_BRAIN\, root
- **Current project:** The active project folder (Newsletter, Scrapers, etc.), all .md files

## How Files Get Fixed
- **Over 500 lines:** Historical/outdated sections get compressed into a `## Historical Summary` block (key points only). Active content stays unchanged.
- **Duplicate files:** Logic-based decision on which is authoritative. Best content merged into one file. MEMORY.md updated.
- **Long conversation:** Run /save, then start fresh session and /recover.

## What Is NOT Done
- Files are never deleted, only compressed or merged
- Active/recent content is never touched, only historical sections get summarised
- Nothing is fixed without approval from King David first
