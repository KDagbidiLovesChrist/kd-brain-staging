---
name: video
description: One front door for ALL video work, make ANY video from scratch OR edit existing footage, as a paid service. Reads the request, routes to the right engine (HyperFrames make-a-video to create · /video-edit to edit · /website-to-hyperframes for URLs · /short-form-video for 9:16 social), runs it, QAs by frames, and delivers. Triggers on "make a video", "make me a video", "create a video", "edit this video/clip", "cut this into a reel/short", "video from my site".
---

# /video · King's Video Service (make ANY video · edit ANY video · for pay)

**Triggers:** `/video`, "make a video", "make me a video", "create a video", "new video", "edit this video", "edit this clip", "cut this into a reel/short", "turn my site into a video", "video ad", "promo video".

**Purpose:** The single, sellable front door for **all** video work. King (or a paying client) describes what they need; this skill figures out whether it's a *create-from-scratch* job or an *edit-existing-footage* job, **routes to the engine that already exists** (it does NOT rebuild any engine), drives it end-to-end, QAs by still frames, and delivers. The offer: **"One person + AI. I make or edit any video you need."**

> **READ FIRST:** master `C:\Users\Dell\.claude\CLAUDE.md`. Video quality bar: `memory\feedback_video_quality_bar.md`. Hard-won build gotchas: `memory\reference_kd_launch_video.md`. "Edited ≠ slow scroll": `memory\feedback_edited_not_scroll.md`.

---

## Step 1 · Route the job (the heart of this skill)

Read the request and pick the engine. **If it's not obvious, ask ONE question: "Is this a brand-new video, or editing footage you already have?"** Then route:

