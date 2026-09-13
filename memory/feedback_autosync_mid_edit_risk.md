---
name: feedback_autosync_mid_edit_risk
description: "The 15-minute auto-sync task can commit and push mid-edit, between two steps of a multi-step file change, landing a broken snapshot on record. Happened twice: once reaching origin/main briefly (26 Aug), once caught local-only (4 Sep). Verify with a real import/run before trusting any auto-sync commit as ground truth."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-04T05:07:30.862Z
---

`sync_brain.ps1` commits and pushes every 15 minutes regardless of whether the working tree is mid-edit. A multi-step change (splitting a file into two, editing several files that must land together) can get captured between its own steps, producing a syntactically valid but functionally broken commit.

**Why:** happened twice now.
1. 26 Aug: a security-fix repair was mid-edit when auto-sync fired, landing a broken test script on `origin/main` briefly (see `project_security_posture_2026-08-26.md`).
2. 4 Sep: splitting `tools\progress_board.py` (to stay under the 500-line rule) into `progress_board_iotas.py` plus a re-import happened as two separate tool calls; auto-sync fired between them and committed the intermediate state (`STAGE_LADDER` referencing names no longer defined in the file, a `NameError` on import). Caught before pushing: `git fetch` + `git merge-base --is-ancestor` confirmed the broken commit had not reached `origin/main`, then the corrected version (verified with a real `import progress_board` and the full test suite) was committed on top and pushed. See [[project_kd_robot_three_nodes_2026-08-29]].

**How to apply:** after any multi-step edit that spans more than one tool call and touches import/dependency relationships between files (a split, a rename, a signature change propagated across callers), run a real import or execution check (`python -c "import <module>"`, the relevant test file) **before** the next `git status`/commit, since an auto-sync cycle may have already landed between your edits. If `git status --short` shows a file as unexpectedly clean (already tracked, no diff) right after creating it, that is a signal auto-sync got there first, not a bug in your own tooling; check `git log` for a recent `auto-sync` commit and diff it before assuming the working tree matches what you last wrote. When a broken commit is found: check with `git merge-base --is-ancestor <broken-sha> origin/main` whether it already reached GitHub before deciding how urgently to fix it. Never assume an auto-sync commit is safe just because it exists; verify, then commit the correction on top.
