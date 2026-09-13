# Empty → Designed Walkthrough · concept + build guide

**King's vision (2026-06-20):** *"I should be able to see every part of my house empty,
and then it fills out as we design."* A before/after reveal per room, bare today,
finished as we lock each room.

This folder holds **`empty_to_designed.html`**, the walkthrough page. The empty house
is ready now; each "designed" image gets dropped in as a room is locked, and that room's
card auto-flips into a live drag-slider (NOW ⇆ DESIGNED). A progress bar shows "X of 12
rooms designed" so the house visibly fills out.

---

## Why this method (the fix for "where are my doors and rooms?")
Every failed attempt happened because we asked AI to **invent** a room. This flips it:
we start from King's **real empty photo** of the room and only **add** the design on top.
Geometry is perfect because it's literally his house. Proven once already with the pale-oak
floor dropped onto his real living-room frame (`deliverables/renders/living_real_floor_v1.jpg`).

**THE RULE:** never generate a room from scratch, always anchor to the real empty frame.

---

## How the laptop fills it in (per room, as each one locks)

### 1. Grab the room's real EMPTY frame
- Pull a clean, well-lit still of the room from the empty-house walkthrough video
  (`tools/extract_room_frames.py`), or use a photo King took.
- Save it to `walkthrough/img/<room>_empty.jpg` (names already wired in the HTML).

### 2. Render the DESIGNED view ON TOP of that exact frame
Use `tools/gemini_render.py` with the empty frame as the reference image:

```
python tools/gemini_render.py --ref "walkthrough/img/living_empty.jpg" \
  --out "walkthrough/img/living_designed.jpg" \
  --prompt "PROMPT BELOW"
```

**The corrected prompt template (this is the 'prompt change' King asked about):**
> "This is a photo of a real empty room. KEEP the exact room unchanged, same walls,
> windows, doors, ceiling slope, radiators, kitchen units and overall shape and camera
> angle. Do NOT move, add or remove any windows, doors or walls. ONLY add the interior
> design: [pale washed Scandi-oak SPC floor], [warm greige walls], [the locked furniture
> + decor for this room], soft warm daylight, photoreal. The result must look like the
> SAME room, just finished and furnished."

Fill the [brackets] from the room's locked spec in `decisions.md` / `rooms/<room>.md`.
If the first render drifts (moves a window etc.), re-run, do NOT accept invented geometry.

### 3. Wire it into the page
Open `empty_to_designed.html`, find the `ROOMS` array, set that room's
`designed:"img/<room>_designed.jpg"`. Save. The card flips to a live before/after and the
progress bar ticks up. **QA isn't done until King approves** (standing rule), send it to
him, fix until he's happy, THEN lock.

### 4. Deploy
Move/copy this folder into the live project (`deliverables/walkthrough/`) and
`vercel --prod --yes`, or add it alongside `house.html` and re-alias.

---

## How the three walkthrough layers connect (King chose all three)
1. **This before/after page**, photoreal, real frames, fills out room by room. (Build first.)
2. **`house.html` empty/designed toggle**, the exact 3D MAP gets a button to flip the whole
   house empty ↔ designed (clean/architectural look, for navigation + layout proof).
3. **Polycam phone scan**, once the house is clear + the new floor's laid, King scans it for a
   true walk-anywhere photoreal model to design into. (Parked until the house is ready, see
   `HOW_TO_SCAN.md`.)

## Use BOTH videos together (King's call, 2026-06-20)
Two source videos cover each room better than one, extract frames from BOTH and cross-check:
1. **Empty walkthrough video**, clean, steady stills of the bare rooms → best for the "NOW"
   side of each slider. (Contact sheets already in the brain:
   `empty_walkthrough_contact_1of2_0-78s.jpg` + `..._2of2_80-149s.jpg`; real living/kitchen
   frames in `references/living-room/_realframes/`.)
2. **Single-shot whole-house video**, fills the gaps the first one rushed past (utility,
   terrace, bike store) AND confirms every wall/window/door for the layout QA.

**Method per room:** pull frames from both → pick the CLEAREST empty still for the slider →
use the other angle to confirm geometry is real before rendering. If a room appears from two
good angles (e.g. open-plan living/kitchen), make two before/after pairs so King sees it
properly. Cross-referencing the two videos = no room missed, no invented geometry.
