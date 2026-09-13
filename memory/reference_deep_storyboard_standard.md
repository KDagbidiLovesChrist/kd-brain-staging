---
name: reference-deep-storyboard-standard
description: "MANDATORY deep-storyboard standard for ALL video/visual builds (modeled on the MiniMax Hub flow): the approved board must carry a Design Sheet Brief + a Character Model Sheet + shot-by-shot stills with emotion-first per-scene fields, BEFORE any render or spend"
metadata: 
  node_type: memory
  type: reference
  originSessionId: 377b479b-4ca1-4b54-a7d6-e4d24f3654c3
---

# Deep Storyboard Standard (MiniMax-depth, MANDATORY)

**Standing decision (2026-06-27, King):** every video, animation or visual we make is taken to the
MAXIMUM best ability. In his words: a skill should be "marked out to the depth... done to the
maximum possible best ability. That should be the whole point." No surface-level work, no thin
text shot-list. The storyboard King approves must hit **MiniMax depth** as THREE deliverables in
order, BEFORE any render or paid generation.

**Source:** @theanimationstudio's "Anime World Cup" **MiniMax Hub** demo (the "Character Scene
Storyboard" / deep-storyboard flow). King sent it via Gmail, subject "Video ai animation storyboard
learn." The real lesson is the PIPELINE depth, not the one app. It layers on top of, and upgrades,
[[reference-visual-production-pipeline]] (its Stage 4 storyboard is now this standard).

## Why this is a rule (the maths), per [[feedback-consensus-everything-rule]]
This is Rule #17 (model the proven winner, consensus) plus Rule #18 (the board must be VISUAL)
made concrete for video. A deep board is the spend gate: lock the whole thing on paper (free),
then generate (paid). It kills wasted spend and the "ew wtf" surprise renders. King must know
exactly what the final video looks like, end to end, before a single frame renders.

## The THREE deliverables (in this order)

### 1. Comprehensive Design Sheet Brief
A full written spec up front:
- Project title
- Logline / goal
- Duration
- Aspect ratio (Panel Ratio, 9:16 for short-form)
- Visual Style (art direction + the EXACT palette)
- Plot Scope
- The character
- The caption style
- The music
- The pacing
- The scene map

### 2. Character Model Sheet
The hero character rendered from MANY angles, poses and expressions (a turnaround sheet) so it
stays identical in every shot. This is the consistency lock (same face/look every scene). For
faceless/UGC work the "character" = the persona / product / hands / setting + the brand look.

### 3. Shot-by-shot production storyboard
EVERY scene shown as a real still frame, exactly how the final frame looks (background visual +
character + caption + headline), each mapped to its exact script line, annotated with these
per-scene fields **IN THIS ORDER (emotion first, per King):**
1. **Scene number + time range**
2. **VO**: the exact script words for that beat
3. **Caption on screen**: the active / highlighted word called out
4. **EMOTION**: start here, always
5. **Shot type**
6. **Camera / Motion**: HOW the still becomes a moving shot (the exact animation: slow push-in
   1.0 to 1.06 Ken-Burns, parallax drift, glitch cut, shake on beat, etc.)
7. **Visual source + Tool**: AI image via kie.ai Nano Banana / Pexels b-roll / in-engine graphic,
   PLUS the motion engine (HyperFrames GSAP or Remotion)
8. **SFX / music cue**
9. **Transition out**
10. **The exact image / motion PROMPT used** (Rule #18 requires the real prompt per shot)

## The agent flow that builds it (MiniMax Hub)
Reference image -> Visual Style -> Panel Ratio (9:16 for short-form) -> Plot Scope (Plot +
storyboard sheet) -> generate. **Nothing renders until King approves this visual board start to
finish.** If he tweaks it, redo the sheet and show it again. Approve-then-build only.

## Where it is baked in (MANDATORY now)
- **`/content-engine`**: a "DEEP STORYBOARD STANDARD (MANDATORY)" section; supersedes the lighter
  shot-list step in Layer 3, before Layer 4 (Produce) spends.
- **`/find-skills`**: the MAXIMUM-DEPTH PRINCIPLE; any visual skill it builds holds output to this
  standard.
- **Applies to EVERY video/visual build going forward.** Other projects (the content engine, the
  Buka, UGC, ads, the faith video engine, client work) adopt it as they come. Add the section to a
  skill when it next touches visual production.

## Related
[[reference-visual-production-pipeline]] · [[feedback-consensus-everything-rule]] ·
[[project-content-engine]]
