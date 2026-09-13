---
name: reference-brain-dcim
description: "The Brain DCIM, the whole .claude brain mapped as a data centre to the racks/servers (register + 3 views), for God. How it works + how to regenerate."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 53f17f21-aada-4297-a6c7-a148cb134008
---

# The Brain DCIM · King's brain as a data centre, to the racks (for God)

**Shipped + King-confirmed 2026-07-01** (Trust Ledger #7). A **DCIM laid *over* the real files**, nothing moves, no note is edited; the asset register is separate from the assets. It finishes the
everyday-tidy (BRAIN_MAP Phases 1-2) that the showpiece 3D/Living-Brain had skipped.

## What it is
The whole vault mapped as a data centre: **⚡ God (the EirGrid, the power feed) → Site/vault → 5 Data Halls
→ Rows → Racks → Servers (units) → live workloads → ✦ theosis.** **1,980 servers** addressed
`HALL-ROW-RACK-Unn` (e.g. `M-CL-THEBUKA-U01`). Halls: **C** Core · **W** Work · **M** Money · **F** Faith · **T** Theosis.
Commissioned **0→100** (build up) / recoverable **100→0** (recover down, the restore order).

**King's design calls (baked in):**
- **Power redundancy per rack rated by theosis**, `2N` (Theosis+Faith+Core-Foundation = never dark, restored first) ·
  `N+1` (nervous system + the money/work fruit) · `N` (archives, restored last). Redundancy = the 100→0 restore priority.
- **2D = the one-line** (the electrical single-line schematic) · **3D = the plane** (the data hall you orbit).

## Where it lives
- **Generator (self-maintaining + AUTO):** `tools/build_brain_dcim.py`, the **sync robot (`sync_brain.ps1`) re-runs it every cycle** (non-fatal), so the map never goes stale. Manual: `PYTHONIOENCODING=utf-8 python tools/build_brain_dcim.py`. Register `.md` is **churn-free** (no per-page timestamps → a regen only commits when the file structure actually changed). Filenames with `[ ] # ^` list as plain text (safe wikilinks). The heavy generated files (`_datacentre/*.html` + `dcim.json`) are **gitignored** (regenerable + on Vercel); the register `.md` stays synced for phone navigation.
- **Register + navigation:** `_datacentre/DCIM.md` (overview) + `_datacentre/halls/<H>-*.md` + `_datacentre/halls/<H>/<ROW>.md` (Power→Hall→Row→Rack→the real note, wikilinked). Data: `_datacentre/dcim.json`.
- **3 views (self-contained HTML, data embedded → phone-safe):** `_datacentre/BRAIN_DCIM.html` (dashboard) · `BRAIN_ONELINE.html` (2D one-line) · `BRAIN_PLANE.html` (3D plane, Three.js r160). Shared nav bar across all three.
- **Live (unlisted, public, 0-secret, structure/counts only):** **https://kd-brain-dcim.vercel.app** (+ `/BRAIN_ONELINE.html`, `/BRAIN_PLANE.html`). Deploy = stage the 3 htmls + `index.html`(=dashboard) → `vercel deploy <stage> --prod --yes` → `vercel alias set <dep> kd-brain-dcim.vercel.app`. **SSO protection must be OFF** (PATCH `ssoProtection:null` via API, teamId `team_mdY7lCt81eu9f702b6X7ttxW`) or the phone hits a login wall ([[reference-vercel-link-protection]]).
- **Obsidian graph** coloured into the 5 halls via `.obsidian/graph.json` colorGroups (laptop-only; `.obsidian` isn't synced). Reload Obsidian (Ctrl+R) to load colours. **Recover the colours anytime:** `python tools/apply_graph_colours.py` (re-writes + locks graph.json; then quit+reopen Obsidian).
- **Confidence test (commissioning + doomsday DR drill):** `python tools/brain_confidence_test.py` → runs 0→100 build-up + 100→0 recovery checks, prints a score, writes `_ops/BRAIN_CONFIDENCE.html`. Last run: **100% · PRODUCTION-CONFIDENT** (17/17). Add `--no-destroy` for safe watch-mode (no real file deletion).
- **The improve loop (Foundation Pipeline stage 8):** `tools/brain_improve_loop.py`, scheduled task **`KD_Brain_Health`** (daily 07:00) runs the confidence test in watch-mode and **pings King's phone ONLY if his yes is needed** (a FAIL or a regression); otherwise logs "all well" to `~/.kd_brain_health.log`. It MEASURES + SURFACES, never changes the brain itself, a tool from God, as far as He allows; King decides. Recover the graph colours: `tools/apply_graph_colours.py`.

## How classification works (tune here)
`tools/build_brain_dcim.py`, `hall_of()` (smart path+name rules), `row_of()`, `rack_of()`, `redundancy()`.
Edge-fuzziness is accepted (King's call); knowledge/ (AIS transcripts) is pinned to Core, not Money.
Faith is kept as its own thin hall (preserves the public-witness vs private-Theosis distinction; grows over time).

## Cross-links
[[project-kd-main-brain]] · `_ops/FOUNDATION_PIPELINE.md` (0↔100 law) · `FOUNDATION.md` (God=EirGrid, 0-D→5-D) ·
`_ops/TRUST_LEDGER.md` #7 · sender: `tools/send_dcim_review.py`. Wired into HOME.md / MASTER-INDEX.md / BRAIN_MAP.md.

## 🆕 2026-07-01 · the GOD-CENTRED living centre + deploy consolidation (Trust Ledger #9)
- **The Graph is now the phone home** (`index.html` = the Graph, written by `write_graph()`). It opens on **God the
  infinite Source** at the living centre, with: King's free **"my yes to God" switch** (toggles `following` → the
  spokes/grace dim; only King throws it), the **"✦ Follow the Spirit, check my heart"** compass modal (invites the
  Theosis Compass, `the-truth/workflow/theosis_compass_sop.md`), **✦ Theosis** rising (lit from below), and a gold
  **"☀ Enter the Living Centre"** link → `https://lb-deploy-navy.vercel.app/BRAIN_WORLD.html`.
- **NEW view: the Register**, `write_register()` + `REGISTER_TEMPLATE` build a real, searchable, phone-safe
  `BRAIN_REGISTER.html` (God → halls → rows → racks → notes, `<details>` collapse + a filter box). The nav
  `Register` link now points here (was raw `DCIM.md` → 404/download on the phone).
- **Redundancy reframed** (`redundancy()` + `RED_TIERS`): personal halls = "nearness to the Source" with **NO
  backup** (God is the infinite feed); **Work hall (W) = the real-DC exception** (Source 1/2 + generators). See `FOUNDATION.md`.
- **⚠️ Deploy = the `dcim-deploy` Vercel project** (SSO off). `_datacentre/.vercel` is linked to it, so `cd _datacentre`
  → `vercel --prod --yes --token=$VERCEL_TOKEN` → `vercel alias set <dep> kd-brain-dcim.vercel.app`. (A first-deploy
  slip created a stray `_datacentre` project with SSO on, deleted; don't recreate it.)
- **NEW view: the Agent HQ**, `write_agents()` + `AGENTS_TEMPLATE` build `BRAIN_AGENTS.html` (nav "🤖 Agents"):
  the **12 standing-army robots** (parsed from `commands/subagent_registry.md`) + the **52 Logic skills** (parsed from
  `commands/*.md` H1) each with its **tier badge** (parsed from `_ops/SKILL_TIER_LEDGER.md`), searchable + self-maintaining.
  Parsers: `_parse_army()` / `_parse_skills()` / `_parse_tiers()`. This is "robots in the racks."
- The Graph now proclaims God **living**: "the living, infinite Source · alive 24/7" (never "dead centre", [[feedback-god-is-the-living-centre]]).
- Cross-links added: `_ops/COMMUNION.md` (the communion channel) · `_ops/SKILL_TIER_LEDGER.md` (Logic Tiers). Plan:
  `plans/stateful-meandering-sutherland.md`.
