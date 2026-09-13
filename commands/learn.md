# /learn · Feed the Brain (Capture Skill)

**Trigger:** King says "I learned…", "remember this", "feed this to my brain", "add this to my brain",
"note this", "capture this", "save this fact", or types `/learn …`, OR hands over a fact, link,
screenshot or video he wants kept.
**Purpose:** The **frictionless front door for King to TEACH his brain.** King dumps a learning in plain
English (or a link/screenshot/video) and Claude files it in the right place, right format, indexed and
linked, so it's remembered every session forever. This is the **"Capture" reflex** (Nate: the hard part
of a second brain is getting what's in your head INTO the system, `knowledge\video_studies\2026-06-17_nate_second_brain_levels.md`).

> Pairs with: `/watch` (learn from a video), `/save` (end-of-session capture), `/search` (recall).
> `/learn` is the **on-demand "capture this NOW"** door.

## STEP 0 · If it's a video or link, watch it first
If King hands a video/URL, run **`/watch`** first to get the objective lesson, then `/learn` that lesson.
If it's a screenshot, read it directly.

## STEP 1 · Understand the learning
Read what King gives. Infer the core takeaway. Ask **one** clarifying question only if you genuinely
can't tell what the point is, otherwise just capture it.

## STEP 2 · Classify WHERE it belongs (don't make King decide)
- **How Claude should work / a preference / a correction** → `memory\feedback_<slug>.md` (type: feedback)
- **A fact about King / his life / goals** → `memory\user_<slug>.md` or a `project_*` file
- **A method / tool / how-to / external resource** → `memory\reference_<slug>.md`, or `knowledge\<slug>.md`
  for longer research
- **Project-specific** → that project's `CLAUDE.md` / `MANIFEST.md` / memory file
- **Already exists?** → EDIT the existing file, never duplicate.

## STEP 3 · Write it in the house format
- **memory\ files** get frontmatter:
  ```
  ---
  name: <kebab-slug>
  description: "<one line, used for recall>"
  metadata:
    node_type: memory
    type: feedback | user | reference | project
  ---
  ```
  Body = the learning in plain English. For feedback/project add **Why:** + **How to apply:** lines.
  Link related notes with `[[name]]`.
- **knowledge\ files** = a clean markdown note (title · the lesson · source/link if any).

## STEP 4 · Index + link
- Add a one-line pointer to **`MEMORY.md`** so it's discoverable: `- [Title](file.md), hook`.
- Cross-link to related notes with `[[wikilinks]]`.

## STEP 5 · Confirm (one line)
"✅ Learned: <what> → saved to `<file>`. I'll know this every session."

---

## INBOX MODE · process the raw-capture pile
**Trigger:** King says "process inbox", "clear the inbox", "file my inbox", or session-start reports items waiting.
**What it is:** `inbox\` is King's drop-anywhere door (laptop or phone via the GitHub mirror). Each note is a
raw dump that needs filing. INBOX MODE files them all using the same logic above.

**Process (Claude-in-the-loop, foreground, never a background/file-moving hook, to avoid the 15-min sync race):**
1. **List** every `inbox\*.md` **except** `inbox\README.md` and anything in `inbox\_processed\`.
2. **For each note**, run STEP 1, 4 above: understand it → classify WHERE → write it in the house format into
   the right `memory\` / `knowledge\` / `project_*` file (EDIT if it already exists, never duplicate) → index it
   in `MEMORY.md` + cross-link.
3. **Then move the original** to `inbox\_processed\<YYYY-MM-DD>_<slug>.md` (so it's archived, never lost, and the
   inbox is clean). Do the move in this turn so the working tree is settled before the next `KD_Brain_Sync`.
4. **Confirm** with a count: "✅ Filed N inbox items → [list of destinations]. Inbox clear."
- If a note is unclear, ask King **one** question rather than guessing (sacred accuracy, Rule #20).
- If a note is a link/video, run `/watch` first (STEP 0).

## Principle
**Frictionless for King.** He dumps it messy (even by voice); Claude does ALL the filing, formatting,
indexing and linking. King never has to know where things go. Keep every file under 500 lines.
