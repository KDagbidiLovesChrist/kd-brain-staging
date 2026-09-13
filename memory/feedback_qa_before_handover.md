---
name: feedback-qa-before-handover
description: "King's hard rule (2026-06-10): TEST your own work, click every button as a real user, including Back/Forward, and confirm it works BEFORE handing over. He found broken buttons twice that I'd called done."
metadata:
  node_type: memory
  type: feedback
  originSessionId: kd-site-v3-2026-06-10
---

# QA your own work as a user BEFORE handover

King, 2026-06-10, after I twice handed over kd-site-v3 as "done + QA-clean" and he immediately
hit broken buttons ("Book a call did nothing"; "Websites went to SEO"):
> "you need to be testing the work you do the QA after doing it to confirm it works before
> handing over to me" · "interact with every button as a user, any errors you see from anything,
> before moving to next part" · "loop the QA until everything works."

**Why:** handing over untested work destroys trust and wastes his time. He's the user, if I
don't catch it, he does, and it looks like I didn't try.

**How to apply (every UI build, before saying "done"):**
- **Actually interact** with every interactive element as a user, click/tap each button, link,
  chip, card; don't just check it renders. Use real clicks + `elementFromPoint` to confirm the
  tap lands on the right element (catches invisible overlays, see [[reference-beat-overlay-pointer-events]]).
- **Test navigation both ways**, follow each link to its destination, then **Back** and
  **Forward**; confirm no stuck state and the page still works.
- **Verify the destination is correct**, not just that something happened (Websites must go to
  Websites, not SEO).
- **Loop** the QA, fix → redeploy → re-test, until 100% clean, across mobile + desktop + wide.
- **Don't theorise the cause** (e.g. "it's cache"), reproduce it and inspect before claiming a fix.

Related: [[feedback-self-verify-top-performance]] · [[feedback-verify-before-rerun]] ·
[[feedback-dont-overcomplicate]].
