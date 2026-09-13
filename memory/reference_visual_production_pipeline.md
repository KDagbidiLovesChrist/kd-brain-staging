---
name: reference-visual-production-pipeline
description: "STANDARD for ALL visual work (ads, animation, faceless content, UGC): storyboard-first pipeline so scripts/stories/prompts are locked and output is predictable BEFORE any paid generation"
metadata:
  node_type: memory
  type: reference
  originSessionId: 02ae15d4-3657-450a-bc63-3c2decc2f408
---

# Visual Production Pipeline (the storyboard-first standard)

**Standing decision (2026-06-26, King):** every visual we make, ads, video animation,
faceless content, UGC, anything, goes through this pipeline. The point is that the **script,
story and prompts are A1 and we KNOW what to expect BEFORE we spend on generation.** Plan the
whole thing on paper (free), lock it, then generate (paid). Kills wasted spend and surprises.
Learned from two TikTok clips King sent (an "AI production sheet" node tool + magnific; and
**MiniMax Hub** "Character Scene Storyboard" by @theanimationstudio). The real lesson was the
PIPELINE, not any one app. This LAYERS ON TOP of Seedance (Seedance = the "make one shot move"
engine, not a story tool). See [[skill-seedance-animated-websites]].

## The 7 stages (plan stages 0-4 are free, generate at 5-6)
0. **Brief / intent** (discovery, Rule #13): what is it (ad / faceless story / UGC), who for,
   the ONE outcome or CTA, length, aspect ratio, platform.
1. **Cast & object bible:** name every recurring character + key object, write personality +
   physical description (the LILA example: "Lila", "Lila's dad", "Ball", each with traits).
   For faceless/UGC the "cast" = the persona/product/hands/setting + the brand look.
2. **Character + style sheets:** generate a reference sheet of poses/expressions/angles per
   character + one environment/style sheet. THIS is the consistency lock (same face every shot).
   Lock aspect ratio + quality (the clip used 16:9, 4K, "no background, photo realistic").
3. **Script / story:** write the actual beats. This is where "A1 scripts/stories" live.
4. **Storyboard:** break the script into shots. Per shot write: what's in frame, camera angle,
   action, the exact IMAGE prompt, and the MOTION prompt. Nothing gets generated until the board
   reads right. This is the "know what to expect" doc and the spend gate.
5. **Generate stills:** one image per shot via Nano Banana / `tools\gemini_image.py`, feeding the
   character sheet as the reference so characters stay identical.
6. **Generate motion + assemble:** animate each shot (Seedance image-to-video / MiniMax / our
   engines), then cut together with VO (ElevenLabs George), captions, music, transitions via
   ffmpeg / Remotion / Hyperframes. See [[reference-faith-narrated-video-engine]] for the ffmpeg
   per-scene pattern and [[reference-hyperframes-video-method]].
7. **QA + deliver:** frame QA, loop until King approves ([[feedback-qa-until-king-approves]]),
   deliver to phone (Gmail link + chat, [[feedback-always-send-gmail-and-link]]).

## How each content type uses it
- **Ads:** full cast + story + storyboard; the brand/product is a "character" with its own sheet.
- **Video animation:** same, character-led narrative.
- **Faceless content:** cast = faceless figures/silhouettes/scenes; still need a style sheet +
  storyboard so every clip matches (this is exactly what the faith "Bible animation" engine does).
- **UGC:** "character" = persona + product; style sheet = the look (phone-shot aesthetic, lighting);
  storyboard = hook -> demo -> CTA beats.

## Tie-in with the TSV framework (Title · Script · Video) · [[learning-digital-product-viral-sales-model]]
TSV and this pipeline are two halves of ONE machine. **TSV = recipe proven to sell** (what to make
+ why it'll get attention, modeled on a proven winner). **This pipeline = the kitchen** (how to
produce it A1, consistent, no wasted spend). Map:
- **T (Title)** -> Stage 0 Brief (the proven hook IS the SEO keyword: wins attention + discoverable).
- **S (Script)** -> Stage 3, but MODEL the winning script's structure/beats/pacing (own words). That
  is what makes the script A1: proven, not guessed.
- **V (Video)** -> Stages 4-7 (storyboard -> generate -> assemble). The storyboard is HOW you copy
  the proven format on purpose (its shots/pacing), character sheets keep it consistent.
- **Bridge step:** storyboard the WINNING video FIRST (decode it into shots/hooks/beats), then
  storyboard YOUR version against that template. Storyboarding decodes the "V" in TSV.
One line: **TSV picks the proven shot; the storyboard pipeline lands it.** `/storyboard` becomes the
"produce" step inside the bigger TSV money-skill (find winner -> copy T/S/V -> PRODUCE -> post ->
funnel to offer), pointed at Mum, then Aunty, then King's UGC, then paid ads. Back half (the offer)
still differs per project.

## What we already own vs what's new
- **Already own:** Nano Banana/Gemini images, Seedance, ElevenLabs VO, ffmpeg/Remotion/Hyperframes.
- **New discipline to add:** character/style SHEETS (consistency) + a written STORYBOARD BEFORE
  generating (predictable output + spend control). No new paid tool required to start.
- **Optional tool to test:** MiniMax Hub (named in the 2nd clip) for auto story+storyboard. Test
  free before committing (lean-spend rule [[feedback-lean-spend-llama-routing]]).

## Honest flags from the source clips
- Both creators' "I sell this to brands / killing it" claims were unproven (no clients/numbers).
- The MiniMax demo's polished anime was PRE-RENDERED with the UI laid over it, so it proves the
  story+storyboard step, not that MiniMax outputs those finished frames. Treat "production-ready"
  with caution; verify by actually generating before promising a client.

## NEXT (not yet built)
Could become a `/storyboard` skill or fold into `/video` as the front step (the WAT "S"). Offered
to King; await his go before building the skill.

## UPGRADE (2026-06-27): the storyboard step is now the DEEP STORYBOARD STANDARD
Stage 4 (storyboard) is upgraded to the MiniMax-depth standard King locked: every video's approved
board must carry THREE deliverables in order, a Comprehensive Design Sheet Brief, then a Character
Model Sheet (the hero from many angles/poses/expressions), then the shot-by-shot production
storyboard with a real still per scene and the per-scene fields (EMOTION first). This is now a
MANDATORY rule baked into `/content-engine` and `/find-skills`. Full spec + field list:
[[reference-deep-storyboard-standard]].
