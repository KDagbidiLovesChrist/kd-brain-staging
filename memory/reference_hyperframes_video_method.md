---
name: reference-hyperframes-video-method
description: "THE method for making King's videos: use Nate Herk's Hyperframes kit (HTML+GSAP, free/local) at C:\\Users\\Dell\\Documents\\hyperframes-editor, follow MOTION_PHILOSOPHY.md (11 Laws) + the installed Claude skills. STOP hand-rolling my own Remotion engine / gimmicks - that produced amateur output King rejected. Set up 2026-06-06."
metadata:
  node_type: memory
  type: reference
  originSessionId: aa4d3aad-d071-43ce-a0da-8880250ec40e
---

# How to make King's videos · the EXACT method (not my own way)

**Hard rule from King (2026-06-06):** use the ACTUAL tools the pros use and replicate the exact formula. STOP reinventing it my own way. My hand-rolled Remotion `KineticEdit` engine + the floating "KD coin on heads" gimmick = REJECTED as amateur ("videos are so bad"). The MOTION_PHILOSOPHY anti-patterns list literally describes my mistakes (flat text fades, hard cuts, static bg, centered motionless type).

## The tool = Nate Herk's Hyperframes student kit (cloned, free, local, MIT)
- Location: `C:\Users\Dell\Documents\hyperframes-editor` (installed `npm install`, exit 0).
- Stack: **plain HTML + GSAP** (3.14.2 via CDN), paused timeline on `window.__timelines`, **Hyperframes CLI** for lint/preview/render. NOT React/Remotion. Powered by Hyperframes (HeyGen): https://hyperframes.heygen.com
- Needs: Node 20+, FFmpeg on PATH, Chrome (headless render). `npx hyperframes doctor` checks.
- 12 finished example projects in `video-projects/`, COPY one as a template (open its `final.mp4` + `index.html`). Best generic starts: `claude-edit-intro` (minimal brand), `may-shorts-19` (polished 9:16 short), `aisoc-hype` (30s brand hype scaffold). AIS-branded ones = reference only (swap brand-tokens.css + logo).

## The method docs (READ before building · these are the quality bar)
- `MOTION_PHILOSOPHY.md`, the **11 Laws** + technique catalog + pre-flight checklist + anti-patterns. The difference between "it rendered" and "it's good." Re-read every time.
  - Core laws: 1 idea per beat (~1.5s avg, cut fast) · black is the canvas (~90% dark) · lit not colored (chrome gradients, halos, vignette) · camera never sleeps (always drifting) · motion blur hides every cut (whip-streaks, no hard cuts) · object metaphors + callbacks · palette ≤5 hues each with meaning · type is a character (scales 8x, chrome gradient + halo) · hold the hero / breathe the outro (4+s) · unifying grid texture under everything · every timeline ends with `tl.to({}, {duration: SLOT_DURATION}, 0)` (Law 11, kills black-frame flash).
- `CLAUDE.md` (in the kit), workspace guide + the 11 Render Contract rules.
- `README.md`, quickstart, the 12 projects, the authoring loop.

## The installed Claude skills (USE THESE, don't improvise)
Available when working in the kit: `/make-a-video` (beginner end-to-end, interviews then builds w/ preview+verify gates), `/short-form-video` (9:16 talking-head + MG playbook), `/hyperframes` (compositions, captions, TTS, audio-reactive), `/hyperframes-cli`, `/gsap`, `/hyperframes-registry` (install catalog blocks: `npx hyperframes add <block>`), `/website-to-hyperframes` (URL -> video).

## The authoring loop (follow every time)
`edit -> npx hyperframes lint -> npx hyperframes preview (Studio, localhost:3002) -> draft render -> VERIFY FRAMES (ffmpeg one frame per scene) -> final render`. Draft: `npx hyperframes render --quality draft --output renders/draft.mp4`. Final: `--quality standard`.

## For King's promo specifically
- Concept still "The One-Man Army" / AI leverage across many professions (tools AND offices - LinkedIn). Script v3 at `Website Builder\video-edit\jobs\idea-A\script_v3_persona.md`.
- Build it as a NEW project in `video-projects/`, copying a generic sibling, swapping in King's brand (black + gold #0A1628 / #C9A84C / #F4C94B), following MOTION_PHILOSOPHY. Prove ONE beat to the gold standard before the full cut.
- Background research (9 Claude-video-editing tutorials) saved to `knowledge\video_studies\` (`CLAUDE_EDITING_METHOD_ALL.md`). See also [[reference-viral-edit-dna]], [[feedback-edited-not-scroll]], [[feedback-reference-driven-design]].


## ⚡ Drift fixes (2026-07-04, sprint T7)
- **Incremental-edit window rule (adopted from the source video):** author HyperFrames edits in 20-30 second segments, never the whole timeline in one pass — prevents logic drift on long cuts.
- **Scoping note (supersedes the 'never hand-roll engines' line):** "use Nate's kit, stop hand-rolling" applies to NEW engines from scratch. The faceless engine's banked `tools\edit_engine\` compositor is EXEMPT — it passed 12 reference-QA rounds + King's approval and is a Trusted stone. Don't rebuild it; do reuse it.
