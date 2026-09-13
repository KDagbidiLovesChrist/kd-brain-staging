---
name: reference-beat-overlay-pointer-events
description: "The tap-stealing overlay bug + fix for stacked-beat sites: inactive beats' interactive children (.cta/.pills/.cards) keep pointer-events:auto and float invisibly over the active beat, stealing taps. Fix = only the .active beat's children get pointer-events. Found 2026-06-10 on kd-site-v3."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-site-v3-2026-06-10
---

# Tap-stealing overlay bug (stacked-beat scroll sites)

On kd-site-v3 (and any site where all "beats"/sections are `position:absolute` stacked at the
same screen-center and cross-fade on scroll), **buttons on INVISIBLE beats can still steal taps.**

## Symptom (how King found it)
- "Book a free call" did **nothing** when tapped.
- Tapping the **Websites** link landed on **SEO**.
One root cause, both symptoms, `document.elementFromPoint(btnCenterX, btnCenterY)` returned a
**different beat's** element (e.g. `DIV.pills` from the services beat) sitting over the visible button.

## Why
- The beat CONTAINER is `pointer-events:none`, and the JS toggled the **beat element's**
  `pointer-events` to auto/none by opacity.
- BUT each interactive child (`.cta`, `.cards`, `.seelink`, `.pills`, `.tiers`, `.contactrow`,
  `.pillx`) had its OWN `pointer-events:auto` in CSS. A child's explicit `auto` **re-enables it
  even under a `pointer-events:none` parent** (pointer-events is inherited, but an explicit value
  on the child wins). So invisible beats' buttons stayed live and, being centered on top of the
  visible beat, intercepted the tap.

## Fix (clean, keeps drag-spin working on empty areas)
1. Add: `.beat:not(.active) :is(.cta,.cards,.seelink,.pills,.tiers,.contactrow,.pillx){pointer-events:none;}`
2. In the rAF loop, toggle `.active` on the beat instead of setting its inline pointer-events:
   `b.el.classList.toggle('active', o>0.5);`  (was `b.el.style.pointerEvents = o>0.5?'auto':'none'`)
- Result: only the **active** beat's buttons are tappable; the `.beat` itself stays
  `pointer-events:none` so empty areas pass taps through to the canvas (drag-spin survives).

## QA method that CATCHES this (do it for every button)
For each button, scroll its beat to full opacity, then:
`const h=document.elementFromPoint(cx,cy); ok = h===el || el.contains(h) || h.closest('a')===el;`
If `h` is a different element → BLOCKED. Settle ≥800ms (a beat far down the scroll needs the
smoothed `p` to reach >0.5 first, else its own button reads as blocked, not a real failure).
Then ALSO click each as a user + test Back/Forward (`pageshow`→resetWarp keeps it clean).

## Lesson
I first blamed CDN/browser cache for "Websites→SEO", **wrong.** Always reproduce + inspect
`elementFromPoint` before theorising. (No-cache headers added anyway as belt-and-suspenders, see [[project-hub-rebuild-v3]].) See also [[feedback-qa-before-handover]].
