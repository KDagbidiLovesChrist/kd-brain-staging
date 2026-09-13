---
name: reference-floor-swap-ai-limit-showhome-method
description: "AI image-gen redraws the WHOLE room (can't do true floor-only on a real photo); use real same-layout show-home photos + manual masked composite instead."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 28f5b404-ca3d-454c-9e1b-632fcf10ea59
---

# Floor/room visualisation · the AI limit + what actually works (from 7 adderig farm)

## The hard limit (King caught this, 2026-06-20)
**Generative AI (Gemini image) cannot do a true "only the floor changes" edit on a real room photo.**
It **re-generates the entire image** every time, walls, window, the view outside, proportions all shift.
So across rooms it looks **inconsistent + "AI slop"**, and the room is no longer the client's real room.
Prompting "ONLY change the floor, keep everything identical" does NOT prevent this. Stop pretending it can.

## What actually works (in order of trust)
1. **Real same-layout reference photos.** If a **show home of the client's exact house type** exists
   (new-build estate), it IS their house, fully designed. Pair **their real empty room** beside the
   **show-home designed room** + a written products/cost plan. No faking. (7 adderig: the Aderig show
   home #55 = King's exact type; stills in `7 adderig farm\deliverables\showhome\sh_*.jpg`.)
   - **King's instinct (2026-06-21): SWAP our chosen products INTO the real show-home photo, change
     ONLY the agreed items.** Right idea, BUT ⚠️ **NO TOOL ACHIEVES IT CLEANLY (proven, don't repeat):**
     - **AI (`gemini_render` show-home base + product refs) REDRAWS THE WHOLE PHOTO**, recomposes the
       room, shifts proportions, changes the view. King: *"everything changed… wtf."* It is NOT a swap.
     - **Manual PIL paste-in (white-bg cutout → paste over the old sofa) FAILS on PERSPECTIVE**,        catalogue product shots are a different camera angle than the scene sofa, so the paste looks
       stuck-on and the **old sofa shows through** behind it. (Proven: a beige cutout over the grey
       show-home sofa = obvious sticker.) Catalogue angle ≠ scene angle = fatal.
     - **✅ WHAT TO ACTUALLY DO:** stop chasing the perfect combined picture. Deliver the **real
       show-home photo (the look) + the real product photos (what they buy) + the cost**, all 100%
       real and what the decision actually needs. If a combined "vibe" pic is wanted, use AI but
       **label it a MOOD, never "your room."** True per-item swaps would need real inpainting/masking
       (not in the current `generateContent` API) or a designer in Photoshop.
2. **Free physical sample board**, most accurate for the actual floor colour in real light. Costs nothing.
3. **Manual masked composite** (true floor-only, no AI): keeps the real room 100%, only the floor pixels
   change. Recipe in `7 adderig farm\.tmp\floor_compare.py`:
   - PIL perspective transform (no cv2 needed): solve 8 coeffs from 4 point pairs (output→texture), then
     `texture.transform((W,H), Image.PERSPECTIVE, coeffs)`.
   - Floor **mask** = a polygon following the skirting line (overlay a coordinate grid on the photo to read
     corners). Feather with GaussianBlur(2).
   - Carry the room's **real lighting** onto the wood: `shading = clip(blur(grayscale)/mean_floor, 0.64, 1.3)`
     then `wood * shading`. Composite `room*(1-mask) + lit*mask`.
   - Use a **CLEAN plank crop** (no dark background edges or it tiles into stripes); add faint plank-edge
     lines; alternate/flip tiles to reduce obvious repeat. Result keeps the real room but the floor reads a
     bit flat, honest trade-off.
4. **Floor visualiser tools** (Roomvo-type, what flooring shops use), purpose-built; try if available.

## AI renders = MOOD only
For the **design stage** (furniture, wall colours), AI renders are an acceptable **vision/mood**, never an
accurate photo of the actual house. Always label them as such. Never sell an AI render as "your real room."

## Rules King set this session
- ONE consistent floor in every room; **floors only** (no wall-colour change, no add/remove).
- **Confirm each room vs the floor plan** before doing it.
- He **can't film new clips** / can't get another empty-house video → work only from existing media.
See [[project-interior-fitout-7adderig]] · [[feedback-no-overselling-verify-before-send]].
