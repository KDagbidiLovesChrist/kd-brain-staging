# /new-project · Project Scaffolding Skill

**Trigger:** User types `/new-project <name>` OR says "start a new project", "set up a folder for…",
"new build for…", "scaffold a project", "make me a project folder"
**Purpose:** Build a new project folder in King's standard Nate WAT structure in ONE move, so the
folder structure is automatic, never hand-built, and everything used inside it is tracked. No more
keeping it straight in a separate doc.

**Also auto-offer:** Whenever you (Claude) start working in a folder that is meant to be a project but
is missing the standard structure (no `CLAUDE.md` / no `workflow/`+`tools/`), proactively SAY:
"This folder isn't set up in the standard structure, want me to run /new-project on it?" Don't wait to
be asked. (CLAUDE.md Operating Rule #14.)

---

## STEP 0 · Discovery first (CLAUDE.md Rule #13)
Before scaffolding, ask King a quick WAT intake (keep it short, plain English):
1. **What is it?**, one line, who it's for.
2. **Money angle**, how does it make money (price, one-off vs recurring, client)?
3. **Tools/APIs**, what will it likely use (Firecrawl? Gemini? Vercel? Supabase? Gmail?).
4. **A `/command`?**, does this deserve its own project-local skill later?

If King already gave a name + enough detail, skip the questions and proceed.

---

## STEP 1 · Scaffold the folder
Run the scaffolder (it copies `templates/project-template/` and fills in name + date):

```
python tools/new_project.py --name "<name>" --one-liner "<one line from discovery>"
```

- Folder location: `--path <dir>`, else `$KD_PROJECTS_DIR`, else `<repo-root>/projects/`.
- On King's Windows machine, projects usually live in `C:\Users\Dell\Documents\`, pass
  `--path "C:\Users\Dell\Documents"` there.
- The script refuses to overwrite a non-empty folder, pick a new name if it stops.

This creates: `CLAUDE.md` · `MANIFEST.md` · **`TRUST_LEDGER.md`** (the project's Foundation-Pipeline stone ledger) · `.env.example` · `workflow/_sop_template.md` · `tools/` · `commands/` · `sessions/_session_template.md` · `.tmp/`.

---

## STEP 2 · Fill the brain + manifest from discovery
- Open the new `CLAUDE.md` and fill in **What this is** + **Money angle** from STEP 0.
- Open the new `MANIFEST.md` and seed the **Tools** / **APIs / Keys** rows with what STEP 0 named.
- Rename `workflow/_sop_template.md` to the real SOP name and write the first steps.

---

## STEP 3 · Register in the master brain
Add the project to master `CLAUDE.md` → **Active Projects** section:
- A status badge line (🆕 NEW) with the one-liner.
- A pointer to the folder + its `MANIFEST.md`.

---

## STEP 4 · Confirm
Tell King in plain English:
- Where the folder is.
- What's inside (the structure).
- The ONE next step (usually: add `.env` keys, then build the first tool).
- Remind: MANIFEST + sessions/ keep it all tracked automatically going forward.

---

## Tracking model (why this exists)
- **`MANIFEST.md`** = the live "what's in this folder" view. Update it whenever a new tool, skill, API
  or key output is used in the project. One glance shows every moving part.
- **`sessions/`** = the full history. `/save` already writes a `session_<DATE>.md` copy into each
  project, that's where the per-project log lives.
- Together: live view + history = King always knows exactly what each folder is using, without a
  separate tracking doc.
