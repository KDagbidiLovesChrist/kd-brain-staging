# Autopilot Research Findings · 2026-05-26
# Filter: published since 2026-03-26 · Claude-focused tutorials prioritized
# Compiled for: BUILT WITH AI faceless YouTube pipeline (Session 1 prep)

## Top Claude-First Sources (last 2 months)

### 1. MindStudio · Claude Code + HyperFrames + ElevenLabs Full Workflow [CLAUDE-FIRST]
- **URL:** https://www.mindstudio.ai/blog/generate-ai-videos-claude-code-hyperframes-elevenlabs-workflow
- **Date:** 2026-05-18 (8 days ago)
- **Summary:** Modular 4-stage Python pipeline: script → ElevenLabs TTS → HyperFrames animation → FFmpeg merge. Claude Code = brain (writes script, segments narration, generates animation prompts, calls all APIs).
- **KEY TAKEAWAY:** **5, 12 minutes per 60-sec video, total API cost under $1.** Numbered intermediate files (audio_1.mp3, visual_1.mp4) is the cleanest pattern. Direct match for BUILT WITH AI architecture.

### 2. Tim McAllister · "Added AI Video Production to Claude Code in One Afternoon" [CLAUDE-FIRST]
- **URL:** https://medium.com/@emergentcap/how-i-added-ai-video-production-to-claude-code-in-one-afternoon-9edcb68853aa
- **Date:** 2026-03-28 (just inside window)
- **Summary:** Claude Code + Remotion (React video renderer) + ElevenLabs. "Beat" system, JSON-driven narrative segments (hook, problem, stat, insight, solution, CTA) auto-redistribute timing based on actual voiceover duration.
- **KEY TAKEAWAY:** 10, 15 min concept-to-published, security-hardened (Keychain creds, ClamAV scan on installs). The **beat schema** is the single best pattern for BUILT WITH AI, maps perfectly to "Real builds. Real euros. Real flops." tagline.

### 3. Blotato · Make AI Videos with Claude Code (Remotion Skill) [CLAUDE-FIRST]
- **URL:** https://www.blotato.com/blog/make-ai-videos-with-claude-code
- **Date:** 2026-05-22 (4 days ago)
- **Summary:** Claude Code skill loads Remotion, runs research, produces storyboard for approval, then renders. 5 video types demonstrated (animated explainer, product launch, testimonials, avatar+captions+broll, infographic).
- **KEY TAKEAWAY:** **$20/mo Claude Pro = unlimited videos** (Remotion is free, no per-video fees). Cheapest viable Claude-first stack. Caveat: avatar generation requires HeyGen handoff; parallel rendering still flaky.

### 4. MindStudio · Automate Video Editing End-to-End with Claude Code [CLAUDE-FIRST]
- **URL:** https://www.mindstudio.ai/blog/automate-video-editing-claude-code
- **Date:** 2026-04-25
- **Summary:** 5-skill chain (ingestion → trim → graphics → render → orchestrate). Each skill reads/writes a shared manifest.json. Tools: VideoUse (trimming/scene detect), Hyperframes (motion graphics), FFmpeg.
- **KEY TAKEAWAY:** **Cost per 30-min video = $1.50, $3.60.** The manifest.json pattern is critical, single source of truth across skills prevents state drift.

### 5. UhiyamaLab · Multilingual YouTube Dubbing (Claude + ElevenLabs + Python) [CLAUDE-FIRST]
- **URL:** https://uhiyama-lab.com/en/blog/video-edit/elevenlabs-youtube-dubbing-workflow/
- **Date:** 2026-03-29
- **Summary:** 7-step pipeline, transcription → text refine → translation → TTS → timeline → mastering → upload. Claude does semantic translation/refinement; Python+ffmpeg does mechanical processing. SHA1 cache invalidation to avoid wasted API credits during testing.
- **KEY TAKEAWAY:** Critical gotcha, **YouTube rejects dubbed audio that does not match original video length exactly.** Use absolute timestamp placement, never concatenation. Also: `ffmpeg amix` defaults silence output; specify `normalize=0`.

