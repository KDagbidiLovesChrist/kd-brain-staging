---
name: feedback-verify-visual-artifacts-before-sending
description: "King's explicit correction, verify any visual/interactive artifact actually renders before publishing it to him, don't ship on code-review confidence alone"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: aca3b852-b673-4b57-8583-e94ffdc52583
  modified: 2026-09-06T13:14:22.752Z
---

King's own words, 6 Sep, after a published 3D artifact ("The One-Line, Walked") rendered as a blank canvas: "ALWAYS MAKE SURE YOUR WORK IS WORTHY BEFORE YOU SEND TO ME."

**Why:** A three.js CDN URL was guessed (`three.js/128.0.0/three.min.js`) instead of verified, and cdnjs actually serves it at `three.js/r128/three.min.js`. Since the Artifact sandbox's CSP blocks a bad external script with no visible console error, the whole scene silently failed and only the static HTML/CSS HUD rendered, an empty black canvas went out with a straight face. Fixed by using `WebFetch` on `https://cdnjs.com/libraries/<lib>` (or a specific version path) to confirm the exact file path BEFORE writing the script tag, not after something breaks.

Once the library loaded, a second, more important class of bug surfaced: real composition/logic bugs that only show up in a render, not in code review, an oversized emissive sphere blotting out the frame, a solid-colour object sitting directly on the camera's flight path becoming a giant flat wall up close, fog not matching the scene background, leaving a visible seam. None of these are visible from reading the source.

**How to apply:** For any artifact with real interactivity, 3D/WebGL, canvas, or anything whose correctness can't be confirmed by reading the code (this includes anything using an external CDN script), render it locally before publishing:
1. Verify third-party CDN paths for real first (`WebFetch` the library's cdnjs page, don't guess a version string).
2. Screenshot the actual rendered page with a local headless browser before publishing: `msedge.exe --headless --disable-gpu --screenshot=out.png --window-size=1400,900 --virtual-time-budget=<ms> "file:///<path>"`, then `Read` the PNG.
3. For a page with multiple states/zones (a flythrough, a multi-step flow), check more than the opening frame, at minimum the destination/payoff view too, not just frame one.
4. When testing a scroll- or state-driven scene by directly overriding a JS variable for a screenshot (rather than the default value), inject the override AFTER the real initialization code that sets that variable, not before it, a `var` declaration further down the script will silently overwrite an earlier assignment (this exact mistake burned real time mid-session, don't repeat it).
5. Audit the file afterward for leftover test-only edits (debug titles, hardcoded test camera positions) before the real publish, several rounds of raw find-and-replace testing genuinely left stale test values in the file that would have shipped to King unnoticed if not explicitly grepped for.

This extends [[feedback_staged_qa_loop_standard]] (real proof before showing King, not "should work") into the specific case of visual/interactive artifacts, where "real proof" means an actual rendered screenshot, not a passing mental code review.
