---
name: feedback-playwright-browser-clarity
description: Always tell King David exactly which browser window or tab to look at when using Playwright
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 7faac182-bade-410c-ac57-df9a2deeb423
---

When using Playwright browser automation, always explicitly tell King David which window to look at before asking him to do anything in it.

**Why:** He often has multiple browser windows open and gets confused about which one I'm controlling vs his own. He has to hunt through tabs to find the right one, which breaks his flow.

**How to apply:**
- Say "Look at the Playwright browser window, it should be the one that just opened with a dark purple/grey toolbar" OR "Look at the tab titled [exact page title]"
- When switching between pages in Playwright, announce it: "I'm navigating to X now, watch that same window"
- When I need him to type something in the Playwright browser, say: "In that same Playwright window, click [X] and type [Y]"
- When he needs to use HIS OWN browser (not Playwright), say: "Open your own Chrome/Edge, not the Playwright window, and go to..."
- Always close unnecessary Playwright tabs before asking him to interact

**Rule:** Never silently navigate and then ask him to act. Always state which window, which tab, and what he'll see before he looks.
