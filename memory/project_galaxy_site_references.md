---
name: project-galaxy-site-references
description: "Galaxy/portfolio website (kingdavidagbidi.com), King's ACTUAL reference videos + everything rejected. Restart point after a long failed guess-loop on 2026-06-05."
metadata: 
  node_type: memory
  type: project
  originSessionId: dad73e07-c773-4a22-b115-3abbd05033ac
---

# Galaxy Website · King's References + What's Rejected (READ BEFORE TOUCHING THE SITE)

## ✅✅ 2026-06-06 · SITE APPROVED ("website is perfect"). LOCKED = kd-site-v2.vercel.app
King approved the new personal site: **`Documents\Website Builder\kd-site-v2\`** → **kd-site-v2.vercel.app**. The look: **mainly BLACK + GOLD**, gold nebula that **breathes** + **moves & gold-streaks as you scroll** (A/B fly-through feel, focal gold glow grows, never blacks out), **3D tilt+glow** on cards/buttons (desktop hover), gig-card style. Hero = "Leverage AI to grow your business, online & on the tools." Two showcase rows, both card-style:
- **Cinematic Flagships** (the `-animated` deploys): Veyra `veyra-b.vercel.app` · Flux `flux-animated.vercel.app` · Nova `nova-animated.vercel.app` · Meridian `meridian-animated.vercel.app` · Kin `kin-animated.vercel.app` · Atlas `atlas-animated.vercel.app` · Orbit `orbit-animated.vercel.app` · Roast `roast-animated.vercel.app`. (NOT the `-3d` ones = PS2, rejected.)
- **Every gig** (artwork in `kd-site-v2/assets/gigs` + live sample): Websites, Stores, AI Automation, AI Assistants, Lead Gen, Marketing & SEO, Social, Video, Animated, Accessibility.
Engine fully in `kd-site-v2/index.html` (inline). Previews captured via Playwright (headless + swiftshader for WebGL). **NOT yet aliased to kingdavidagbidi.com**, King to decide go-live. Next focus: **the VIDEO/ad**. Earlier rejected: realtime-3D PS2 cards, flat car (Veloce)/clinic, autoplay-only (not scroll), too-static, all-gold-busy, black-out-on-scroll.

## (superseded) DECISION 2026-06-05 (evening): ADJUST the existing live site · do NOT rebuild.
King wants to **make targeted ADJUSTMENTS to his current live site** (kingdavidagbidi.com, the black+gold "Leverage AI to grow your business online & on the tools" site with his laptop photo, nav Services/Work/Pricing/Contact/Book a call). He does NOT want it replaced with a new concept, and does NOT want it left untouched, he wants to **tweak the one he has**. The from-scratch cosmos-glide REBUILD is **PARKED** (prototypes `kd-hub-cosmos.vercel.app` A=`/` B=`/direction-b.html`, `kd-hub-glide-proto.vercel.app`); the generated glide clip (`kd-hub-cosmos/assets/glide-bg.mp4`) is reserved for the **AD/intro only**. **Find the live site's source folder before editing** (likely `kd-hub-galaxy-photo` or a `kd-hub-v*`; verify which is aliased to the apex). Make King's specific tweaks, show him, redeploy + re-alias only on his OK.

On 2026-06-05 (earlier) I rebuilt the site background ~7 ways and King rejected **every one** ("terrible"). The mistake: **guessing instead of cloning his reference videos.** His references are downloaded, use them (kept below for AD reference).

## His reference clips (downloaded)
`Documents\Website Builder\video-edit\refs\king_refs_now\` (emailed today: "Movement", "POV view in start", "In visuals", a main TikTok, "Editing styles"). What they show:
- **astroplaneet / sanjariuss / astronomas_**, vibrant cosmic nebulae (gold/blue/purple/teal) with **planets floating in them**; a **gold Interstellar/Gargantua accretion-disk black hole**.
- **ammo_visuals ("Movement")**, **FPV drone glide/dive**: fast, smooth, banking, falling forward over terrain.
- **"POV view in start"**, first-person astronaut glide along ISS toward Earth; smooth ease-in, gentle tilt.
- **Main TikTok**, one continuous shot **diving DEEPER through evolving glowing nebula clouds**, no loop, banking, dreamy.

**Synthesis = smooth premium cinematic FPV glide/FALL THROUGH space, passing nebulae + planets.** Site tone = **black + gold** (his personal-portfolio palette, see [[feedback_palette_personal_only]]). Cosmos should back the WHOLE site (every section), feeling like you glide/fall through it as you scroll.

## REJECTED 2026-06-05 (don't rebuild these)
planet-globe journey w/ 3 warp variants · DOM planet globes on a space video ("don't match bg") · per-gig dive-zoom + constant-play video ("swiping not falling") · gold-cloud 100-frame scrub (laggy phone) · gold+teal eclipse whole-page scrub (laggy + too teal) · static black+gold parallax (too static) · **seamless-loop gold-ringed-planet glide video** ("terrible", current live state).

## Hard constraints
1. **Smooth on King's PHONE** = pass/fail. Heavy = 100-image frame-scrub + playbackRate video-scrubbing (re-decode). 
2. **Black + gold** (brand), not multicolour.
3. **Reference-driven**, clone the EXACT clip; don't describe ([[feedback_reference_driven_design]]).
4. Don't re-alias `kingdavidagbidi.com` until King OKs (apex still shows OLD galaxy = safe fallback). Staging = kd-hub-galaxy-photo.vercel.app.
5. Lean on KIE, King topped up ~10k credits 2026-06-05 + was unhappy about the burn.

## Path forward
Ask King to point at the SINGLE reference clip that IS the look+movement → clone it precisely, lightweight (smooth-first), black+gold → show a quick HERO/bg prototype → get explicit "yes" on look+smoothness BEFORE extending to the whole site. Then lock site → then build the AD (site = ad's opening shot). Reusable gold/black assets in `Website Builder\seedance\` (glide_final, galaxy_best, galaxy_dive, galaxy_flight2, blackgold). Tools: kie_generate.py, gemini_watch_local.py, download_gmail_media.py, push_kd.py. Full detail: `handoffs\handoff_2026-06-05_18-40_save.md`.
