# sebintel study — free CLI skills for design + video (2 TikToks, 2026-07-04)
> Studied frame-by-frame in Claude Code web (cloud session — no Gemini key by King's keys-off-cloud rule; ffmpeg frame extraction instead; audio transcription blocked by network policy, burned-in captions read from frames).
> Creator: **@sebintel** (TikTok). King sent 2 clips: "learn from him, get his video ideas + prompting for our brand and better results."

## One-paragraph summary + the "wow"
Sebintel's whole channel formula is: **Claude Code + one free skill install = a pro result that used to cost thousands** ("build a $10,000 website", "Claude just learned to edit videos"). The wow for us: everything he sells as the secret is a **free, open-source CLI install** — and half of it is already in the KD brain. The genuinely new pieces are the **`npx skills` CLI** (one-command skill installs), the **official Remotion agent-skills bundle**, and the **UI UX Pro Max design-intelligence skill**.

---

## Video 1 — "Build a $10,000 website" (~43s)
**Hook:** flashes 3 jaw-dropping concept sites (Deadpool "CineDaily" movie site, VR BOXXX headset store, a loud pink/purple drinks brand) + "$10,000" on screen before explaining anything. Proof first, method second.

**His method (from frames):**
1. Install Claude Code (shows the official docs quickstart, `curl -fsSL https://claude.ai/install.sh | bash`).
2. Install the design skill: **UI UX Pro Max** — terminal shows `uipro init --ai cursor` (works for Claude Code too: `uipro init --ai claude --global`, or the Claude Code plugin route).
3. Browse **Magic UI** component galleries (hero sections, grid patterns, backgrounds) and feed picks to Claude.
4. Prompt Claude section-by-section ("every section…") with the skill active; Claude writes the site code live.

**Verified (real + free):**
- UI UX Pro Max = open-source skill by nextlevelbuilder: **67 UI styles · 161 colour palettes · 57 font pairings · 99 UX guidelines · 161 reasoning rules**, plus a v2 Design System Generator. Install into Claude Code: `/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill` then `/plugin install ui-ux-pro-max@ui-ux-pro-max-skill` (or `uipro init --ai claude --global`). Sources: [GitHub](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) · [docs](https://ui-ux-pro-max-skill.com/docs/cli-reference/) · [dev.to write-up](https://dev.to/wonderlab/open-source-project-of-the-day-part-7-uiux-pro-max-skill-ai-design-intelligence-for-building-4bd5)
- Magic UI: already in the brain's client tools plan (shadcn MCP + Magic UI + Aceternity).

## Video 2 — "Claude just learned to edit videos" (~38s)
**Hook:** a stunning samurai-ink/origami motion-graphics gallery ("HONOR", "THE WEIGHT OF STEEL") — output first, again.

**His method (from frames):**
1. Install the official Remotion agent skills: **`npx skills add remotion-dev/skills`** (the `npx skills` CLI is Vercel's open agent-skills tool).
2. Claude then knows Remotion's frame-based timing, compositions, audio sync → builds **motion reels in code** (frame shows a "Claude motion reel · HTML" artifact: kinetic typography, scene timeline, Anton/Space Grotesk fonts, red/yellow/cream palette — the "AI is EVERYWHERE" reel).
3. For editing real footage: upload the clip + prompt: **"Make sure you apply cuts, zooms, captions, graphics inside the upload…"** — one instruction naming the exact edit moves.

**Verified (real + free):**
- `npx skills` = [vercel-labs/skills](https://github.com/vercel-labs/skills), free. Remotion bundle = [remotion-dev/skills](https://github.com/remotion-dev/skills): 4 skills (remotion-best-practices, 3d, mediabunny…), installs to `.agents/skills/`. Docs: [remotion.dev/docs/ai/skills](https://www.remotion.dev/docs/ai/skills)
- ⚠️ **Honest flag:** Remotion itself is free for individuals/small teams but needs a paid company licence past ~3 people. King solo = FREE today; re-check if the agency (L3) hires.

---

## What's NEW for us vs already ours
| Piece | Status in KD brain |
|---|---|
| Claude Code CLI | ✅ Have (the brain IS a Claude Code setup) |
| Remotion editing workflow | ✅ Studied deeply (claude_edit_* series) + hyperframes-editor installed |
| Magic UI / shadcn components | ✅ In client tools plan (`skill-forge\client_tools_plan_2026-06-22.md`) |
| **`npx skills` CLI** | 🆕 One-command skill installer — upgrades skill-forge's install step |
| **remotion-dev/skills bundle** | 🆕 Official skill = Claude natively fluent in Remotion (beats our ad-hoc notes) |
| **UI UX Pro Max skill** | 🆕 Design intelligence on tap for /website, /website-sales, /seedance-site, the Buka, Olly's site |

## His prompting + content lessons for @30Kingdavid (bank these)
1. **Result-first hook (0–3s):** show the finished jaw-dropper + a money number ("$10,000") BEFORE any explanation. Matches our RESULTS-method note.
2. **One-install promise:** each video = ONE tool, ONE command on screen ("npx skills add …"). Simple enough to screenshot. Our videos should show the exact command the same way.
3. **Talking-head + screen sandwich:** face for trust beats, full-screen terminal/result for proof beats, big white+yellow captions (same style we locked for the Faceless Engine).
4. **Edit-instruction prompting:** name the exact moves in one line — "apply cuts, zooms, captions, graphics" — instead of vague "edit this nicely". Adopt in /video-edit prompts.
5. **CTA = "follow @sebintel"** full-screen end card, nothing else. Clean single CTA.
6. **Video ideas we can do our way (AI-tools niche, faceless):** "I built a €X site with one free command" (use our real client demos) · "Claude just learned to edit video — here's the command" · before/after motion-reel reveals of our own brand assets.

## 🆕 Addendum (same day) — Higgsfield CLI (King found it)
**Real + official:** [higgsfield-ai/skills](https://github.com/higgsfield-ai/skills) = 4 Claude Code skills (`/higgsfield:generate`, `soul-id`, `product-photoshoot`, `marketplace-cards`), installable free via `npx skills add higgsfield-ai/skills` or the plugin marketplace; there's also an [official CLI](https://higgsfield.ai/cli) (`npm install -g @higgsfield/cli`) + an MCP. CLI is [reportedly faster/cheaper than MCP](https://techsy.io/en/blog/higgsfield-mcp-claude-code) for agent workflows.
**⚠️ MONEY TRUTH (Rule 12):** the CLI/skills are free, but **generations cost Higgsfield credits** — free tier = small daily credits, watermarked, selected models only; paid from **$15/mo Starter (70 credits)** to $49 Plus / $129 Ultra ([pricing](https://higgsfield.ai/pricing) · [breakdown](https://www.scopeful.org/tools/higgsfield)). NOT free like Remotion/UI UX Pro Max.
**Overlap check:** it drives the SAME models we already pay per-use for via kie.ai + MuAPI (Seedance 2.0, Nano Banana, Kling) — our seedance-site pipeline stays ~$1.33/site. **Unique wins:** Soul ID **consistent character** (relevant to the faceless 2D character brand), cinematic camera-move presets, ready UGC ad pipelines.
**Verdict:** install skills FREE + test on free watermarked daily credits only; **NO subscription unless a specific paid job needs it → `/money` gate.**

## 🆕 Addendum (2026-07-10) — Video 3: "run Claude Code for FREE" (claude-code-router) · fact-checked for King
**Clip:** ~45s TikTok, @sebintel. Transcribed (faster-whisper) + frames read. Claim: "someone built a GitHub repo that lets you run Claude Code for free, 16,000+ stars."
**The tool = [`musistudio/claude-code-router`](https://github.com/musistudio/claude-code-router)** (MIT, open source). His frames show the exact flow: Claude Code → lightweight proxy on `localhost:3000` → model router → DeepSeek / Kimi / Qwen / OpenRouter / local model.

**VERDICT: mostly TRUE, one word oversold.**
- ✅ Mechanism is 100% correct: Claude Code just reads env vars (`ANTHROPIC_BASE_URL` + token), so pointing it at a proxy that speaks the Anthropic Messages API and forwards to another provider genuinely works. Same interface + workflow, different engine. CC can't tell.
- ✅ Star count: he says "over 16,000"; it's now **28,000+** ([repo](https://github.com/musistudio/claude-code-router) · [guide](https://polyskill.ai/blog/claude-code-router)). He undercounted (older clip).
- ⚠️ **"for free" is the clickbait (Rule 12 money truth):** free = the Claude Code CLI itself. The MODELS it routes to are free ONLY if you run a **local model** (your machine, lower quality) or a **free tier** (OpenRouter). DeepSeek/Kimi/Qwen APIs are **cheap, not free**. Accurate framing: "any model, way cheaper," not "free."
- ⚠️ **The catch nobody says:** interface stays, but the BRAIN changes. The whole KD brain runs on Claude Opus 4.8. Swap the engine to DeepSeek/Kimi and every skill still "works" but reasoning, judgment, and King's-voice writing drop a tier. "CC doesn't know the difference" is true; **King would.**
- **Verdict for us:** legit + real, good to KNOW exists (cheap grunt-work on a spare machine), but do NOT point the actual money engine at it. Overlaps our existing cheap-lane / cost-router notes ([[reference-cheap-lane-setup]] · [[reference_muapi_cost_router]]).
**Content angle for @30Kingdavid:** classic sebintel formula again = "one free repo does the impossible" + result/number first. If we ever cover it, we tell the FULL truth (the "for free" caveat) as our differentiator: honesty as the brand.

## Install plan — ✅ EXECUTED 2026-07-04 (King: "I want all cli skills!!") · 28 skills live in `skills/`, registered in `skill-forge/MANIFEST.md` + `_ops/SKILL_TIER_LEDGER.md` (T1)
1. `npx skills add remotion-dev/skills` in the video projects (laptop; also works in Claude Code web sessions per-project).
2. UI UX Pro Max → `uipro init --ai claude --global` on the laptop (lands in `~/.claude/skills/` = the brain, syncs everywhere) OR the /plugin route.
3. Register both in `skill-forge\MANIFEST.md` + tier them in `_ops\SKILL_TIER_LEDGER.md`.
Cost: **€0. All Llama-lane free installs.** Directly serves MONEY MODE: better client sites (Buka/Olly/website-sales) + sharper Faceless Engine videos, no new spend.
