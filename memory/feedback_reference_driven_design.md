---
name: reference-driven-design
description: "For visual style work, get the actual reference video/image first, text descriptions only get to ~60% fidelity, last 40% needs frame-by-frame visual reference"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8a918888-62f1-45e7-b6da-0e50caf372bc
---

# Reference-Driven > Spec-Driven for Visual Design

When the task is "build something to match a specific visual style (Mubashir's, Cold Fusion's, etc.)", get the actual reference asset BEFORE building. Text descriptions of visual style produce ~60% fidelity. The remaining 40%, specific cut rhythm, transition feel, B-roll texture, music character, precise color grade, can only be captured by dissecting a real reference.

**Why:** Validated 2026-05-26 night session. Spent ~70 min building two Remotion proofs of a "dramatic motion-graphics finance documentary" style based on (a) my own interpretation of "Mubashir-style" and (b) a 6-bullet text pitch KD pasted from Mubashir's Fiverr gig. KD's honest read: *"The video is okay. Not really. You almost had it from text."* He confirmed the only way to nail it is to see the actual reference.

**How to apply:**
- For any future "make it look like X" task, ask for the reference asset FIRST. Don't build from text.
- If the reference is behind a login wall (Fiverr portfolio, etc.) and WebFetch/Playwright is blocked: ask the user to screen-record on their phone + AirDrop. Less brittle than scraping.
- When the reference arrives, dissect frame-by-frame: cut timing, transition style, color grade, text overlay patterns, music character, B-roll selection, sound design. Then build.
- Text-described style work is fine for *first-pass exploration* (proves a stack is viable, validates direction at a high level), but never ship from a text-only spec when the user has a specific visual target in mind.

**Related:** [[interview-applicant-first]], same principle for personal documents (CV, cover letter): get the source-of-truth from the person, don't fabricate from third-party context.
