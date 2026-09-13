---
name: feedback-verify-contact-info-before-sending
description: "Never guess a contact's email address from a name or partial spelling and send to it. Ask King directly for the exact address before any send. A guessed address that happens to accept a send still doesn't confirm delivery to the right person."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b5ada31e-43cd-4032-922e-1828cfd76d48
  modified: 2026-08-28T10:10:38.340Z
---

Never guess a contact's email address from a name, a partial spelling, or a common domain
pattern, and then send something to it. Ask King directly for the exact, confirmed address before
sending anything real.

**Why:** on the PaintPots delivery to Samson ([[project_paintpots_samson_website_build]]), King
gave a rough name only ("Samson Oduwale" from a misheard spelling of a real surname). Guessed
`samson.oduwale@yahoo.com` and sent two real emails to it before any confirmation the address
existed. The mistake only surfaced when a later Google Drive share call to the same guessed
address failed twice with "invalid argument", the actual signal that it was not a real account.
Even then, there was no way to know whether the two earlier emails had silently vanished or
bounced, since email sends do not error on a nonexistent recipient the way a Drive share does.
King had to supply the real address (`Samson.oduwole2120@gmail.com`) directly.

**How to apply:**
- A first name plus a rough surname is not enough to guess an email address, even with high
  confidence in the spelling. Ask for the exact address before the first send, not after a guess
  fails.
- Searching existing inboxes (Gmail search_threads, memory) for a prior message from that person
  is a legitimate way to find a real address, and should be tried first. If that search comes back
  empty, that is a signal to ask directly, not to fall back to a plausible-looking guess.
- A tool that lets you fail fast (like a Drive share returning "invalid argument" on a bad address)
  is more trustworthy than a send-only tool (like email) that will not tell you the address was
  wrong. Where possible, verify an address against a tool that can reject it before using a
  fire-and-forget send.
- If a send already went out to a guessed address before this was caught, say so plainly and
  correct it in the next message to the real recipient (do not just quietly switch addresses).
