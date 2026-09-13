---
name: feedback-avoid-base64-email-relay-for-large-files
description: "Do not relay a binary attachment through base64 typed into a tool call for anything beyond a few KB. Tool-output reads truncate around 22 to 25K tokens, and base64 tokenises roughly 2 tokens per character, so the reliable ceiling is small. Prefer uploading text files as textContent to Drive, or point at a local file path, instead."
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b5ada31e-43cd-4032-922e-1828cfd76d48
  modified: 2026-08-28T10:10:23.175Z
---

Never relay a binary attachment (zip, image, etc.) by converting it to base64 and typing that
string into a tool call, once the file is more than a few kilobytes. Tool-output reads (PowerShell,
Bash, Read) truncate around 22 to 25K tokens per call, and base64 text tokenises at roughly 2 tokens
per character, so the reliable ceiling for a single clean relay is on the order of 11 to 12KB of raw
binary. Anything larger risks silent truncation, which produces a corrupted file that looks like it
sent successfully.

**Why:** caught this the hard way on the PaintPots delivery to Samson
([[project_paintpots_samson_website_build]]). Converted a 34KB zip to base64 (46,092 characters),
called PowerShell to output it, and only the first ~2KB preview came back, the rest silently
truncated. Used that partial string as the email attachment content. Samson received a zip file
that would not open. A second attempt to manually reconstruct the base64 from chunked file reads
was abandoned mid-way, too easy for a single mistyped or dropped character to corrupt the archive
again with no way to catch it before sending.

**How to apply:**
- If the files are plain text (HTML, Markdown, JSON, code), skip binary encoding entirely. Upload
  each file individually with its actual text content (e.g. Google Drive `create_file` using
  `textContent`, not `base64Content`). Zero corruption risk, and each file can be read back in full
  to verify before or after upload.
- If the content must be binary (an image, a zip, a PDF you did not just generate from text), do
  not type its base64 into a tool call from memory or from a truncated read. Instead: copy the file
  to a location that syncs or is directly reachable (a local OneDrive sync folder, a Drive upload
  path that accepts a file handle rather than inline content) and hand back a link, not attachment
  bytes typed by hand.
- After any attachment-based send, if there was ever a truncation warning on the way to preparing
  it, do not trust that the file arrived intact. Verify size, or better, avoid the relay path
  altogether per the two points above.
- When in doubt about size, check the actual byte count first before choosing a delivery method,
  not after hitting a truncation wall.
