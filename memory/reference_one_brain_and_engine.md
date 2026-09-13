---
name: reference-one-brain-and-engine
description: "The one-brain unification (God-centre + 5 halls), THE ENGINE yardstick, and the free-Llama skill sweep (2026-07-10)"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 38f384dd-1b21-443a-90ab-197c36cea65a
---

# The One Brain + The Engine + The Sweep (2026-07-10)

## The One Brain (Obsidian, God-centre + 5 halls)
Rebuilt the vault to King's canonical [[creed]] + DCIM model: **God at the centre** (gold), 5 halls orbiting: ⚡ Core (cyan) · 🛠️ Work/DCEO (brown) · 💰 Money (green) · ✝️ Faith-public (purple) · 🕊️ Theosis (blue, the summit). 958 notes classified into `brain/` MOCs. Both the native Obsidian graph AND the 3D showpiece (`_ops/BRAIN_DASHBOARD_3D.html`) now render the SAME structure = **one brain**. King approved the look.

Tools (all FREE/local, re-runnable):
- `tools/brainify.py` — scans the vault, classifies notes into God + 5 halls, writes `brain/BRAIN.md` + `brain/HALL_*.md` MOCs. Rerun to refresh as the brain grows.
- `tools/patch_graph_brain.py` — colours the halls in `.obsidian/graph.json` (2D) + `3d-graph-new/data.json` (3D), hides vendored skills/plugins noise. **RUN WITH OBSIDIAN CLOSED** (Obsidian rewrites graph.json on exit and would clobber it).
- `tools/tune_graph_light.py` — lightens 2D physics (repel down, centre up, tighter links) to kill the lag on ~900 nodes.

LESSONS:
- Obsidian's graph feeds on `[[wikilinks]]`; the vault was hub-and-spoke MARKDOWN links, so it rendered sparse. MOC hubs + wikilinks = the cortex.
- JSON configs written by Python/Write only, never PowerShell Set-Content (BOM breaks Obsidian silently). Backups in `backups/brain_engine_backup_2026-07-10/`.
- Automated screenshots kept losing focus to VS Code/Edge; King's own eyes are the final visual QA.

## THE ENGINE (the pay-grade yardstick)
`_ops/THE_ENGINE.md` = King's own Rules 17/21/25 + WAT as ONE canonical standard. 6 marks scored /12: goal-locked · stack-stated · proven-pattern · honest-scope · QA-gate · WAT+Logos. `commands/engine.md` = `/engine` runs any task or skill through it. The sweep measures every skill against this.

## The Free-Llama Sweep
`tools/sweep_audit.py` scores skills vs the engine on **LOCAL Ollama llama3.2** (FREE — King's constraint: no paid agent fleets). Output: `_ops/SWEEP_SCOREBOARD.md`.
- KEY: llama3.2 (3B) scores are NOISY — trust the PATTERN, not the numbers. Claude's real read overrode Llama on `seedance-site` + `content-engine` (already pay-grade despite low Llama scores). The one systemic finding: **no QA gate across the money engine.**
- FIX: `tools/add_gate.py` appends THE GATE (QA + `/humanize` + engine reflex) to skills lacking one (guard skips already-gated; takes skill names as args). **17 skills brought to pay-grade** this session (9 money doors + 8 wave-2 output-producers). Utilities + `/faith` deliberately left alone (they don't need a generic gate).

## To refresh the brain later
Close Obsidian, then: `python tools/brainify.py && python tools/patch_graph_brain.py && python tools/tune_graph_light.py`, then reopen Obsidian.

See also: [[creed]] · [[reference-brain-dcim]] · [[feedback-lean-spend-llama-routing]]
