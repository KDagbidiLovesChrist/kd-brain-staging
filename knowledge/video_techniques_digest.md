# Video Techniques Digest · MARKER Style Promo
*Every technique directly observed in the 5 reference videos, mapped to how to build it in Remotion.*
*Sources: NC1=i9syvOdnJ5Y, NC2=9BQa7cCW5vw, NC3=ODRJkEGTI_U, NC4=RBvIv-LfVBE, NH=ZNbgOhxhzXg.*

---

## SECTION 1: HOOK TECHNIQUES

### 1.1 Immediate Text-Provocation Hook (NC2, NC4)
A large, punchy word or phrase appears in the first frame over B-roll footage, "Any money?" / "A ton of money".
**Remotion:** On frame 0, render a `<Sequence from={0}>` containing a bold `<div>` positioned center-screen with `opacity` interpolated 0→1 over 6 frames. No logo, no music fade-in, text and sound hit simultaneously.

### 1.2 Bold Claim + Counter Payoff (NC1)
Hook states a specific number ("18 tricks") visible at 0s, then every technique is revealed sequentially, the number is the implicit promise keeping people watching.
**Remotion:** Store items array; render a `currentIndex` that increments per section. Show "X of 18" badge in top corner using `interpolate(frame, [sectionStart, sectionStart+6], [0,1])`.

### 1.3 Question Hook (NC3)
A chalk-drawn question on a dark board fills the screen for 2, 3s, forces a mental answer before any speech.
**Remotion:** Use `<Img>` of a pre-rendered chalk texture card (PNG), fade in over 8 frames with `springConfig`. Pair with chalk-squeak SFX on frame 1.

---

## SECTION 2: CAPTION TECHNIQUES

### 2.1 Word-Level Pop-In Subtitles (NC4, NH)
1, 3 words appear in sync with VO, bottom-center, white bold sans, each popping in with a scale spring.
**Remotion:** Parse Whisper JSON timestamps into `{word, start, end}` array. For each word: `<Sequence from={startFrame} durationInFrames={duration}><span style={{transform: `scale(${spring(...)})`}}>{word}</span></Sequence>`. Nerd font = "Inter Bold" or "Poppins ExtraBold".

### 2.2 Emphasis Scale-Up on Key Words (NC4)
A specific word mid-sentence grows to 130, 150% scale for its duration, 1 word per sentence, not every word.
**Remotion:** In the captions data, flag `isKey: true` on 1 word per sentence. In the render component: `transform: isKey ? 'scale(1.4)' : 'scale(1)'` with a `spring()` transition.

### 2.3 Color Swap on Emphasis (NC4, NC3)
Key word turns from white to a brand color (gold, red, or teal) for 1, 2 seconds.
**Remotion:** `color: isKey ? '#C9A84C' : '#FFFFFF'` with a `spring` on opacity of a colored overlay layer underneath.

---

## SECTION 3: ANNOTATION / MARKER TECHNIQUES

### 3.1 Hand-Drawn Circle Appearing (NC3, ODRJkEGTI_U chalkboard scenes)
A felt-tip or chalk circle draws around a UI element over ~15 frames (half a second).
**Remotion:** Use an SVG `<circle>` with `strokeDasharray` = circumference and `strokeDashoffset` interpolated from circumference→0 over 15 frames. Pair with pen-scratch SFX on frame 1 of the draw.

### 3.2 Underline Draw-On (NC3 "SUBTITLES", "Front Loading" cards)
A horizontal line draws under a word from left to right.
**Remotion:** SVG `<line>` with `strokeDashoffset` from full-length→0 over 10 frames. Use `strokeLinecap="round"` for a natural brush feel.

### 3.3 Arrow Pop-In (NC3 diagrams, NC2 graph annotations)
An arrow appears pointing at a feature, snapping in with a slight overshoot.
**Remotion:** SVG `<path>` for arrow body + head. Animate `scale` with `spring({damping: 8, mass: 0.5})` to get the overshoot snap. Pair with a sharp "tap" SFX.

### 3.4 Chalk / Marker Text Write-On (NC3 chalkboard: "Don't Over Edit", "Big Transitions")
Letters appear as if handwritten, each character appearing sequentially with a slight delay.
**Remotion:** Split string into chars. Each char: `<Sequence from={i * 3}>` so they appear 3 frames apart. Use a slightly rough/textured font (Google Font: "Permanent Marker" or "Kalam").

