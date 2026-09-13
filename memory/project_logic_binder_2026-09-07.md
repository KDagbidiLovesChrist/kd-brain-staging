---
name: project_logic_binder_2026-09-07
description: "The night-shift binder: curated memory for Claude Code on LOGIC-B so King's Jarvis survives the laptop being off. Option B ruled by King 7 Sep; Stage 1 built and tested, Stages 2 to 3 pending."
metadata: 
  node_type: memory
  type: project
  originSessionId: 32296f14-bc6c-5b09-8bb4-fffa2fbf3340
  modified: 2026-09-07T17:00:55.774Z
---

# The Night-Shift Binder · LOGIC-B gets memory of King · 2026-09-07

## The ruling
King: "i want it to have memory of me" (7 Sep, about Claude Code on LOGIC-B with the laptop
off). Three options were laid out with the risk maths; **King chose Option B by quoting it
back verbatim**: a curated small binder, never the full brain, on the cloud box. Faith files
absolutely never. The engine's own brain switch on LOGIC-B stays EMPTY: the binder feeds
King's own Claude Code sessions only, never the mission pipeline, so the travel gate's hole
stays closed. Same day: "add 1b" accepted, **llama3.2:1b pulled onto LOGIC-B and verified**
(`ollama list` shows 1b + 3b), giving the box a fast local voice beside the pinned 3b.

## Stage 1 · BUILT AND TESTED (7 Sep), nothing has left the laptop
- `tools/logic_binder.py`: allowlist-only builder (5 files, nothing else can ship), reuses
  the proven `precompact_save.scrub()` secret scrubber, then line-level lane redaction
  (business, clients, finances, faith, beloved; the term list is in code), then a secret and
  forbidden-term scan that FAILS the build on one violation. Stages into gitignored
  `_private/logic_binder_out/`. NIGHT_LOG.md is never overwritten once the box writes it.
- Sources written: `tools/binder_src/CLAUDE.md` (who King is, how to speak, hard limits,
  "that lives at home" rule) and `tools/binder_src/RUNBOOK_LOGIC_B.md` (every service and
  fix procedure on the box, keep-warm rule, night log protocol).
- `tests/unit/test_logic_binder.py`: 10 real tests, 10 passing (planted ghp_ secret never
  ships, planted Klarnow line never ships, allowlist-only, idempotent, night log preserved,
  real sources scan clean). Added to `tests/real_coverage_gate.sh` in the same session per
  the gate rule.
- First real build: 5 files, 4 home-lane lines auto-removed, scan clean. Manifest shown to
  King (CLAUDE.md 2757 B · RUNBOOK 2707 B · CAMPUS_STATE.js 15453 B · HANDOFF.md 6680 B ·
  NIGHT_LOG.md 117 B).

## Stage 2 · SHIPPED AND VERIFIED (7 Sep, ~17:00 UTC, King's go: "im happy with 1" then
## "before we do mic test do stage 2")
Transport CHANGED from the original spec, flagged to King openly: no GitHub repo, no deploy
key. `tools/sync_binder_logicb.py` pushes the binder straight over the existing SSH door
(laptop initiates every network move, King's 29 Aug authority order; the box never holds a
write credential; no sixth copy of the data in another cloud) and pulls NIGHT_LOG.md home
in the same pass (push never touches the box's night log after seeding). First real sync:
all 4 files on the box at `/home/opc/kd-binder/`, each sha256 VERIFIED byte for byte, night
log seeded. Scheduled daily 21:00 as Windows task `KD_Binder_Sync` (laptop-bound work, per
the tools-safety rule), logging to `_private\binder_sync.log`.

## Not done yet (in order, each needs its moment)
1. Stage 3: Claude Code CLI installed on LOGIC-B (ARM Linux), King logs in once over SSH,
   binder as its CLAUDE.md; night log flows back to the laptop each morning.
2. The drill that proves it: laptop OFF, SSH from phone, `claude`, ask "who am I", hear it
   answer correctly.

## Context links
[[project_kd_robot_three_nodes_2026-08-29]] (LOGIC-B build, keep-warm applied same day,
commit b1d014c in the engine repo) · [[project_logos_backup_node_setup_2026-08-27]] (LOGIC-A
parked) · the campus map `_datacentre\KD_CAMPUS.html` (the binder ships its data file).
