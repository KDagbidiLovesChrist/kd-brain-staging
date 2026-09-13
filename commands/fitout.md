# /fitout · Interior Fit-Out (one room per run) · "7 adderig farm"

> ⏸ **PROJECT PARKED 2026-07-03: the credit union REJECTED the house loan (car loan only).** The design
> stays locked and ready; NO new work blocks until funding is real (the funding talk lives in the /money
> finance re-review). Run this skill only on King's explicit ask. See `memory\project_interior_fitout_7adderig.md`.

Designs **one room at a time** of King's 3-bed Dublin townhouse: real Irish/EU products, real € prices,
locked to a running ledger, building toward a costed shopping list + 3D walkthrough.

**Usage:** `/fitout [room]`, e.g. `/fitout living-room`. No room = pick the next "not started" room.

## Steps to Execute

1. Navigate to the project folder:
   `cd "C:\Users\Dell\Documents\7 adderig farm"`

2. **Read state (in this order):**
   - `MASTER_PROMPT.md`, the full brief (your role = senior interior designer / FF&E specialist).
   - `decisions.md`, every locked choice, the floor table, assumptions, threshold (€150), grand total.
     **Honour everything already locked. Do not re-ask or re-decide it.**
   - `CLAUDE.md`, the standing RULES (warm-greige walls · floor per room · no ensuite Bedroom 1 ·
     sons' rooms = adult · real available products + € prices · flag splurge vs save).

3. **Pick the room.** Use the `[room]` arg, or the next "not started" room in `decisions.md` §5.
   - If `floorplan.jpeg` is missing from the project root → ask King to add it, then stop.
   - Read `floorplan.jpeg` (layout/dimensions/placement) and `references\<room>\` pics (mood/palette).
     If no ref pics, proceed from the palette + brief and note refs were missing.

4. **Direction summary first.** Give King a 2, 3 line summary of the room's direction. **Get a thumbs-up
   before the full build** (cheaper than regenerating a wrong room).

5. **Full room spec.** Using `rooms\_TEMPLATE_room_spec.md`, produce all 7 parts (master prompt §4):
   Concept · Surfaces (real paint names/codes) · Furniture & FF&E (item · style · product + retailer ·
   € price · dimensions) · Lighting · Soft furnishings & decor · Layout notes (to the floor plan) ·
   Room subtotal. **Flag splurge vs save.** Save to `rooms\<room>.md`.
   - **Decision rule:** unspecified detail, under €150, non-structural → make a sensible designer call,
     **log it as an assumption** in `decisions.md`, keep going. At/over €150 or structural (sofa, beds,
     flooring) → **stop and ask King.** Never invent a product or a price.

6. **Lock it.** Append the room's locked pieces + assumptions + palette/floor choice + subtotal to
   `decisions.md`; update the room status and the **GRAND TOTAL**.

7. **Render brief.** Append this room's 3D render prompt + key products to `deliverables\render_briefs.md`.

8. **Deliver.** Tell King the room is locked, show the subtotal + new grand total, and (per his standing
   rule) email the room spec link + paste it in chat. Then offer the next room.

> Full SOP: `workflow\fitout_sop.md` (LAPTOP-ONLY: lives outside the synced brain, in the fit-out project folder). Source of truth: `MASTER_PROMPT.md`. State: `decisions.md`.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
