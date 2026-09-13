---
name: reference-live-ai-demo-pattern
description: "How to build a LIVE, working AI demo on Vercel (serverless + Claude) to win Upwork/freelance jobs demo-first, plus the exact gotchas hit building LessonForge + FlowLine on 2026-06-08."
metadata:
  node_type: memory
  type: reference
  originSessionId: kd-firstbid-2026-06-08
---

# Live AI Demo Pattern (the demo-first weapon)

The winning move on Upwork: instead of describing what you'd build, hand the client a **working version of THEIR thing** on a live URL. Two flavours, both deployed to Vercel (free, public via the project's production alias):

## A) LIVE AI tool (real backend) · e.g. LessonForge (lessonforge-demo.vercel.app)
A static `index.html` + a Vercel **serverless function** that calls Claude server-side. Files:
- `index.html`, the UI; calls `fetch('/api/generate', {POST, json})`.
- `api/generate.js`, serverless function. Plain `fetch` to `https://api.anthropic.com/v1/messages` with headers `x-api-key`, `anthropic-version: 2023-06-01`, `content-type`. Use **`claude-haiku-4-5`** for cheap demos (~fractions of a cent/run). Use `output_config:{format:{type:'json_schema',schema:{...}}}` to get clean structured JSON, then render it.
- `package.json` with `{"type":"module"}` (REQUIRED, see gotcha 1).
- Set the key as a Vercel env var (server-side, never in the page).

## B) Static dashboard mockup (no backend, $0) · e.g. FlowLine (kd-flowline.vercel.app)
Just `index.html` with a polished, branded dashboard (fake-but-realistic data). Faster, zero cost, perfect when the demo is "show the system" not "run the AI." Screenshot it for a gig-card thumbnail.

## Deploy
`vercel deploy --prod --cwd <folder> --yes` → use the clean **production alias** (`<project>.vercel.app`) as the public link. (Re-alias the personal domain after any kd-site-v2 deploy: `vercel alias set <prod-url> kingdavidagbidi.com` + www.)

---

## ⚠️ GOTCHAS (all hit + solved 2026-06-08 · don't re-debug)
1. **ESM 500 with empty body** = Vercel treats `.js` as CommonJS, so `export default` crashes at load. **Fix:** add `package.json` `{"type":"module"}`.
2. **`TypeError: Cannot convert argument to a ByteString … value 65279`** = a **BOM** got into the API key when set from PowerShell (`.env.master` is UTF-8-with-BOM, and piping to `vercel env add` re-adds a BOM). **Fix:** sanitise the key at runtime in the function: `const key=(process.env.ANTHROPIC_API_KEY||'').replace(/[^\x21-\x7E]/g,'')`. Don't fight the shell.
3. **New Vercel project = deployment protection ON** → the raw deployment URL (`*-<hash>-king-david-s-projects2.vercel.app`) returns **401**. The clean production alias (`<project>.vercel.app`) is public. Always test + link the **clean alias**, not the hash URL.
4. **Project-name collision**, `flowline-demo` already existed (an old AI-receptionist demo owns `flowline-demo.vercel.app`). A new folder of the same name created a separate, protected project. **Fix:** use a unique project/folder name (named it `kd-flowline`). The `.vercel.app` namespace is global.
5. **`vercel env rm` needs `--yes`** (piping "y" doesn't work). **`vercel alias set` needs `--yes` too** for some flows.
6. **No em-dashes in client-facing demo copy** (King's hard rule), caught one in FlowLine, replaced. Check every demo page before shipping.

## QA before sending a site/demo (King's standard)
Use Playwright: check **0 console errors**, **0 broken images** (`[...document.images].filter(i=>!i.complete||i.naturalWidth===0)`), **no horizontal overflow** (`scrollWidth > innerWidth`), and on a card grid **even count + uniform card height** (odd count in a 2-col grid leaves a lone half-row). Test at **390px (phone)** AND desktop. Related: [[demo-library]] · [[feedback-personalised-demos]] · [[feedback-sound-human-not-ai]].
