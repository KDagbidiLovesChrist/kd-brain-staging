---
name: reference-brain-integrity-gate
description: "The brain's two read-only link/ref gates + the contradiction-sweep method, and the 2026-07-05 deep-sweep results."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 8ccf124b-2333-453a-8b79-46c55a6b8fec
---

The brain has TWO read-only link/reference gates (run both from `.claude`, exit 0 = clean):
- `tools/qa_ref_check.py` — refs inside `commands/` + `skills/**/SKILL.md` (the operational skill defs). The one `/qa-master` already calls.
- `tools/brain_link_scan.py` — NEW (2026-07-05): checks ALL 3 link styles the brain uses, `[[wikilink]]` (resolved via a `name:` frontmatter + basename index), `[text](path)` markdown links, and backtick Windows-paths, across `memory/ _ops/ commands/ knowledge/` + root hub docs. It HARD-FAILS only on a broken link to a **synced-brain doc that should exist**; laptop-only `tools/*.py` + `workflow/*.md` refs and unresolved `[[wikilinks]]` are INFO (the memory system treats an unresolved wikilink as a valid forward-marker). Excludes `backups/ brain_backup/ archive/ .tmp/`. Honors `LAPTOP-ONLY` / `MISSING` flags on the line, same convention as qa_ref_check.

Both are now wired into `/qa-master` (Rule 19/21). **Contradictions have NO automated tool** (Rule 19 stays a manual/LLM pass): sweep via ~9 cluster subagents (active projects · standing rules · references · _ops law · commands · root hubs · faith · knowledge · skill-counts), each checking internal consistency + against the canonical hubs (CLAUDE.md rules, MEMORY.md CURRENT, ACTIVE_PROJECTS.md), then verify before fixing. Scale to stakes; leave dated snapshots frozen.

**Deep sweep 2026-07-05 (via `/aide` → systematic-debugging + this method): brain fundamentally healthy.** Fixed: 2 planned-scoreboard refs flagged (`engine.md`, `THE_ENGINE.md` → `_ops/SWEEP_SCOREBOARD.md`, MISSING-flagged); command count corrected 53→54 and total →111 across ~13 live files (a `/engine` command was added); test-tracking reconciled to README's honest ~2,020 tests / ~1% line coverage (CLAUDE.md was stale at 1,007/25%); YouTube own-voice-clone disclosure aligned to **disclose-by-default** in `/video-edit`; cold-outreach **KILL guard** prepended to `/cold-email` `/monetize` `/setup_hours` + `feedback_pivot_to_global_market.md`; `/autopilot` given an **HITL publish gate** (no auto-post without King); car loan corrected €3,300→**€3,500** (King confirmed). **Faith lesson count:** left untouched this session (King unsure at the time); **subsequently confirmed 34 canonical** (King, per MEMORY 07-10), stale 32/36/37 citations to be synced to 34 (sacred ground; doctrine → Fr Bogdan). `.tmp/` = 204MB temp, safe to clear on King's yes; mirror dirs already gitignored. See [[reference-androo-live-cockpit]].