### 6. MindStudio · Content Repurposing with Claude Code Skills [CLAUDE-FIRST]
- **URL:** https://www.mindstudio.ai/blog/automate-content-repurposing-claude-code-skills
- **Date:** 2026-04-16
- **Summary:** One Claude Code skill turns a YouTube transcript → LinkedIn post + X thread + newsletter. Modular file pattern: skill.md (steps), brand-voice.md (tone), platform-formats.md (rules), examples/ folder.
- **KEY TAKEAWAY:** Separating PROCESS (skill.md) from CONTEXT (brand-voice.md) is the consistency unlock. **Perfect template for BUILT WITH AI cross-posting (YouTube → Buttondown newsletter → Twitter thread).**

### 7. vfarcic/youtube-automation (GitHub) [CLAUDE-PARTIAL]
- **URL:** https://github.com/vfarcic/youtube-automation
- **Date:** Active 2026 (CLAUDE.md present, exact commit date not visible)
- **Summary:** Production-grade Go service with React UI. 6-phase lifecycle (Ideas → Started → Material Done → Edit Requested → Publish Pending → Published). Uses Azure OpenAI (not Claude) for content gen, but the CLAUDE.md guidance file is rich.
- **KEY TAKEAWAY:** **6-phase lifecycle + reflection-based field completion** is the model for production-grade pipelines. Has built-in thumbnail prompt injection defense (sanitize Unicode control chars + role-tag prefixes). Borrow the phase model, not the AI layer.

---

## Secondary Sources (other AI tools, last 2 months)

### 8. Autoadify · Faceless YouTube AI Automation Stack 2026 [CLAUDE-PARTIAL]
- **URL:** https://autoadify.com/blog/faceless-youtube-ai-automation-channel-2026
- **Date:** 2026-05-20
- **Summary:** 6-layer stack: Claude Opus 4.6 or GPT-5 script ($0.30, 0.80/vid), ElevenLabs v3 ($22, 99/mo), Kling 3.0 + Nano Banana 2 visuals ($0.80, 1.50/vid), Descript/CapCut Pro ($9.99, 24/mo), Nano Banana 2 thumbnails ($0.05, 0.15/vid).
- **KEY TAKEAWAY:** Total monthly economics = **$120, $190/mo for 12 videos**, ~2.5 hrs/video. Confirms King David's €130, 170/mo Phase 2 budget is realistic, not optimistic.

### 9. dev.to · wedgemethoddev "Faceless Channel That Runs Without Me" [CLAUDE-FIRST]
- **URL:** https://dev.to/wedgemethoddev/how-i-automated-a-faceless-youtube-channel-that-runs-without-me-code-architecture-1fn8
- **Date:** 2024-04-03 (edited 2024-04-07), **OUTSIDE WINDOW, included only for code reference; treat as architectural inspiration not current truth**
- **WARNING:** Predates 2026 tooling. Useful only because it uses Claude Sonnet 4.6 + ElevenLabs + Pexels + ffmpeg + Whisper end-to-end at $0.55/video. Architecture still valid; pricing/model names outdated.

### 10. emergingai.substack · Claude + YouTube = Dollar$ [CLAUDE-PARTIAL]
- **URL:** https://emergingai.substack.com/p/claude-youtube-dollar-video-automation
- **Date:** 2026-05-11
- **Summary:** Linear pipeline (concept → script → voiceover → visuals → long-form → Shorts → TikTok → Telegram → analytics). Claude = "heavy thinking", GPT-5.5 = research/QC.
- **KEY TAKEAWAY:** Warns: **"Most faceless AI channels die before they hit 50 videos."** Process discipline > tool stack. Reinforces King David's roadmap of consistent shipping over chasing tools.

