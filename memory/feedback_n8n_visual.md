---
name: feedback-n8n-visual
description: King David wants pipeline visuals to match n8n exactly, needs MCP/screenshot access to n8n to learn the style properly
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 184ee3b8-d555-4e02-bb4d-851119a96d2b
---

King David wants any pipeline or automation visual to look exactly like n8n's deployed workflow canvas, not inspired by it, identical to it.

**Why:** He uses n8n and is familiar with that visual language. When showing others his system, it needs to look like the real tool so it's immediately recognisable and explainable.

**What went wrong:** Multiple attempts to replicate n8n style from memory fell short. The nodes looked close but the layout, curves, and overall feel didn't match what he had in his head.

**Fix planned:** Give Claude access to n8n via MCP, screenshot tool, or a live browser session so it can see the actual interface and replicate it accurately, not guess.

**How to apply:** Next time a pipeline visual is requested, ask for a screenshot of the target n8n workflow first OR use Playwright MCP to browse n8n's demo/docs to see the actual interface before building anything.
