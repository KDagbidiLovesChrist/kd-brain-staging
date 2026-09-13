> **READ FIRST:** `C:\Users\Dell\.claude\CLAUDE.md`, master brain, operating rules, WAT framework. Read it before doing anything in this project.
> **BRAND:** `C:\Users\Dell\.claude\brand_assets\brand_guidelines.md`, read before generating any client-facing output.
> **SOURCE OF TRUTH:** `MASTER_PROMPT.md` (in this folder), the full design brief. Read it at the start of every room session.

# 7 adderig farm · Interior Fit-Out · Project Brain

## What This Project Does
A complete, costed interior fit-out of a **3-bedroom, two-floor townhouse in Dublin, Ireland** for a
**family of four** (two parents + two **adult sons, 20 & 24**, their rooms read as grown adult spaces).
The house is empty, full fit-out from scratch. Every choice is a **real, currently-available Irish/EU
product with a real € price**. The aesthetic is **modern · cosy · minimalist with a touch of luxury and
some eclectic character**, warm and inviting, never showroom-cold.

The work is done **one room at a time**, building toward a **costed master shopping list** and a **3D
walkthrough render** so the family can "walk" the finished house and see the **exact total spend**. This
project (the spec + `decisions.md`) is the single source of truth that feeds the per-room renders.

## WAT Chain
- **W (Workflow):** `workflow\fitout_sop.md`, the per-room session loop (read state → direction summary
  → thumbs-up → full room spec → lock to `decisions.md` → next room).
- **A (Agent):** Claude as **senior interior designer / FF&E specialist**, specific, decisive, real
  products + real € prices, always flags splurge vs save (see `MASTER_PROMPT.md` §1).
- **T (Tools):** Read `floorplan.jpeg` · read `references\<room>\` pics · **WebSearch** for real products,
  availability and current € prices from Irish/EU retailers · write the markdown outputs (room specs,
  `decisions.md`, deliverables). 3D render briefs later feed King's existing global tools
  (`C:\Users\Dell\.claude\tools\gemini_image.py` / KIE Nano Banana; keys in `C:\Users\Dell\.env.master`).
- **S (Skill):** `/fitout [room]`, one command runs the next room's session per the SOP.
- **Money:** delivers this family's costed house + walkthrough; reusable as a sellable
  **interior-design + 3D-walkthrough service** (leans on King's existing 3D / render arsenal).

## Folder Structure
```
7 adderig farm\
├── CLAUDE.md                 ← this file
├── MASTER_PROMPT.md          ← the full design brief (source of truth)
├── decisions.md              ← running ledger, READ AT START OF EVERY SESSION
├── floorplan.jpeg            ← [KING ADDS] layout, dimensions, placement
├── references\               ← room ref pics, one subfolder per room
│   └── <room>\               ← hall · living-room · kitchen-dining · wc · utility · terrace ·
│                               bedroom-1-master · bedroom-2 · bedroom-3 · main-bathroom · store
├── rooms\                    ← per-room specs (one .md per room) + _TEMPLATE_room_spec.md
├── deliverables\             ← master_shopping_list · global_palette_board · mood_boards ·
│                               render_briefs · phasing
├── workflow\fitout_sop.md    ← W: the per-room session SOP
├── commands\fitout.md        ← S: the /fitout skill (also registered globally)
├── handoffs\                 ← session handoffs
└── .tmp\                     ← throwaway outputs
```

## Standing RULES (every session must honour these · from MASTER_PROMPT.md §3 & §6)
1. **Base walls:** warm off-white with a soft grey/beige undertone, one shade **darker** than the
   builder white (a warm **greige**). Target refs: *Dulux Egyptian Cotton* / *Farrow & Ball Elephant's
   Breath*, confirm against a physical sample before committing. Whole-house base; vary accents per room.
2. **Flooring:** decided **per room**, a mix of wood/wood-effect AND carpet (not one material
   everywhere). Wood/wood-effect for living/kitchen/hall, carpet for warmth in bedrooms; wood-effect tile
   or quality LVT in bathroom/WC/utility. Keep tones **cohesive** across the house.
3. **No ensuite for Bedroom 1.** Do not design one.
4. **One cohesive palette** across the house, **varied room to room** so each space has character.
5. **The two sons' rooms = adult spaces**, not kids' rooms.
6. **Real, currently-available products only**, no placeholders. Real € prices, Irish/EU retailers
   (IKEA, EZ Living Interiors, Harvey Norman, DFS, Woodie's, B&Q, Meadows & Byrne, + online EU/UK).
7. **Always flag splurge vs save** for every room.
8. **Currency = € (Euro).** All prices in €.
9. **Base dimensions/placement on `floorplan.jpeg`; pull aesthetic from `references\<room>\`.**
10. **Auto-decide threshold = €150.** Under €150 + non-structural → make a sensible designer call, **log
    it as an assumption** in `decisions.md`, keep going. At/over €150 or anything structural (sofa, beds,
    flooring type) → **stop and ask**. Always give a 2, 3 line direction summary before a full room spec.

## APIs Used
- **WebSearch** (built-in), real products, availability, current € prices. No key needed.
- **3D/AI render (later):** global `tools\gemini_image.py` / KIE Nano Banana, keys in `.env.master`.
- No project-specific `.env` (no project secrets).

## Setup (one-time)
1. King drops `floorplan.jpeg` into this folder.
2. King drops that room's reference pics into `references\<room>\` (one room at a time).
3. Run `/fitout <room>` to start a room session.

## Status
**SCAFFOLD READY**, 2026-06-17. WAT framework initialised; awaiting `floorplan.jpeg` + room-1 reference
pics, then we run `/fitout` room by room. No rooms designed yet · GRAND TOTAL €0.