### 11. mejba.me · Claude Code + Remotion Motion Graphics [CLAUDE-FIRST · content blocked]
- **URL:** https://www.mejba.me/blog/claude-code-remotion-youtube-motion-graphics
- **Date:** Unverified (returned HTTP 403)
- **STATUS:** EXCLUDED per protocol, could not confirm publish date.

---

## Recent Architecture Consensus (2026)

What every recent Claude-first builder is doing right now (drawn from sources 1, 6):

1. **Claude Code orchestrator + Python glue + external API workers.** Nobody runs n8n or Make for serious autopilot, too slow, too brittle, too expensive. Pure Python scripts called from a Claude Code skill is the winning pattern.

2. **JSON-as-shared-state.** Every pipeline uses either a manifest.json (MindStudio) or beat-props JSON (Tim McAllister) as the single source of truth between stages. Stages read/write the same file; no message queues.

3. **Numbered intermediate files.** audio_1.mp3, visual_1.mp4, segment_1.json. Predictable naming = easy debugging + resumability.

4. **Skill-based modularity.** Process logic in skill.md, context (brand voice, platform rules) in separate .md files. Examples folder for format anchors. This is the AIS-style WAT pattern, King David already lives here.

5. **Claude Pro $20/mo + open-source rendering (Remotion).** Cheapest viable autopilot stack. Pay-per-API only for voice (ElevenLabs) + optional avatar (HeyGen).

6. **5, 15 minutes per video, $0.55, $3.60 per video API cost.** Range depends on length and whether avatars are involved.

---

## Claude-Specific Patterns

How Claude is being used in 2026 YouTube automation:

| Role | What Claude does | Confidence |
|------|-----------------|------------|
| **Research** | Topic ideation, niche viability scoring, competitor research via WebSearch | HIGH · every Claude-first source |
| **Script writer** | Long-form narration broken into timed beats/segments with B-roll markers | HIGH · universal pattern |
| **Orchestrator** | Calls ElevenLabs, HeyGen, FFmpeg APIs; manages manifest.json state | HIGH · defining feature of Claude Code over GPT |
| **Prompt generator** | Writes prompts for animation tools (HyperFrames, Kling, Remotion components) | HIGH |
| **Cross-poster** | Reformats one script into LinkedIn/X/newsletter via skill files | HIGH · MindStudio pattern |
| **Quality control** | Pre-publish review of generated assets, retention prediction | MEDIUM · emerging |
| **Avatar generation** | NOT a Claude strength · hand off to HeyGen ($1-5/min API) | N/A |
| **Voice synthesis** | NOT a Claude strength · hand off to ElevenLabs | N/A |
| **Video rendering** | NOT a Claude strength · hand off to Remotion (free) or HyperFrames (paid) | N/A |

**Typical Claude-orchestrated pipeline setup time:** "One afternoon" (Tim McAllister) to a few days. King David's 4-session plan (~10 days) is realistic for production-grade.

**Cost per video at scale (Claude-first):** $0.55, $3.60 API + amortized $20/mo Claude Pro.

---

## Tool-by-Tool 2026 Status

| Tool | Tier needed | Cost | Confirmed working in last 60 days? |
|------|------------|------|-----------------------------------|
| **Claude API / Claude Code** | Pro $20/mo OR API pay-per-use | $20/mo unlimited videos via Code | YES · multiple May 2026 tutorials |
| **YouTube Data API v3** | Free tier (10,000 units/day) | FREE | YES · **MAJOR WIN: video uploads dropped from ~1,600 to ~100 units/call on 2025-12-04 → 100 uploads/day on free tier** |
| **ElevenLabs API** | Starter $5/mo (30k credits) OR Creator $22 OR Pro $99 | $5-99/mo | YES · Python SDK active; Irish accent supported via Eleven v3 audio tags |
| **HeyGen API** | Pay-as-you-go (no free tier since Feb 2026) | $1.00/min Avatar III 1080p → $5.00/min Avatar IV 4K | YES · but **free API tier DEAD; old $99 Pro/$330 Scale plans grandfathered only** |
| **Submagic API** | Business plan required | $41/mo + $0.69/min processed video | YES · launched Jul 2025; webhook callback model; n8n/Make/Zapier integrations |
| **Buttondown API** | Any paid plan | Token-auth REST at `api.buttondown.com/v1/emails` | YES · fully working, custom templates added Feb 2026 |
| **Twitter/X API** | **NO free tier for new devs since Feb 2026** | Pay-per-use: $0.01/post created, $0.005/post read (cap 2M reads/mo) | YES but EXPENSIVE · legacy Basic ($200/mo) and Pro ($5k/mo) grandfathered only |
| **Remotion** | Open source | FREE | YES · primary rendering layer for Claude Code in 2026 |
| **HyperFrames** | API subscription | Per-render fees | YES |
| **VideoUse** | API | $0.50· $1.20 per 30-min video | YES |
| **FFmpeg** | System install | FREE | YES · already installed via winget on King David's laptop (2026-05-23) |

