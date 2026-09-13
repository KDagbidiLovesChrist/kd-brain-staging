# King's Video Editing Playbook
*Everything learned from the 5 videos King sent (2026-06-06). Source: Nate Curtiss "Editing Tutorials" x4 + Nate Herk "Claude Just Destroyed Every Video Editing Tool" x1. Transcripts saved in `knowledge\ais_resources\transcripts\`.*

---

## THE ONE PRINCIPLE (every video says this)
**The edit is the supplement, not the star.** The message (script + real proof) does the selling. The edit's only job is RETENTION: hook hard, hold a steady pace, put a sound on every movement, change the music at the turns, and never over-do it. Nate Herk's killer line: *the tool doesn't give you taste, people with taste 10x, people without get mediocre output.*

---

## VIDEO 1 · "Genius YouTube Editing Tricks" (Nate Curtiss)
Four concrete tricks:
1. **Animated stock characters**, a logo/face on a stock body, made to "talk": key-frame it popping in from off-screen (ease the keyframes), add a free handheld-camera-shake preset so it feels alive, edit multiple poses side-by-side. Reusable as a preset.
2. **Big number counters**, counting up (money, jobs, dates). Done with a timecode trick: stretch it so the number climbs, speed it up, add a glow + impact sound when it lands.
3. **Revealed line graphs**, draw the line with the pen tool, animate a "linear wipe" in reverse so the line draws itself on, add a grid + labels behind it.
4. **Clean animated subtitles**, auto-generate from transcript, show only 1, 2 words at a time, small, bottom of screen, subtle stroke/shadow, readable font. Do NOT over-style them.

## VIDEO 2 · "7 Editing Tips to Boost Retention" (Nate Curtiss)
1. **Don't over-edit for your audience**, match editing level to who's watching. Younger = more cuts/effects; older = calmer. Editing is the supplement.
2. **Raise your graphs / frontload**, put the most work into the first ~30 seconds, then keep a consistent pace so retention doesn't drop off a cliff.
3. **Big transitions only for big moments**, a huge whoosh/zoom only when changing scenes/sections. Everywhere else: simple jump cuts.
4. **Sound design**, a sound on every element that moves (icon slides in -> slide sound). You can even fake/enhance real sounds (the LOTR ring-drop trick). Don't overdo it.
5. **Music as a tool**, keep it quiet under the voice (about -5 to -25 dB below VO), and CHANGE the track when big things happen (intro -> body, section -> section).
6. **Get creative**, auto-captions, motion tracking, text overlays, trending effects.
7. **Give viewers a break**, don't hyper-stimulate the whole time. Pauses (like Obama's speaking pauses) read as confidence and keep people listening.

## VIDEO 3 · "How to Edit Viral Videos for FREE" (Nate Curtiss)
- **Clean the audio** first (remove echo/noise, boost level). **Color-grade** footage even with cheap lights.
- **Pacing matches audience**, high energy first 30s, then settle but stay fairly quick.
- **Overlap clip audio on two tracks** to smooth rough cuts.
- **Ken Burns effect**, slow zoom/scale on any still image so the frame breathes.
- **Sound design**, when it's right, you don't notice it. Music between -5 and -25 dB; change the song every 30, 90s.
- **Free b-roll** from Pexels; screen-record with OBS.

## VIDEO 4 · "How to Edit Viral Videos" (Nate Curtiss)
- **A-roll vs B-roll**, gather 2, 4x more b-roll than you need. Cut every 1, 4 seconds in the intro.
- **Intro is everything**, stimulate the screen immediately; keep intro AND outro short or people drop off.
- **Pop-in subtitles** (keyframe scale) used sparingly after the intro.
- **Use presets** for transitions (work smart, not hard).
- **Motion tracking**, e.g. track a profile pic onto a person's head.
- **Scale for emphasis**, scale a clip down ~80% for a joke, or up + grainy for impact.
- **Sound design = "the single biggest thing that turns a decent edit into an incredible one."**
- **Music**, section the video, change music per section, use only non-copyright music, fade/riser between songs, keep it -10 to -20 dB under VO.

## VIDEO 5 · "Claude Just Destroyed Every Video Editing Tool" (Nate Herk)
- Edit videos with **Claude Code + an HTML->video renderer** by natural language. He uses HyperFrames; **we use Remotion** (he praises Remotion as more reliable). This is exactly our setup.
- **Transcribe the video to word-level timestamps** so motion graphics sync to the words (we do this with Whisper).
- **Look at every frame before rendering**, then iterate with timestamped feedback like you'd give a human editor.
- Feed it a **brand/design system** so outputs look on-brand.
- **The meta-lesson:** taste + creative intuition = 10x with these tools. The tool doesn't supply taste; you do (that's the iteration loop).

---

## THE TECHNIQUE CATALOGUE (what we can actually build in Remotion)
| Technique | Use it for |
|---|---|
| Word-by-word subtitles synced to VO | Pace + engagement on talking sections |
| Ken Burns (slow zoom) | Any still / screenshot so it breathes |
| Scale-for-emphasis | Punch the key word/clip |
| Number counter + glow + impact | A real, honest stat (never fake) |
| Line graph draw-on + grid | Showing growth (honest only) |
| Polaroid b-roll cards (tilt + shadow) | A gallery of real work |
| Animated character (logo-face on body) | Personality / "talking" without a face |
| Motion tracking | Stamp a logo onto moving footage |
| Gold streak / ink-wipe / zoom-punch | Section breaks only (big moments) |
| Sound design (whoosh/tick/riser/impact) | Every move; risers into turns |
| Music that changes energy per section | Bridge the viewer through the story |

---

## HOW IT MAPS TO KING'S PROMO
- **Hook** in the first 2, 3s (a question stops the scroll).
- **Frontload** energy, then steady pace with 2, 3 **breathing pauses**.
- **Big transitions only** on the turn, the proof, the CTA.
- **Sound design on every move**; music quiet under George, lifts at each turn.
- **Proof = real work only** (King's honesty rule, no fake numbers/counters).
- **Faceless**, the work IS the star; brand presence via the KD mark.

## THE 4 STYLE DIRECTIONS (these are genuinely different · pick one to clone)
1. **Apple-style reveal**, minimal, ultra-premium. One big site at a time, slow camera, huge negative space, almost no text. Restraint is the wow.
2. **Nate Curtiss edit**, fast edutainment: characters, counters, graphs, polaroid cards, word subs, zoom punches. What 4 of the 5 videos literally are.
3. **Mubashir cinematic**, dark, dramatic, bold two-tone titles, silhouettes, heavy grade, infographic node maps. Trailer energy.
4. **(what we built first)**, kinetic gold text + footage behind it. Good, but King found it same-y after a few passes.

> Note to self (Claude): stop reskinning one engine. Commit hard to ONE style and build it from scratch. Reference-driven > spec-driven, clone the actual reference, don't average them.
