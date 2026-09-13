---
name: reference-brain-unification
description: "How King's brain stays ONE thing across laptop + phone: main is canonical (laptop auto-syncs to it), cloud/phone work lands on branches that must be MERGED into main, and heavy projects get a light-sync. The leak = unmerged branches, not broken sync."
metadata: 
  node_type: memory
  type: reference
  originSessionId: eefe8385-e0d9-4c29-b4f6-638899dc8ce0
---

# Brain Unification · keep it ONE brain (set 2026-06-20)

King's brain lives in 3 contexts; the rule is to keep them converged on **`main`**.

## The architecture
- **Laptop `C:\Users\Dell\.claude`** = the live brain. Auto-syncs to GitHub `main` every 15 min via
  `KD_Brain_Sync` (`tools\sync_brain.ps1`). Laptop == `origin/main` is the healthy state.
- **GitHub `KDagbidiLovesChrist/kd-brain`** = the cloud copy. The PHONE (Claude Code web) reads from here.
- **Phone** = Claude Code web on the repo. Sees whatever is on GitHub `main`.

## The leak we hit (2026-06-20) · and the fix
- **Symptom:** "phone work feels pointless / brain not synced / confusing." House project invisible from phone.
- **Real cause:** sync was NOT broken, it was **unmerged branches.** Cloud/phone sessions (Claude Code web)
  work on a **branch** (e.g. `claude/king-pipeline-reorganize-…`), which **never auto-merges to main.** So
  laptop `main` and the branch diverged (split at the last common commit) and neither had the other's work.
- **Fix:** **merge the branch(es) into `main`** (backup first), resolve conflicts keeping BOTH sides, push.
  Then laptop + GitHub + phone all see one brain.

## STANDING RULE (apply every time)
1. **After any cloud/phone (Claude Code web) session, MERGE its branch into `main`**, don't leave work on a
   stray branch. Check `git branch -r` for unmerged `claude/*` branches; merge + push them.
2. **Backup before merging** the whole brain: `git branch backup/pre-unify-<date>`.
3. **Pause `KD_Brain_Sync` during a merge** (`Disable-ScheduledTask -TaskName KD_Brain_Sync`) so it can't
   commit a half-merged/conflicted state; **re-enable after** (`Enable-ScheduledTask`).
4. **Heavy projects (videos/renders/GBs) stay OUT of the lean brain** (e.g. `Documents\7 adderig farm`).
   To make one visible on the phone, **light-sync** only its markdown specs + small images into
   `knowledge\<project>\` and mark it a READ-ONLY snapshot (source of truth = the laptop folder). See
   `knowledge\7adderig_farm\README_SNAPSHOT.md`.
5. **Keys never go in the repo** (gitignored). For the phone, add them as **cloud secrets**
   (code.claude.com → environment → secrets), e.g. `GEMINI_API_KEY` for `/watch`.

Related: [[project-brain-on-github-phone]] · [[reference-second-brain-levels]] · [[feedback-feed-the-brain]].
