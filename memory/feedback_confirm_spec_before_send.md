---
name: feedback-confirm-spec-before-send
description: "King's rule, confirm exactly how he wants a design BEFORE building/sending it, to avoid design mix-ups"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b9b6bf5e-2a62-4125-ba7b-5cacf1f480d6
---

King's standing rule (2026-06-21, house project): **before building or sending a design/deliverable, confirm
with King exactly how he wants it**, read back my understanding of his (and Josh's) instructions and get a
yes/correction first. He said: "when something is sent confirm with me how i want it to be so we dont get
design mix up."

**Why:** several rapid instructions + Josh's reference pics were creating mix-ups (e.g. he sends an island
seating pic but only wants the *arrangement*, not the stools in it; he changed the splashback from black to a
seamless neutral panel). Building first and sending wastes effort and erodes trust.

**How to apply:** when his/Josh's intent is at all ambiguous, restate it plainly + use AskUserQuestion to lock
the specifics BEFORE rendering/sending. Especially for reference photos, confirm WHICH part of the pic he
wants (layout vs material vs colour vs the actual product). Pairs with [[feedback-no-overselling-verify-before-send]]
and [[feedback-qa-until-king-approves]]. Project: [[project-interior-fitout-7adderig]].

**⚠️ STRENGTHENED for Josh (2026-06-22): LISTEN to Josh, don't assume you understand him.** King: *"listen to
Joshua and stop trying to think you understand him, re-explain to him what he wants to make sure and confirm
instead of just saying you understand and send him… make sure it is correct and fits the mathematical
dimensions as well, nothing forced."* The Josh room loop kept auto-rendering + sending on each reply (assuming
his intent). **RULE: when Josh (or anyone) gives a request, read it back to him in his own words as a
checklist and ask him to confirm BEFORE rendering/locking**, don't just say "got it" and send. **AND verify
the furniture genuinely fits the REAL room dimensions** (Josh's room = 2.82 × 2.56 m): check the math (e.g.
queen 1.5×2.0 + wardrobe 1.0×0.6 → ~1.3 m clear strip, ~50% floor left = snug but real). Never force/cram
furniture in just because it's wanted, if it doesn't fit, say so honestly. The dimension-accurate to-scale
PLAN is the proof of fit; an AI render can "force" furniture and hide a bad fit. Keep it consistent with the
overall house plan. Pairs with the geometry method ([[reference-floor-swap-ai-limit-showhome-method]]).

**⚠️ The #1 cause of mix-ups (2026-06-21): a reference King sent was a Google Drive link that is LOGIN-LOCKED**
(opening it redirects to a Google sign-in / `gdrive_dl.py` fails). I couldn't open his "where I want the fridge"
video (`IMG_7701/7702.mov`) so I GUESSED and got it wrong twice → he was rightly frustrated ("why do you get
confused"). **RULE: the moment a Drive link is login-locked, TELL KING plainly "I can't open it, it needs a
login" and ask him to either set it to "Anyone with the link" OR send a plain photo/screenshot, NEVER guess
what's in a file I can't see.** (His phone's Gmail "Drive video" inserts = login-locked; a normal photo
attachment like `IMG_7703.png` works fine.) The claude.ai Google-Drive MCP CAN read his file metadata but a
72MB video can't be pulled as base64, so a plain photo/screenshot is the reliable channel.
