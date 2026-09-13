---
name: feedback-verify-before-rerun
description: Never re-run a background task on a quiet/buffered output. Wait for the COMPLETION notification or check the result file. Caused a duplicate cold-email send 2026-05-30.
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 8fb279df-42f8-407e-b099-c5ed1554b8ea
---

Before re-running any background job (especially anything that SENDS, emails, messages,
payments, deploys), confirm whether the first run actually finished. Python and many tools
**buffer stdout**, so a background task's output file can look empty/quiet while the process
is still alive and working, or has already finished.

**Why:** On 2026-05-30 a paced 8-email Gmail batch finished in the background, but its output
file was empty (buffered), so it looked hung. I re-ran it. Both runs succeeded → 8 Dublin
businesses each got the SAME cold email twice, ~10 min apart, in King David's name. Sloppy,
hurts the brand impression, not recoverable.

**How to apply:**
- Wait for the harness task-COMPLETION notification (it fires with exit code) before assuming
  a background job hung. A quiet buffer is NOT failure.
- Or check the real artifact (the SEND_LOG / output file / DB row), not just stdout.
- For send/pay/deploy actions, run UNBUFFERED (`python -u`) or in the foreground so the
  state is visible, and make the tool idempotent (skip already-sent recipients via a log).
- When in doubt, verify the side effect (Gmail Sent folder, etc.) before re-firing.

Links: [[project-website-sales]] [[feedback-self-verify-top-performance]]
