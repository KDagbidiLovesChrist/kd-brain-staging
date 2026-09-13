---
name: reference-notion-brain-mirror
description: How the main brain mirrors to Notion + the 3 desktop doors + the Obsidian Canvas map + the Obsidian Skills. Built 2026-07-01.
metadata: 
  node_type: memory
  type: reference
  originSessionId: baa74a4b-f89b-4ed4-bdda-dff72af272b1
  modified: 2026-08-02T04:06:22.914Z
---

# The Notion brain mirror + desktop doors + Canvas map (built 2026-07-01)

## Notion mirror of the MAIN brain
- **Script:** `tools\notion_brain_sync.py`, reuses the proven faith-sync pattern (`the-truth\tools\notion_sync.py`):
  reads `NOTION_TOKEN` from `.env.master`, converts markdown → Notion blocks, then **updates every page in place**
  (`upsert_page()`, added 2026-08-02) instead of trash-and-recreate.
- **2026-08-02 fix:** the old `archive_old_containers()` step trashed the "KD Main Brain" child page and rebuilt
  a fresh one on every sync (any edit to CLAUDE.md/MEMORY.md/CREED.md/FOUNDATION.md/KING_OS_BREAKDOWN.md/
  THE_JOURNEY.md triggered it via the 30-min autosync task) — nothing was lost, but it fired a scary "moved to
  Trash" Notion notification every time and swapped the page's id. Replaced with `upsert_page()`: finds the
  existing child page by title (`find_child_page()`), clears its blocks (`clear_children()` + paginated
  `get_all_children()`), and refills it via PATCH — same page id survives across syncs, no more Trash banner.
  Applies to the container AND all 7 sub-pages (King OS, Journey, Foundation tile, Creed, Foundation doc,
  Active Projects, Memory index). Tested: `--dry` run (17-129 blocks/page, clean) + one live run against the
  real page (confirmed `[~] updating existing page` reuse path, no archive calls). Root cause of the trigger
  that day: an unrelated MEMORY.md edit from a different session tripped the fingerprint check.
- **Curated first version** (King chose "show me before expanding"): a front door (God at the centre + the
  God-limit truth + a link to the live site) + **🏛️ The Foundation** (CREED + FOUNDATION) + **📂 Active Projects**
  (parsed live from `CLAUDE.md`) + **🧠 Memory index** (`MEMORY.md`) + an **embedded live brain map** (the DCIM site).
- **King's page:** "KD Main Brain" (id `390cbf0d40988013b18ad654e054e3ec`), shared with the **KD Brain Sync** connection.
  Run: `python tools\notion_brain_sync.py "<page url>"` (or `--dry` to assemble blocks with no Notion call).
- **Auto-refresh:** `tools\notion_brain_autosync.py` (fingerprints CLAUDE.md/MEMORY.md/CREED.md/FOUNDATION.md;
  re-syncs only on change) + Windows task **`KD_Brain_Notion_Sync`** (every 30 min, silent via pythonw).
  State + log outside the repo: `.notion_brain_sync_state` / `.notion_brain_sync.log`.
- **DCEO stays behind the work wall**, never mirror real Amazon/work data into personal Notion.
- Notion has **no native graph** like Obsidian, so the "connection map" is the **embedded live map**; if the site
  blocks iframing it shows as a link and the live-site door opens it full.

## The 3 desktop doors (on the Desktop, `.url` shortcuts)
- **KD Brain - Living Centre** → `https://kd-brain-dcim.vercel.app` (the God-centred live site).
- **KD Brain - Notion** → the KD Main Brain Notion page (points at King's stable page, survives re-syncs).
- **KD Brain - Obsidian** → `obsidian://open?vault=5d71cb4dd561cb47` (the `.claude` vault id).

## The Obsidian Canvas brain map
- **File:** `_ops\BRAIN_MAP.canvas`, a JSON Canvas 1.0 mind-map: **God** at the centre, **★ Theosis** the summit,
  the **5 sub-brains** (Core/Infra · Work-DCEO · Money · Faith-public · Theosis-private) each with key nodes,
  brand colours. Opens + is editable in Obsidian Canvas. Built with the new **json-canvas** skill.
- Edit/extend it with the `json-canvas` skill; validate ids-unique + edges-resolve after any change.
- **v3 readability rules (2026-07-03, King's "isn't filled out" fix):** Obsidian HIDES node text when zoomed
  out, wrap every cluster in a labeled **group** (labels stay visible at any zoom) and make the group wide
  enough for its label (~16 canvas px/char + 60) or it truncates. Headings `#`/`##` inside nodes; keep the
  whole map ≤ ~3100 canvas units wide so text renders at fit-zoom. QA loop = `scratchpad qa_canvas.py`
  pattern: validate JSON + containment/overlap/label-fit + render a PIL preview and eyeball it.

## The Notion map mirror (2026-07-03)
- The KD Main Brain front door now mirrors the map: ✨ Summit → ✝️ God the Source → the 5 halls as coloured
  callouts (blue Core · purple Faith · gray Work · green Money · orange Formation), then the live embed + tiles.
  Built by `map_mirror_blocks()` in `tools\notion_brain_sync.py`.
- **⚠️ Notion icon gotcha:** callout icons must be TRUE emoji, text symbols like `★` are rejected with a 400
  validation error (use ✨ instead). Verify pushes via the blocks API, not just exit 0.

## Obsidian Skills (official, installed 2026-07-01)
- `kepano/obsidian-skills` (Steph Ango, Obsidian CEO; MIT). 5 skills in `skills\`: **obsidian-markdown** (wikilinks/
  callouts/properties), **obsidian-bases** (database views), **json-canvas** (mind-maps), **obsidian-cli** (needs the
  optional `obsidian` CLI), **defuddle** (clean web→markdown for research, needs optional `npm i -g defuddle`).
- Pure-instruction, vetted safe. Logic Tier **T1**. Registered in `skill-forge\MANIFEST.md` (#16). They give Claude
  native Obsidian authoring; use them when writing notes, Bases, or Canvas maps.
