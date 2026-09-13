---
name: reference-king-video-style-saasui
description: "The editing style King wants for his videos, derived by cross-referencing the 3 reference sources he sent (2026-06-07): saved TikToks + a masterclass YouTube video + the @whatastory channel. The common thread = 'beat-synced SaaS UI animation'. Read before building any King promo/ad video."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-video-refs-2026-06-07
---

# King's target video style = "Beat-synced SaaS UI animation" (from his own references)

On 2026-06-07 King sent 3 reference sources and asked me to cross-reference for the style common to all
three (not to copy any one). Sources: (1) 9 saved TikToks emailed to kingagbidi@gmail.com subject **"Video refs"**
(creator/POV clips about making SaaS & motion videos: @raihanvisuals, @yasin.vfx, @fabiscreativevision, @diyxstudios,
+ ClickUp/Cal.com/currency/widget SaaS ads); (2) a YouTube masterclass `zWbLfFA9l8s` teaching the "SaaS Animation
Style"; (3) the **@whatastory** channel (premium SaaS explainer motion-graphics, has MANY styles, so cross-ref, don't copy all).

## The common DNA (present in essentially every reference)
1. **The hero is animated UI that INTERACTS, not scrolls**, a search bar types itself, a dropdown opens, cards
   slide/pop, an app icon bounces, a dashboard reacts, a chat types + replies.
2. **Everything is locked to the music beat**, cuts AND each animation hit the beat; music drives the whole edit
   (lo-fi / electronic / trap). This is the #1 signature.
3. **Pop / bounce / overshoot + glow** on text and UI (springy `back.out` easing).
4. **Clean bold sans-serif text**, centered, pops in, with ONE accent colour highlighting the key word.
5. **UI sound design**, typing ticks, clicks, whooshes, pops, under the track.
6. **Fast cuts (0.5, 1.5s)** + a **hook in the first 2-3s**.
7. **Two background flavours both appear:** bright clean white (ClickUp/Cal.com look) OR dark moody with glow
   (raihanvisuals/yasin look). King chose "show both" in the proto.

## Why it fits King
His demos ARE UIs (NOVA site, KIN shop, Rivella AI chat, Relay dashboard, lead-finder). So don't scroll them, **animate the interactions** (a message types into the AI chat, a deal card pops onto the dashboard, a button clicks
with a glow + a click sound), all on the beat. A premium, sellable style; bigger step up than the slow-scroll ad or
the text-only fast-cut.

## First proto built (2026-06-07) · `video-projects/kd-ad-saasui/`
12.6s, 1080×1920, 30fps. Native HTML/GSAP UI (so it really types/pops). Scenes: HOOK → AI chat (types "Do you fix
boilers?" → "Booked you in for tomorrow 9am ✓") → dashboard (€count-up + glowing bars + "Deal won €1,860" toast) →
gold WIPE → search (types "cafe website dublin" + 3 site cards pop) → booking (slot tap → big "Booked ✓") → CTA.
DARK+glow first half, BRIGHT+clean second. Real 120BPM beat + UI SFX (`tools/build_audio.py`). Delivered: email
**19ea34d5597cb81b** + kd-review.vercel.app (green SAAS-UI card). Awaiting King's verdict: direction? + dark/bright/mix?

## Build techniques (reusable)
- Beat track: synth kick/hat/snare via ffmpeg lavfi + place on the 0.5s grid + UI SFX (`build_audio.py`).
- Count-up / typing: GSAP tween a proxy `{n:0}` with `onUpdate` slicing text / formatting number, fires on
  HyperFrames seek-render (deterministic). Same pattern as the launch-video counter.
- Pop-in: `fromTo(... {scale:0.6,autoAlpha:0} -> {scale:1,autoAlpha:1}, ease:'back.out(2.4)', immediateRender:false)`.
- Bars: a flex bar MUST have `height:100%` or it collapses to 0 (scaleY on a 0-height div = invisible). (Bug hit + fixed.)
- No em-dashes in on-screen copy (King's hard rule, hit + fixed in the AI reply).
- Tools: `gemini_editstyle_url.py` (study a YouTube URL's edit style, no download) · `gemini_watch_editstyle.py`
  (local files) · `fetch_video_refs.py` (pull email attachments) · `yt-dlp` for links. Run with PYTHONIOENCODING=utf-8
  (Gemini output has → chars that crash Windows cp1252 console).

## FULL AD shipped (2026-06-08) · ~55s, 4K, LIVE on kingdavidagbidi.com
King approved + it's done ("much better… we done"). The proto grew into a 15-scene ad. **What King insisted the ad MUST say (each was a separate note, bake these into any future King ad):**
1. **LEVERAGE, not a feature list.** Open "WHAT A WHOLE TEAM DOES" → 8 role chips collapse into a gold KD coin "ONE PERSON + AI." Close "Everything a whole company does, from one person, and AI."
2. **WHO it's for = EVERYONE, not just business.** A "FOR EVERYONE" beat: Creators · Trades · Self-employed · Shops · Startups · Big brands. (He flagged creators specifically.)
3. **Concrete value in numbers.** "Admin, automated: ~10 hrs/week → 30 min · Save time. Save money. Make more." (his own example).
4. **His REAL websites IN the animation** (not abstract mockups): relay/lead/nova/kin clips popped in browser cards on the beat.
5. **The offer at the end:** "Your first sample is FREE. Visit us at kingdavidagbidi.com" (voice + on-screen).
6. Creator angle in the content beat: "grow & monetize your socials."

**Build pipeline (reusable):** HyperFrames composition `video-projects/kd-ad-saasui/index.html` (single paused GSAP timeline, scenes timed to Hale VO word-starts) + `tools/regen_vo_hale.py` (body VO) + `tools/gen_cta_tail.py` (append offer line w/o re-timing body) + `tools/seedance_backdrops.py` (gold nebula → ping-pong loop) + `tools/build_audio.py` (beat bed, asplit trick). Render `npx hyperframes render --quality high`; 4K = ffmpeg lanczos upscale (native portrait-4k OOMs on the nebula). Deliver: 3 inboxes (`.claude/tools/send_saasui_full.py`) + kd-review + Desktop. Site: `kd-site-v2` showreel section, re-alias domain after deploy. Full next-steps + gotchas: [[project-upcoming-tasks]].

Related: [[feedback-edited-not-scroll]] · [[feedback-video-quality-bar]] · [[reference-kd-launch-video]] · [[reference-viral-edit-dna]] · [[reference-king-services-audience]] · [[project-upcoming-tasks]]
