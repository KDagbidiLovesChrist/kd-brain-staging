---
name: feedback_republish_artifact_alongside_local_board
description: "The KD Robot progress board has two live copies (the local file served at 127.0.0.1:5056, and a claude.ai artifact King checks from his phone). Rebuilding the local file does not update the artifact; both must be republished together, every time."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ae01ba25-a571-403d-b5ba-1c8458631cfc
  modified: 2026-09-04T05:07:16.925Z
---

Whenever `_ops\PROGRESS_BOARD.html` is rebuilt, republish the claude.ai artifact copy in the same step, not just the local file.

**Why:** discovered 4 Sep 2026 when King asked "so stage R is finish why isnt p&p updated" after rung R had genuinely closed and the local board was already correct. The local board (served via `ollama_gui.py` at `127.0.0.1:5056/brain/PROGRESS_BOARD.html`) and the claude.ai artifact (`https://claude.ai/code/artifact/bff54c23-d37e-4c0c-89ad-ee166e5bb104`, titled "KD Robot Progress") are two separate publish targets built from the same file. King checks the artifact link from his phone, not the localhost URL, so a fix that only touches the local copy is invisible to him even though the underlying data is genuinely current. The artifact tool's own description confirms this: a claude.ai artifact is static and "can only be republished fresh," it never auto-syncs from a local file changing.

**How to apply:** any time `tools\progress_board.py` rebuilds `_ops\PROGRESS_BOARD.html` (a manual run, a code fix, a new iota added), immediately follow with `Artifact.publish` on the same file path against the existing artifact URL. Treat the two as one atomic step, never sequential-and-separate. This is distinct from the live-loop-restart issue ([[feedback_autosync_mid_edit_risk]] is a different failure mode: stale in-memory code, not a stale artifact) though both should be checked together after any board code change: rebuild the file, restart the `KD_Progress_Board` loop task so it serves the new code, republish the artifact. Related: [[project_kd_robot_three_nodes_2026-08-29]].
