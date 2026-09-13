---
name: feedback-qa-against-reference-and-data
description: "QA every relevant output by MATCH-CHECKING it against the reference winners we model + the data, not just \"does it run\". Applies to voice pacing and the majority of QAs."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 2ba59bb5-296d-4799-a925-202e0e0fbd35
---

King's standing rule (2026-06-28, after the Revolut draft missed the mark): **QA is a MATCH-CHECK against the competitors/inspiration + the data, not a does-it-work check.** Our whole method is "model the proven winner" (Rule #17), so the QA must close the loop: put our output next to the reference winner (e.g. @faceless.inc.proj, @hustle.faceless, the niche's top videos) AND the data (cut pace, length band, caption style, pacing), and confirm the similarities are actually there. If it doesn't match their quality/style, it fails QA, fix it before sending.

This applies to **the majority of QAs**, explicitly including **VOICE** (pacing edited to match the references' punchy energy, not just EQ/mastering, tighten dead air, match the rhythm), and to captions, motion, cut pace, length, structure, b-roll quality.

**Why:** the inspiration comes from data; if the output doesn't measurably resemble the proven winners, the modelling failed and the result won't perform. "It rendered" is not the bar, "it looks/sounds like the top videos in the niche" is. (Extends [[feedback-multi-source-consensus-research]] + [[feedback-consensus-everything-rule]] + [[feedback-no-overselling-verify-before-send]].)

**How to apply:**
- Before sending ANY produced asset, hold it against the reference winner + the decoded spec ([[reference-faceless-inc-edit-style]]) + the produce/edit data ([[reference-faceless-video-results-consensus]], produce_spec.py / edit_analyze.py) and list, concretely, where it matches and where it doesn't.
- VOICE: edit the pacing to the reference rhythm (tighten gaps, match energy), then master. Judge by data + ear ([[reference-voice-take-judging-consensus]]).
- If a gap exists, fix it or say so honestly, never ship the shortcut and imply it matches ([[feedback-no-overselling-verify-before-send]]).
- Production tool must be capable of the match: real edit engine (Remotion / CapCut+Submagic), NOT an ffmpeg slideshow. The 2026-06-28 lesson: a static ffmpeg assembly can never match an edited UGC video.
