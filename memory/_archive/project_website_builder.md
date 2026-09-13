---
name: project-website-builder
description: "Website Builder project, Claude builds HTML/CSS sites, Vercel deploys them. New income stream."
metadata: 
  node_type: memory
  type: project
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

New project created 2026-05-15 as part of Day 3 full setup (Nate Herk Ch 11).

**Status:** [NEW], Project structure built. Vercel account not yet created.

**Folder:** `C:\Users\Dell\Documents\Website Builder\`
**Skill:** `/website`

**WAT chain:**
- W: `workflow\build_website.md`, 6-step SOP: brief → brand → structure → build → review → deploy
- A: Claude, takes plain-English description, reads brand guidelines, builds full HTML/CSS/JS
- T: `tools\deploy_vercel.py`, deploys finished site folder to Vercel via CLI
- S: `/website`, one command triggers the full pipeline

**Pricing:**
- Landing page (1 page): €300, €800-3, 5 days
- Service site (3-5 pages): €800, €2,500-1, 2 weeks
- Monthly maintenance: €100, €300/month

**Setup needed before first use:**
1. Create free account at vercel.com
2. Install CLI: `npm install -g vercel`
3. Login: `vercel login`
4. Type `/website` and describe the site, Claude builds it, deploy

**How to apply:** When King David gets a website client, type `/website` and describe what they need. Claude builds the full site, asks for review, then deploys to Vercel. Client gets a live URL.

**Why:** Every business needs a website. Build in 1-2 days. Charge €300, €2,500. Pairs naturally with the lead scraper and newsletter service for a full client package.
