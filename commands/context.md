# /context · Context Quality Guardian

**Trigger:** User types `/context` OR says "check context", "context health", "are we losing context", "check files"
**Auto-trigger:** Runs automatically at the start of every session before any other task (auto mode, quick scan only)
**Purpose:** Keep every file under 500 lines, eliminate duplicates, and flag when the conversation is getting too long, so Claude always operates at 100% accuracy, never on diluted context

---

## TWO MODES

### AUTO MODE · runs at session start, every time
Quick scan. Report only. Do NOT fix anything without approval.

### DEEP MODE · runs when user types /context
Full review + diagnosis. Reads actual file content, not just line counts. Fixes after approval.

---

## STEP 1 · Run the scanner
Execute the context check script to get a file size report:
```
python C:\Users\Dell\.claude\tools\context_check.py
```

This scans two scopes:
- **Global brain:** All .md files in `C:\Users\Dell\.claude\` (CLAUDE.md, memory\, commands\, DCEO_BRAIN\)
- **Current project:** All .md files in the current project folder (if one is open)

Read the output carefully before proceeding.

---

## STEP 2 · Check MEMORY.md for duplicate entries
Open `C:\Users\Dell\.claude\memory\MEMORY.md`.
Look for:
- Two entries that describe the same topic
- Two filenames that sound very similar (e.g. `project_newsletter.md` and `project_wat_newsletter.md`)
- Entries pointing to files that no longer exist

Note any issues found.

---

## STEP 3 · Check conversation length
Estimate the current conversation length:
- **SHORT**, under 20 exchanges, context is clean
- **MEDIUM**, 20, 50 exchanges, context is adequate but watch it
- **LONG**, 50, 80 exchanges, context is degrading ⚠️
- **CRITICAL**, 80+ exchanges, answers may no longer be 100% reliable, fresh start recommended 🚨

---

## STEP 4 · Deliver the Context Health Report

Always use this exact format:

```
╔══════════════════════════════════════╗
║      CONTEXT HEALTH CHECK            ║
╚══════════════════════════════════════╝

FILES OVER 500 LINES [global brain]
────────────────────────────────────
  • [filename], [X] lines ⚠️
  (or: All files within limit ✓)

FILES OVER 500 LINES [current project]
────────────────────────────────────
  • [filename], [X] lines ⚠️
  (or: No project open / All files within limit ✓)

POSSIBLE DUPLICATES OR CONFLICTS
────────────────────────────────────
  • [file A] and [file B], may overlap ⚠️
  (or: No duplicates detected ✓)

CONVERSATION LENGTH
────────────────────────────────────
  Status: [SHORT ✓ / MEDIUM ✓ / LONG ⚠️ / CRITICAL 🚨]
  [If CRITICAL: Recommend /save then fresh session]

OVERALL STATUS
────────────────────────────────────
  [✓ All clear, context is clean and sharp]
  [⚠️ X issue(s) found, review below]

══════════════════════════════════════
[AUTO MODE]: Say "fix it" to resolve all issues, or name specific ones.
[DEEP MODE]: Detailed diagnosis follows below.
══════════════════════════════════════
```

---

## STEP 5 · DEEP MODE ONLY: Detailed diagnosis
(Skip this step in auto mode)

For each flagged file over 500 lines:
- Read the file
- Identify which sections are recent/active (keep these exactly as-is)
- Identify which sections are old/historical (summarise these)
- State specifically: "I will compress lines X, Y into a summary. Here's what the summary will say: [preview]"
- Wait for approval before making any changes

For each possible duplicate pair:
- Read both files
- Compare content
- State specifically: "File A is more current/specific. I recommend [keeping A / merging B into A / clarifying the difference]"
- Wait for approval

---

## STEP 6 · Fix (only after approval)

### Fixing files over 500 lines:
1. Identify all historical/outdated sections
2. Write a `## Historical Summary` block compressing the key points (max 10 bullet points)
3. Replace the historical sections with this summary block
4. Verify the file is now under 500 lines
5. Confirm to King David: "Compressed [file] from [X] lines to [Y] lines ✓"

### Fixing duplicate/conflicting files:
1. Read both files fully
2. Use logic: which is more current? More specific? More referenced?
3. Merge the best content into the authoritative file
4. Remove or archive the weaker file
5. Update `MEMORY.md` index to reflect the change
6. Confirm: "Merged [file B] into [file A]. [file B] removed. MEMORY.md updated ✓"

### Fixing long conversations:
1. Run `/save` to lock in all progress
2. Tell King David: "Session saved. Start a fresh Claude Code session and type /recover to pick up exactly where we left off."

---

## THE 500 LINE RULE
This is a hard limit, not a suggestion. Every file in the system must stay under 500 lines.
Why: Claude reads files fully. If a file is 1000 lines, Claude splits its attention. If it's 400 lines, Claude has full focus. Full focus = 100% accurate answers.

---

## WHEN TO RUN /context
- **Automatically:** First thing every session, before any task (auto mode)
- **On demand:** Any time you say "check context", "how's our context", "is context ok"
- **Proactively:** Before any complex multi-step task, confirm context is clean first
- **After any big /save session**, verify the saved files didn't bloat