| The request is… | Route to (invoke) | Lives at |
|---|---|---|
| A **new video from a concept / script / idea / brand** (no source footage) | the HyperFrames **`make-a-video`** skill | `.claude\skills\make-a-video\SKILL.md` |
| **Edit / cut existing footage**, "make a reel from this clip", client raw files, tighten a talking-head | **`/video-edit`** (gig 10, Remotion style library) | `Documents\Website Builder\video-edit\` |
| A **URL / existing website → video** | **`/website-to-hyperframes`** (fallback: `/video-to-website`) | `.claude\skills\website-to-hyperframes\SKILL.md` |
| A **9:16 talking-head / short social hook** | **`/short-form-video`** | `.claude\skills\short-form-video\SKILL.md` |
| A **cinematic scroll-scrub "3D" website video** | **`/seedance-site`** path / Seedance method | `memory\skill_seedance_animated_websites.md` |
| Unsure | ask the one question above, then route |

**Routing rules**
- One job can chain engines (e.g. create a new ad with `make-a-video`, then route the finished file through `/short-form-video` for a social cut). Note the chain up front.
- Don't reinvent, the chosen engine owns the actual build, its gates, and its rules. This skill owns **routing + intake + pricing + delivery + QA discipline**.
- Reuse King's existing assets where relevant: `video-projects\kd-launch\` (demo clips, Hale VO `george-vo.mp3`, `brand-tokens.css`, fonts), `Built With AI\remotion\styles\*` (edit styles).

---

## Step 2 · Intake (for any paid/client job, capture before building)
1. **Goal**, what's the video for? (ad / promo / launch / product demo / tutorial / social post / client deliverable)
2. **Audience** + where it'll play (TikTok/Reels/IG · YouTube · website · email).
3. **Type → engine** (use the router) and **aspect** (9:16 1080×1920-16:9 1920×1080-1:1) + **target length**.
4. **Brand**, colours, logo, brand name, tagline, CTA. (King's OWN videos = black+gold personal brand; CLIENT videos = the client's brand, never King's, see `memory\feedback_palette_personal_only.md`.)
5. **Source**, footage files (into the engine's `raw/`) · "use stock B-roll" (Pexels, free) · from-scratch · a URL to capture.
6. **Voice**, client's own recording · ElevenLabs narrator · music-only. (Hale TTS id `dXtC3XhB9GtPusIpNtQx`; key is TTS-scoped.)
7. **Captions**, provided text · auto-from-audio (whisper) · off.
8. **Music**, vibe; **cleared tracks only**.
9. **Deadline + tier.**

---

## Step 3 · Pricing (PLACEHOLDER · set exact prices at the first paying client)
Sell the service; lock the number when a real buyer appears. Starting ladder (reference = video-edit's existing tiers):

| Tier | Rough scope | Price |
|---|---|---|
| Short social | 10-25s vertical, 1 style, captions | **TBD** (ref ~$89) |
| Standard promo | 30-60s, brand applied, VO + music | **TBD** (ref ~$229) |
| Premium ad | flagship cut, multi-agent polish, 4K | **TBD** |
| Custom / long-form | explainer, documentary, retainer | **TBD / quote** |

> Mark every quote "indicative, confirmed on brief." Don't undercut the quality on offer; quote the **human motion-designer upgrade** (cinema-10) separately, funded by client money.

---

## Step 4 · Build → QA → deliver
- **Build:** hand off to the routed engine and honour ITS gates (HyperFrames make-a-video has 2 mandatory preview gates; `/video-edit` authors a `job.json` + runs `video_edit.py`).
- **Cost-aware AI generation:** whenever a job needs AI images or AI video clips (Seedance/Kling/Veo/Flux/Nano Banana), generate through the **cost router** `C:\Users\Dell\.claude\tools\gen_router.py`, it quotes MuAPI (live) vs kie.ai and runs the cheapest for the chosen quality tier (`quote` first = free). MuAPI key in `.env.master`; top-ups via `/money`. (See `/seedance-site` "Cost-aware generation".)
- **QA (always, I cannot watch video play):** extract frames at every beat + transition with ffmpeg and **`Read` each PNG**. Lint must be 0 errors. Confirm: footage full-frame + bright + legible, scroll smooth (true 30fps, no frame-dup), audio clean (waveform), captions land, correct CTA/socials, no pricing in King's own ads. **King watches the final once before it ships.**
- **Deliver:**
  - **Client job →** the client's files + a portfolio entry (frame it Mubashir-style: "client wanted X; we handled script → delivery").
  - **King's own →** email all 3 inboxes (reuse `C:\Users\Dell\.claude\tools\send_launch_video.py` pattern), publish on **kd-review.vercel.app** (`Documents\Website Builder\kd-review\` → new card + `vercel --prod --yes`, verify 200), copy to Desktop (1080 + 4K via `scale=2160:3840:flags=lanczos`).

---

## Research-backed production stack + technique checklist (multi-source consensus, 2026-05-26)

Pulled from `knowledge\autopilot_research_findings.md` (11 Claude-first 2026 tutorials, cross-checked) plus the production-technique half of `knowledge\production_stack_research.md`. Cost-tier pricing tables (what to charge, subscription ladders) stay owned by `/money`'s cost router, this section is HOW to build it well, not what to charge for it.

**The stack every 2026 Claude-first builder converges on independently (this is real consensus, not one source):**
1. **Claude Code = the orchestrator.** It writes the script, breaks it into timed beats, calls every other tool (voice, render, captions), and manages state through a shared JSON file. Every source agrees, nobody runs n8n or Make for this, too slow and too brittle for real video pipelines.
2. **Remotion (free, open-source, React-based)** = the default render layer, already wired into King's engines (`make-a-video`, `/video-edit`). **HyperFrames** (HTML-native, per-render cost) is the fallback when speed-to-first-render matters more than the fee, also already wired in.
3. **ElevenLabs** = voice. Starter tier covers Phase 1 volume, but the free tier has **no commercial rights** (attribution required), swap to CapCut's free built-in TTS for anything that will actually publish/monetize until ElevenLabs is upgraded.
4. **Whisper (free, local) + FFmpeg (free)** = transcription, captions, and the mechanical cut/merge/subtitle-burn layer. No cloud upload needed, runs on King's own machine.
5. **Pexels (free, commercial-cleared, no attribution)** = default b-roll source. Cannot resell the clips as-is, but fine for finished videos.
6. **A single shared state file** (`manifest.json` or `job.json` / `props.resolved.json`, numbered intermediate files like `audio_1.mp3`, `visual_1.mp4`) between every pipeline stage. This is exactly what King's `/video-edit` orchestrator already does, keep that pattern, don't drift to ad hoc file names.

**The honest cost reality (state it plainly, don't oversell it to a client):** the tightest Claude-first pipeline in the research (MindStudio's HyperFrames + ElevenLabs workflow) reports **under $1 (about EUR 1) in API cost for a 60-second video**, 5 to 12 minutes of build time. Across all sources the range is **$0.55 to $3.60 per video** in raw API cost, depending on length and whether an AI avatar is involved (avatars push cost up a lot, King's faceless style with real screenshots and his own voice skips that cost entirely). This is production API cost only, it is separate from any Claude subscription and completely separate from what King charges a client, that ladder lives in this file's "Step 3 Pricing" above and in `/money`'s cost router.

**Gotchas worth remembering (pulled straight from the research, not guesses):**
- YouTube's "Altered or Synthetic Content" checkbox is mandatory for AI-voice/AI-avatar video depicting real people or events, a missed tick is a permanent ad-revenue ban (already in this file's Faith filter section, repeated here because it is the single most-cited gotcha across sources).
- `ffmpeg amix` silences the output by default when mixing multiple audio cues unless `normalize=0` is set explicitly.
- Dubbed or replaced audio must match the original video length exactly, use absolute timestamp placement, never simple concatenation, or platforms reject the upload.
- Remotion versions 4.0.439 and 4.0.441 carry a known loader-utils vulnerability, pin to 4.0.442 or newer, or stay below 4.0.439. Skip the `@remotion/mcp` package (it makes unauthenticated external calls).

**Technique library:** the full 66-file library of motion, editing, UI, and workflow studies now has a map at `knowledge\video_studies\INDEX.md`, grouped by theme (hooks, motion graphics, UI/UX, website scroll-scrub, AI build workflows, AI edit workflows, ad-style references, viral editing techniques, faceless-channel pipelines). Check the INDEX before building anything visual, most styles King will be asked for already have a matching study, don't guess a look from scratch when a real reference exists.

---

## CapCut finishing lane (LAPTOP · manual polish, NOT a build engine)
Nate Herk's pattern (nateherkai TikTok, frames watched 2026-07-04): **Claude Code creates** the video/animation/motion graphics from a prompt; **CapCut does the finishing pass**, auto captions, local captions, text templates. CapCut never replaces the build engines above, it's an optional last-mile polish.

**Route a finished cut through CapCut when…** | **Keep the ffmpeg/Remotion pipeline when…**
---|---
One-off cut that needs King's caption style fast (white + **YELLOW pop**) via auto captions | Batch / programmatic jobs (faceless engine, client pipelines that must be reproducible)
Text templates / stickers / trending caption looks | Captions burned by script (edit engine word-pop, whisper → Remotion)
Quick mobile/phone edit, King polishing by hand | Anything run from the cloud door (CapCut can't be reached from cloud)

**Hard facts (verified 2026-07-04, lean-spend friendly):**
- **Free desktop tier:** 1080p export · **auto captions FREE but capped ~10 min per video** · watermark ONLY if crown (Pro) templates/effects are used, own footage exports clean. Paid: Standard $9.99 (watermark-free templates) · Pro $19.99 (4K/60fps, unlimited captions, full AI toolkit). Free tier covers our shorts.
- **NO official public API** (confirmed 2026; CapCut's open platform = editor plugins only). Third-party open-source draft-file tools exist (VectCutAPI / CapCutAPI + a capcut-ai-editor MCP on GitHub) but they run **locally against CapCut project files**. So: **CapCut = a LAPTOP/manual step. Never plan it into a cloud-session pipeline.**
- Sources: capcutguide.com + eesel.ai + flowith.io pricing breakdowns (2026) · samautomation.work/capcut-api · github.com/sun-guannan/VectCutAPI.

## Honest ceiling (state it, don't oversell)
Code (HyperFrames/Remotion + ffmpeg) tops at a strong **8** (sleek/minimal ~8.5). True cinema-**10** (hand-crafted motion graphics) needs a **human motion designer**, funded by client money later. I **cannot watch video play**, QA is always **still frames** + King watches the final once before delivery.

## Faith filter + hard rules
- **Cleared music only** (YouTube Audio Library / Uppbeat / Epidemic / client-supplied). Never ship unlicensed audio.
- **No fabricated client results.** Honest claims only.
- **YouTube AI disclosure:** tick "Altered or Synthetic Content" for AI-generated or altered realistic voice/scenes. **When in doubt, disclose** - YouTube's 2026 policy has no clear own-voice-clone exception, and an undisclosed AI voice risks Partner Program eligibility. ⚠️ King to verify the current YouTube rule for a licensed clone of his OWN voice narrating his OWN words; until confirmed, default to disclosing (matches `/content-engine`).
- **King's own ads:** no pricing in-video; domain shown (not spoken) only at the end; no em-dashes in copy; footage is the hero (big/bright/legible); keep the breathing pauses; offer a multi-agent "make it much better" consensus pass with my consent before sending (`memory\feedback_video_quality_bar.md`).
- **Off-limits content:** gambling, alcohol, adult, deception (`memory\feedback_faith_values_filter.md`).

## Architecture (WAT)
- **W:** this SOP (route → intake → build → QA → deliver).
- **A:** Claude, reads the request, routes, drives the chosen engine, runs frame QA.
- **T:** HyperFrames (`make-a-video`, `/hyperframes`, `npx hyperframes` CLI) · Remotion video-edit (`video_edit.py` + `Built With AI\remotion\styles\*.jsx`) · ffmpeg · ElevenLabs · faster-whisper · Pexels · Vercel.
- **S:** `/video` (one front door for create + edit).
- **Money:** paid video service, make OR edit any video. Tiers TBD per first client.

## Related skills (the engines this routes to)
- `make-a-video`, create from scratch (HyperFrames, 8 gates)
- `/video-edit`, edit existing footage (gig 10)
- `/short-form-video`, 9:16 talking-head / social hook
- `/website-to-hyperframes` · `/video-to-website`, URL/site → video
- `/seedance-site`, cinematic scroll-scrub "3D" website video
- `/hyperframes` · `/hyperframes-cli` · `/gsap`, framework rules + CLI + animation reference

> 🎬 **Remotion lane:** the `remotion-best-practices` skill (installed 2026-07-04) is live — for programmatic/React-based renders and caption engines, consult it BEFORE hand-writing ffmpeg filters. Routes: batch/programmatic → Remotion or ffmpeg; one-off polish → CapCut lane above.

> 📦 **Delivery + versioning law (drift fixes, 2026-07-04):** final encodes ship as libx264 + yuv420p pixel format (platform compatibility). Revisions DUPLICATE the scene/asset as _v2, never overwrite (scene versioning rule).
