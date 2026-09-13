---
name: feedback-show-screen-while-browsing
description: "Always show a screenshot after every browser action so King David can see what's happening on screen in real-time"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: d62f7abd-1ac1-4f04-8ccb-ea31b237dcfb
---

When using Playwright (browser control), take a screenshot AND read it (display it inline) after EVERY action, navigate, click, fill, scroll. King David watches the screen as I work and needs to see each step visually before the next one happens.

**Why:** He said "post it on the screen and I see what you're doing", visual learner, voice input user, needs to follow along in real-time not just see the end result.

**How to apply:** After every mcp__playwright__ tool call, immediately call browser_take_screenshot + Read to display it inline. No silent navigation.
