---
name: obsidian-bom-cdp-debug
description: "Two proven gotchas+fixes from the 3D graph install (2026-07-04) - PowerShell BOM breaks plugin JSON, and CDP is the way to debug Obsidian live"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 89977113-b405-4a28-8d60-718e8c407d1a
---

# Obsidian plugin debugging · the BOM trap + the CDP door (proven 2026-07-04)

**Context:** installing the `3d-graph-new` community plugin into the `.claude` vault. Global 3D graph rendered blank. Root causes found and fixed, both reusable.

## Gotcha 1 · PowerShell 5.1 writes JSON with a BOM → Obsidian plugins silently break
- `Set-Content -Encoding utf8` (PS 5.1) prepends a UTF-8 BOM (`﻿`).
- Obsidian's `JSON.parse` of plugin `data.json` throws `Unexpected token '﻿'` and the plugin **silently falls back to default settings** (no visible error).
- **Fix:** write plugin JSON with Python (`open(p,'w',encoding='utf-8')`) or the Write tool. Never PS 5.1 `Set-Content utf8` for JSON another program parses.

## Gotcha 2 · debugging a live Obsidian = launch with the CDP port
- `Obsidian.exe --remote-debugging-port=9222` (exe at `%LOCALAPPDATA%\Programs\Obsidian\Obsidian.exe`).
- Python + `websocket-client` (installed) with **`suppress_origin=True`** (else 403 Forbidden).
- `Runtime.evaluate` gives full app access: `app.vault.getMarkdownFiles().length`, `app.plugins.plugins`, `app.commands.executeCommandById(...)`, leaf types via `app.workspace.iterateAllLeaves`, and the real console errors.
- Working scripts pattern saved in this session; rebuild from this note if needed. Port closes on normal restart.

## 3D graph plugin facts (3d-graph-new 1.1.11) - FULL FIX CHAIN (proven 2026-07-04, 3 layers)
- Default `maxNodeNumber: 1000` → **blank global graph** on vaults bigger than that. Set to 4000 in `.obsidian/plugins/3d-graph-new/data.json`.
- **Layer 1 · the plugin's search filter is INERT** (all engines: default/builtIn/dataview) - searchQuery in data.json does nothing; with orphans ON it graphs ALL vault files (8,157 incl. .py/.json). **Fix = patch `main.js`**: in `Graph.createFromApp`, both `app2.vault.getFiles()` calls got `.filter(f => f.extension==="md" && !NOISE_REGEX.test(f.path))` (noise = .obsidian, _datacentre, handoffs, plans, backups, drafts, sessions, templates, etc. - same folders as the 2D graph filter). ⚠️ A plugin UPDATE overwrites this patch - re-apply after updating.
- **Layer 2 · Obsidian's link index can stall** (likely from force-killing the app mid-index): `metadataCache.resolvedLinks` stuck at 430/2,100 sources, MEMORY.md showing 0 of its 188 links, while `getCache()` per-file link lists were fine. **Fix (CDP or console):** `app.vault.getMarkdownFiles().forEach(f=>app.metadataCache.resolveLinks(f.path)); app.metadataCache.trigger('resolved')` - heals the whole index and makes the plugin rebuild.
- **Layer 3 · camera + fit:** view object path = `leaf.view.graph3dView.forceGraph` (or `.instance`) → `.zoomToFit(1000,60)` frames the galaxy.
- Hall colours: `groups` in data.json `temporaryGlobalGraphSetting` = same 6 queries/colours as `.obsidian/graph.json` (gold #C9A84C God/_ops · purple #C678DD apologetics · blue #4A90D9 the-truth · brick #8D6E63 DCEO · green #98C379 Money · cyan #56B6C2 Core). Perf: showLinkArrow off, orphans ON is fine post-patch (825 nodes, 260 links).
- View type `3d-graph-view-global`; commands `3d-graph-new:open-3d-graph-global` / `-local`.
- Plugin config + patch are laptop-local (`.obsidian` gitignored) - redo per device, e.g. when [[project-brain-on-github-phone]] adds iPhone Obsidian.