---

## Critical Gotchas (recent · last 60 days)

1. **YouTube July 2025 "inauthentic content" enforcement is real and ongoing.** Mass-produced template videos are de-monetized. BUILT WITH AI must show "human involvement", King David's real voice, real Stripe screenshots, real Irish accent satisfies this. Don't drift to fully synthetic avatars without disclosure.

2. **YouTube "Altered or Synthetic Content" checkbox is permanent ad-rev ban if missed.** Required for any AI avatar/AI-voice video depicting real events/people. Already noted in CLAUDE.md but bears repeating, Claude Code must tick this in the API upload payload, not skip it.

3. **HeyGen killed the free API tier in Feb 2026.** Pay-as-you-go from $1/min. Old $99 Pro / $330 Scale tiers ONLY for existing subscribers with uninterrupted payment. **King David cannot get on the old plans now.**

4. **Twitter/X API has no free tier for new developers since Feb 2026.** Pay-per-use only, $0.01/post created. For BUILT WITH AI cross-posting, budget ~$0.05/video for one tweet+thread. Cheap but adds up.

5. **Remotion versions 4.0.439, 4.0.441 have a critical loader-utils prototype pollution vulnerability.** Pin to 4.0.442+ or earlier than 4.0.439. Also: `@remotion/mcp` package makes unauthenticated external calls, exclude it.

6. **Claude Agent SDK billing changes 2026-06-15.** Starting that date, Claude Agent SDK and `claude-p` usage on subscription plans draws from a new monthly Agent SDK credit, SEPARATE from interactive limits. **Action: review autopilot cost model after 2026-06-15.**

7. **HeyGen API is fully separate billing from web plans.** Buying Creator/Pro/Business does NOT give API access. King David must top up the API wallet separately ($5 minimum).

8. **YouTube dubbed audio must match original video length EXACTLY.** Use absolute timestamp placement, not concatenation. Affects any multilingual expansion of BUILT WITH AI down the line.

9. **`ffmpeg amix` filter silences output with many cues at default normalization.** Always specify `normalize=0`.

10. **Submagic API needs Business plan ($41/mo), no cheap entry.** If captions budget is tight, do captions via Whisper + FFmpeg subtitle overlay (free) until volume justifies Submagic.

---

## Open Questions for Session 1

1. **Voice path, Irish accent: real King David voice (iPhone Voice Memos + ElevenLabs Professional Voice Clone) vs Eleven v3 Irish accent tag from text?** Real voice = highest authenticity but adds friction. Eleven v3 = full autopilot but synthetic. **Recommendation: start real voice for Videos 1, 5 to build channel authenticity, then test cloned voice for Video 6+ once subscriber trust is established.**

2. **Render layer, Remotion (free, React, code-based) vs HyperFrames (paid, API)?** Remotion = $0 ongoing, full control, steeper setup. HyperFrames = faster setup, per-render cost. **Recommendation: Remotion. Aligns with Claude Pro $20/mo budget and BUILT WITH AI faceless style (text + screenshots + Stripe receipts, not avatars).**