---

## SECTION 4: TITLE CARD TECHNIQUES

### 4.1 Dark Premium Title Card (NH · every section turn)
Near-black background (#0A0A0A or deep navy), large white headline, small subtitle in muted color, subtle grain texture overlay.
**Remotion:** Full-frame `<div style={{background:'#080C12'}}>`. Headline in `Inter ExtraBold` 72, 96px, subtitle in `Inter Regular` 28px at 60% opacity. Add a noise SVG filter (`feTurbulence`) at 3, 5% opacity for grain.

### 4.2 Color Accent Line on Title Card (NH · teal bar left of headline; NC3 red markers)
A 3, 4px vertical or horizontal bar in accent color beside or under the headline.
**Remotion:** `<div style={{width:'4px', height:'80%', background:'#C9A84C', borderRadius:'2px'}}` absolutely positioned left of headline. Animate height from 0→100% with spring on card entry.

### 4.3 Two-Word Impact Card (NH: "MAGIC / TRASH" cards)
Just 2 enormous words, full frame, one per line, maximum contrast, used once or twice max for emotional punctuation.
**Remotion:** `fontSize: 'clamp(80px, 18vw, 160px)'`, `letterSpacing: '-0.02em'`. Each word on its own line, staggered entry by 8 frames. Pair with a low bass thud SFX.

---

## SECTION 5: B-ROLL / FOOTAGE TECHNIQUES

### 5.1 Screen-Recording as Full-Frame B-Roll (NC4 OBS section, NH timeline closeups)
The screen fill the entire frame, no phone-in-hand framing. Shows the real tool/site at work.
**Remotion:** `<Video src={screenRecording} style={{width:'100%', height:'100%', objectFit:'cover'}}`. Apply Ken Burns: `transform: scale(${interpolate(frame, [0, durationInFrames], [1.0, 1.04])})`.

### 5.2 Ken Burns on Still Images (NC4 explains this; NC2 website thumbnail examples)
Any still screenshot or static image slowly scales 3, 5% over its duration, never a static dead frame.
**Remotion:** `transform: scale(${interpolate(frame, [0, duration], [1.00, 1.05])})` on any `<Img>` component. Always use `transformOrigin: 'center center'` to avoid edge drift.

### 5.3 Scale-Down for Comedy/Contrast (NC4: "scale a clip to 80% for a joke")
A clip or image shrinks to 70, 80% and re-centers, used once for a "but wait" beat.
**Remotion:** `transform: scale(0.78)` with `borderRadius: 12px` and a subtle `boxShadow`. Appears with a quick spring + quiet "squish" SFX.

### 5.4 Side-by-Side Comparison (NC3 "Younger vs Older Audiences" card; NC1 character poses)
Two items float in from left and right, meeting center screen simultaneously.
**Remotion:** Two absolute-positioned `<div>` elements, each with `translateX` spring from ±200%→0. Add a divider line that draws in from center outward after they land.

---

## SECTION 6: PACING / STRUCTURAL TECHNIQUES

### 6.1 Frontloaded Edit · More Cuts in First 30s (NC3 explicit retention-curve frame; NC4 "cut every 1-4 seconds intro")
The timeline is densest at the start. After ~30s, cuts slow by ~30%.
**Remotion:** Define sections with different `targetCutDuration` props, `intro: 60, 90 frames (2, 3s)`, `body: 90, 120 frames (3, 4s)`, `payoff: 120, 150 frames (4, 5s)`.

### 6.2 Obama Pause (NC3 explicit reference · "confident silence")
A 1.5, 2 second pause where no new element appears and music is barely audible. Used once after a strong claim.
**Remotion:** A deliberate `<Sequence>` with a held shot and no annotation events. Music volume interpolated to -30 dB then back up.

### 6.3 Section Riser (NC4 timeline: riser clip before section cut)
Half a beat (8, 12 frames at 30fps) before a section-turn cut, a rising tone or drum fill builds.
**Remotion + Audio:** Pre-bake riser SFX clip (free from Freesound). Place it with `<Audio startFrom={section.startFrame - 10}`. Use `volume={interpolate(frame, [start, start+10], [0,1])}`.

---

## SECTION 7: SOUND DESIGN TECHNIQUES

### 7.1 Sound Per Element (NC4 "the single biggest thing"; NC2 explicit demonstration)
Every annotation, caption pop, title card entry, and B-roll cut has a corresponding audio hit. Not a general music track, individual SFX tied to visual events.
**Remotion:** Maintain a `soundEvents[]` array in the composition props. Each event: `{frame, src, volume}`. Loop array and render `<Audio key={i} src={e.src} startFrom={e.frame} volume={e.volume} />`.

### 7.2 Music Duck Under VO (NC4 "-10 to -20 dB under VO"; NC3 similar)
Music is clearly present in the background but the VO voice dominates at all times.
**Remotion:** Set music `volume={0.18}` (roughly -15 dB relative). When VO is silent between sections, raise to `volume={0.45}`. Use `interpolate` to crossfade.

### 7.3 Music Section Change (NC4 "change the song every 30-90s")
At each major section turn, the music track changes energy, often a harder beat in, a softer tone mid, a lift into CTA.
**Remotion:** Use multiple `<Audio>` components, each with `startFrom` and `endAt` props. Crossfade via volume interpolation over 15 frames at the join point.

### 7.4 Sound-Enhanced Real Audio (NC4 "fake/enhance real sounds · LOTR ring trick")
A natural sound in footage is boosted or a complementary SFX layered under it for impact.
**Remotion:** Layer a `<Audio src={sfx}>` starting 2 frames before the real sound in the footage clip. Keep volume low (0.3) so it blends.

---

## SECTION 8: CHARACTER / PERSONALITY TRICKS (Bonus · Curtiss-native)

### 8.1 Animated Logo-Character (NC1: logo face on animated body)
A brand logo or face composited onto a stock animated character, multiple poses side-by-side, each keyframed in from off-screen.
**Remotion:** Use a sequence of character PNG frames (exported from After Effects or built-in CSS animation). Each pose: absolute positioned, `translateX` spring from +120%→0. This is optional for MARKER style but available.

### 8.2 Motion-Tracked Logo Stamp (NC4: profile pic tracked onto person's head)
A logo or avatar rides on top of a moving element in footage throughout a clip.
**Remotion:** Pre-compute motion path in Python (OpenCV tracking). Pass `x[]`, `y[]` arrays as props. Render `<Img style={{position:'absolute', left:x[frame], top:y[frame]}}/>`. Advanced, skip for v1.

---

## SECTION 9: WIRE THESE (Integrations Worth Adding)

### Whisper (word-level captions pipeline) · ESSENTIAL
**Why:** NH explicitly shows word-level timestamps as the foundation. Without it, captions are estimated/manual.
**Tool:** `openai-whisper` Python package (free, local). Run: `whisper audio.mp3 --output_format json`. Parse `segments[].words[].start/end` into `captionsData.json`. Feed to Remotion as a prop.
**Cost:** Free (runs on CPU locally; GPU = faster).

### Freesound.org API (free SFX library) · ESSENTIAL
**Why:** NC4 is explicit that a sound on every element is the biggest quality lift. Need 20, 30 SFX clips: marker-squeak, underline-draw, paper-tap, whoosh-soft, whoosh-hard, cash-register, bass-hit, riser-5s.
**Tool:** Freesound API (free account, 60 calls/min). Search `/search/text/?query=marker+squeak&filter=duration:[0 TO 2]`. Download `.wav`, convert to `.mp3` via ffmpeg, place in `public/sfx/`.
**Cost:** Free.

### Pexels API (free B-roll video fallback) · OPTIONAL
**Why:** NC4 cites Pexels for free B-roll. Use only as filler if a real screen-recording is not available for a section.
**Tool:** `https://api.pexels.com/videos/search?query=...` with `Authorization: PEXELS_KEY`. Note: requires browser `User-Agent` + `Referer` headers (seen in reference_free_video_pipeline.md).
**Cost:** Free tier: 200 requests/hour.

### ElevenLabs TTS (George VO) · ALREADY WIRED
**Why:** NH and NC4 both use a single consistent narrator voice throughout. King's "George" voice is already in `.env.master`.
**Note:** Key already active. Call `POST /v1/text-to-speech/{voice_id}` with `model_id: eleven_multilingual_v2`. Use stability=0.5, similarity=0.75.

### ffmpeg (local, already installed) · ALREADY WIRED
Used for: extracting frames for QA, trimming audio, crossfading music clips, converting SFX to .mp3.
**Cost:** Free.

---

*Written by ANALYST agent from frame-by-frame study of 5 reference videos. 2026-06-06.*
