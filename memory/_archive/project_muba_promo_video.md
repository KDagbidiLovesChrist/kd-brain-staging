---
name: project-muba-promo-video
description: "🔴 The promo VIDEO (2026-06-06 15:30). After many MARKER (scroll+caption) iterations King said 'doesn't look edited, looks the same, not like the YouTube videos', RIGHT. BREAKTHROUGH = new KineticEdit engine (fast-cut montage, a cut every ~0.85s). 12s proto LIVE on kd-review, awaiting his verdict on the energy. €0 earned."
metadata: 
  node_type: memory
  type: project
  originSessionId: aa4d3aad-d071-43ce-a0da-8880250ec40e
---

# The Promo Video · status 2026-06-06 15:30

## Where it stands
King wants a faceless 9:16 promo for his one-man AI studio (websites, shops, AI assistants, automation, content/video) that is EDITED like the Nate Curtiss YouTube videos he sent. After a long session of MARKER iterations he was clear: **"it looks exactly the same, doesn't look edited, not like the YouTube videos."** He was right, and I built the fix.

## ❌ Why MARKER failed the "edited" test
`MarkerEdit.jsx` = premium full-screen site footage + bold caption + dark cards. Even after adding deep dives + multi-shot `shots[]` + money/time payoff (the 74s `marker-final.mp4`), it's a **slow scroll with text**, fundamentally NOT the reference grammar. The references cut every ~0.85s with a DIFFERENT visual each cut. Stacking zooms on one scrolling clip can't replicate that. The multi-agent team reproduced the same look because they used the same engine. (Engine still exists + works; King just doesn't want that style.)

## ⚡ THE BREAKTHROUGH · `KineticEdit` engine (the keeper)
`Built With AI\remotion\styles\KineticEdit.jsx` (registered in `Root.jsx`). Built by re-studying the references frame-by-frame (0.5s grid in `refs\king\yt\study\`). A **fast-cut montage**: flat `shots[]`, a cut every ~0.6-1.2s, types:
- `text`, kinetic pop-caption (words spring in, 1-3 words, one gold word)
- `clip`, a site-flash with a zoom-punch (src=frame, rate~0.25 holds the good frame)
- `stat`, a money counter ticking to a value (€6,480 / "a month, on autopilot")
- `icons`, a row of service icons (web/shop/ai/auto/content)
Whoosh on EVERY cut, ping on gold words, impact on the first hit. Faceless, black+gold.
**Proto LIVE:** `jobs\kinetic-proto` → `kinetic.mp4` on **kd-review.vercel.app** (⚡ KINETIC at top, slow-scroll `final.mp4` below for contrast). Awaiting King's verdict on the ENERGY.

## 🎯 NEXT (if King approves the energy)
**Script-first** → punchy ~35-40s script → George VO (id `JBFqnCBsd6RMkjVDRZzb`) → build the FULL cut in KineticEdit (hook → the ways → demo flashes → money counter(s) → who → MORE MONEY/MORE TIME payoff → free-sample CTA, VO over the fast cuts). Prove a short segment, then scale. If close-but-not: faster cuts / bigger pop-text / more money+graphics.

## Assets / tooling
- Clean clips (grey cropped): `muba-promo\raw\*_clean.mp4` (fl_meridian, store_fashion, saas_a, w_veyra, g_assistant, g_social), staged in `assets\jobs\muba-promo\`.
- VO in `assets\jobs\marker-extra\`: hook_v2, bridge_v2, who_short, payoff, who_all, v_content, dd_web/ai/auto, who1, who3, hook_short.
- Rubric `knowledge\video_rubric.md` (MS1-MS8); techniques `video_techniques_digest.md` + `video_editing_playbook.md`; sound map `jobs\marker-proto\sound_map.md`.
- Pipeline `video-edit\tools\video_edit.py`. Agents must render FOREGROUND (background renders die when the agent ends).
- See [[feedback-edited-not-scroll]], [[reference-portrait-capture-footage]], [[project-upcoming-tasks]].

## Rules from King this session
Forget his prior tone/preference rejections, try ALL the reference techniques. Budget open ("if we have to spend, spend"). €0 earned, the video is a perfectionism loop; the money move (sending/`/apply`) is still untouched.
