---
name: project-hub-rebuild-v3
description: "kd-site-v3 = King's personal site, immersive real-time-3D, NOW LIVE on kingdavidagbidi.com (+ www) since 2026-06-16. Contact bar wired (WhatsApp + Instagram/LinkedIn/X/TikTok/Facebook) + 'It Will Be Done' motto. Earlier (06-10): tap-stealing overlay bug fixed, services = filterable demo gallery, gold fills all-around, optimized, every button click-tested incl Back/Forward."
metadata:
  node_type: memory
  type: project
  originSessionId: kd-site-v3-2026-06-10
---

# Hub kd-site-v3 · 🟢 LIVE on kingdavidagbidi.com (2026-06-16)

King's personal hub. Folder `Documents\Website Builder\kd-site-v3\`. Three.js **r160 ESM**.
**🟢 LIVE on the domain**, **kingdavidagbidi.com** + **www** + **/services.html** (aliased 2026-06-16, verified 200 / 0 errors / 61fps; replaced kd-site-v2). Preview mirror still at kd-site-v3.vercel.app.
**Contact bar wired (2026-06-16):** WhatsApp wa.me/353899582092 + Instagram/LinkedIn/X/TikTok/Facebook icons + the **"It Will Be Done"** motto, on the home contact beat (`#b-contact`, reuses the ICONS SVGs) + the services footer (the `CONTACT` object + `buildContact()`). og:image/og:url now point at the domain.
**Re-alias after ANY deploy:** `cd kd-site-v3` → `vercel --prod --yes` → `vercel alias set <prod-url> kingdavidagbidi.com` + `... www.kingdavidagbidi.com`. QA with `?v=N` cache-busters.
Deploy: `cd kd-site-v3` → `vercel --prod --yes` (team king-david-s-projects2; auto-aliases kd-site-v3.vercel.app).
**Use `?v=N` cache-busters when QA'ing right after a deploy** (CDN/edge caches the HTML briefly).

## Home (`index.html`)
- **KD particle hero = untouched/sacred** (dust morphs KD → worlds → golden-hand-holds-city finale on scroll).
- **Gold particle backdrop now wraps ALL around at any aspect.** The field width was fixed (380) →
  narrower than a wide desktop → black half. Now `FW=clamp(2*(156*aspect+90),440,1600)`, `FH=620`,
  counts ∝ FW (constant density) → fills the whole frustum at 1900-wide AND 390 mobile, 60fps. See
  [[reference-gold-backdrop-3d-dive]].
- **Buttons fixed** (was the big bug): only the **`.active`** beat's children are tappable, see
  [[reference-beat-overlay-pointer-events]]. Hero title visible at p=0 (beatOpHold). Flagships
  grid compacted (3 cols, fits 800h). Finale copy de-duped. Dead `#sound` CSS removed.
- 7 flagship cards (AUREO/LUMO/AURA/MARÉA/AETHER/ASCENT/ISOLA) → external demos. 4 seelinks + 5
  pills → services.html#section. og:/twitter share tags added.

## Services (`services.html`) · REDESIGNED as a filterable gallery (King chose redesign)
- Hero → **category chips** (All·Websites·Stores·AI·Automation·Apps·Content·Video·SEO·Accessibility·Email)
  → responsive **grid of 31 demo tiles** (30 demos + Email tile) → tap = gold dive into the live demo.
  Featured demo per category spans 2 cols + a "Featured" badge. Reuses the `D` demo map.
- **Deep-link BY FILTER (kills the mobile wrong-section bug):** home `#ai`/`#saas`/… → on load
  activate that chip, no scroll-jump. `hashchange` listener re-filters too. All 9 hashes verified → right filter.
- **Arrival**: a gold overlay fades on load (mirrors the home dive-out → continuous journey).
- Background = gold particles + **env_studio.jpg** (was 510KB PNG → 42KB JPG, identical because blurred).
  Footer = Book a call + Email (WhatsApp/socials are PLACEHOLDERS until King provides them). Sound button removed.

## QA done this session (all PASSED, both pages, mobile 390/360 + desktop 1280 + wide 1900)
0 console errors · 0 horizontal overflow · 60, 61fps · every button **clicked as a user** (CTAs→cal.com
tab, seelinks/pills→correct filter, cards/tiles→correct demo) · **Back/Forward clean** (no stuck dive) ·
loop reset works · KD hero intact · gold all-around verified.

## OPEN / NEXT (King's call)
1. King re-tests on his phone (pull-to-refresh once, no-cache header now in `vercel.json`).
2. Tell me his **"also"** (he typed it, it cut off) + **WhatsApp # + social links** → finish contact bar.
3. **Alias kingdavidagbidi.com → kd-site-v3** on his explicit GO only (then update og:image/url host).
4. Optional: per-category featured ordering on services; matching "arrival" on external demos (can't edit those).

## References
- Gold field + dive + r160 freeze bug + all-around fix: [[reference-gold-backdrop-3d-dive]].
- The button overlay bug + fix + QA method: [[reference-beat-overlay-pointer-events]].
- QA-your-own-work rule: [[feedback-qa-before-handover]].
