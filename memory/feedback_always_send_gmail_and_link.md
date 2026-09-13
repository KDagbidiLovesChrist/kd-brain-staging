---
name: feedback-always-send-gmail-and-link
description: "Standing delivery rule (King 2026-06-09): when any build/deploy is DONE, always email the live link to King's Gmail AND post the link in the chat. Default delivery for finished work."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 972bb7d5-c2f9-41f3-9f4b-37ce8c5e2ffd
---

When any build or deploy is finished, ALWAYS do two things automatically: (1) email the live link to King's **Gmail** (kingagbidi@gmail.com, and the other two inboxes by default: iCloud + Yahoo), and (2) post the live **link directly in the chat** so he can tap it there too. Don't wait to be asked each time.

**Why:** King works mostly from his phone and voice. He needs the link in Gmail to open/test on his phone, and in the chat for quick access. He said: "always send to gmail and send link here when done."

**How to apply:**
- On every "done"/deploy of a site/app/video, send the link (with a screenshot or two when useful) to his inboxes via the SMTP sender (`GMAIL_APP_PASSWORD`), e.g. `replicas\claude-studio\send_site_to_phone.py` pattern, and a quick ntfy push ([[reference-notify-and-video-pipeline]]).
- Also paste the clickable link in the chat reply.
- Notify all 3 inboxes by default ([[user-name-king]]); Gmail is the must-have.

**⚠️ STRENGTHENED 2026-06-20 (King frustrated a link never reached his phone):** this applies **during TESTING too, not only at "done".** ANY time I produce a link for King to look at/test, it is NOT delivered until I have BOTH emailed it to all 3 inboxes AND fired the ntfy push, automatically, no reminder. King: *"it should just open automatically and send to my phone when we are testing… have an edge-case reassurance, QA things like these you don't forget."*
- **Standing delivery checklist (run every time a link is produced):** ① `tools\push_kd.py` push (title + msg + click_url) → ② SMTP email to TO=[kingagbidi@gmail.com, Kingdavidagb@icloud.com, kingdavidagbidi@yahoo.com] with a big tap button → ③ paste the clickable link in chat. SENDER=kingagbidi@gmail.com, key=`GMAIL_APP_PASSWORD` in `.env.master`.
- Treat "link delivered to his phone" as part of the definition of done, a pasted-in-chat link alone is a FAIL (he's phone-first).