3. **Avatar layer, needed at all?** BUILT WITH AI niche = case studies with real screenshots. No avatar needed. **Recommendation: skip HeyGen entirely for Phase 1. Save $30, 150/mo.**

4. **Cross-post stack, Buttondown ($9, 29/mo) confirmed for newsletter. Twitter pay-per-use $0.01/post confirmed.** OK to proceed; budget ~$5/mo for Twitter at 12 videos/mo × 5 tweets/video.

5. **Cron, Claude Code Routines (free, built-in) vs trigger.dev (free tier, more observable)?** King David's CLAUDE.md already locked Routines for personal use. **Confirmed: Routines for BUILT WITH AI autopilot.**

6. **Captions, Whisper free vs Submagic $41/mo?** Whisper handles transcription; FFmpeg `subtitles` filter burns them in. No need for Submagic until brand voice/aesthetic upgrade. **Recommendation: Whisper + FFmpeg for Phase 1. Submagic only after first €500 month.**

7. **Phase 1 MVP target stack confirmed:** Claude Code Pro ($20) + ElevenLabs Starter ($5) + Remotion (free) + Whisper (free) + FFmpeg (free) + YouTube API (free) + Buttondown ($9) + Twitter pay-per-use (~$5/mo) = **~$39/mo all-in.** Well under the €30, 50 Phase 1 budget.

---

## Sources

- [MindStudio · Claude Code + HyperFrames + ElevenLabs Full Workflow](https://www.mindstudio.ai/blog/generate-ai-videos-claude-code-hyperframes-elevenlabs-workflow) · 2026-05-18
- [Tim McAllister · Added AI Video Production to Claude Code in One Afternoon](https://medium.com/@emergentcap/how-i-added-ai-video-production-to-claude-code-in-one-afternoon-9edcb68853aa) · 2026-03-28
- [Blotato · Make AI Videos with Claude Code](https://www.blotato.com/blog/make-ai-videos-with-claude-code) · 2026-05-22
- [MindStudio · Automate Video Editing End-to-End with Claude Code](https://www.mindstudio.ai/blog/automate-video-editing-claude-code) · 2026-04-25
- [UhiyamaLab · Multilingual YouTube Dubbing](https://uhiyama-lab.com/en/blog/video-edit/elevenlabs-youtube-dubbing-workflow/) · 2026-03-29
- [MindStudio · Content Repurposing with Claude Code Skills](https://www.mindstudio.ai/blog/automate-content-repurposing-claude-code-skills) · 2026-04-16
- [vfarcic/youtube-automation (GitHub)](https://github.com/vfarcic/youtube-automation) · Active 2026
- [Autoadify · Faceless YouTube AI Automation Stack 2026](https://autoadify.com/blog/faceless-youtube-ai-automation-channel-2026) · 2026-05-20
- [emergingai.substack · Claude + YouTube = Dollar$](https://emergingai.substack.com/p/claude-youtube-dollar-video-automation) · 2026-05-11
- [YouTube Data API v3 · Quota changes](https://developers.google.com/youtube/v3/guides/quota_and_compliance_audits) · current
- [HeyGen API Pricing 2026](https://help.heygen.com/en/articles/10060327-heygen-api-pricing-explained) · current
- [Submagic API docs](https://docs.submagic.co/introduction) · current
- [Buttondown API docs](https://docs.buttondown.com/api-subscribers-send-email) · current
- [X (Twitter) API Pricing 2026](https://www.xpoz.ai/blog/guides/understanding-twitter-api-pricing-tiers-and-alternatives/) · Feb 2026
- [ElevenLabs Irish accent + Eleven v3 audio tags](https://elevenlabs.io/blog/eleven-v3-audio-tags-emulating-accents-with-precision) · current
- [Claude Agent SDK overview](https://code.claude.com/docs/en/agent-sdk/overview) · current
- [Claude Agent SDK June 15 billing change](https://support.claude.com/en/articles/15036540-use-the-claude-agent-sdk-with-your-claude-plan) · Jun 2026
