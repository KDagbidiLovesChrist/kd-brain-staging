# /watch · Deep Video Analysis Skill

**Trigger:** King sends a video (file OR YouTube/TikTok/link) OR says "watch this", "analyse this video",
"break this down", "/watch". Whenever King shares a video, RUN THIS, don't just react to the title.
**Purpose:** Turn any video into ONE objective, trustworthy lesson by **watching it deeply AND
cross-checking online summaries**, then save the lesson to the brain so it compounds (Rule #15).

**Standing rule King set (2026-06-17):** "Anytime I send a video I need a deep analysis from watching it
AND seeing summaries online, all together, coming to an objective lesson." So every video = watch + research
+ synthesize + save. Never give a summary-only take and call it "watched."

---

## STEP 1 · WATCH IT (primary source)
Run the Gemini watcher on the actual video:
- Link: `python tools/watch_video.py --url "<youtube/tiktok/url>"`
- Uploaded file: `python tools/watch_video.py --file "<path in /root/.claude/uploads/...>"`
- For a specific lens, reuse a focused watcher in `tools/` (`gemini_watch_motion/ui/editstyle/workflow.py`).

**Requires `GEMINI_API_KEY`** (env secret, or `.env.master`). If it's missing, STOP and tell King the
watch step can't run without the key, then do Steps 2, 4 on summaries only and label it clearly as
"NOT watched, summaries only."

## STEP 2 · RESEARCH IT (secondary sources)
`WebSearch` the title + creator + topic. Pull: what others say it teaches, takeaways, criticisms, and
any official repo/docs/links shown. Goal = a second, independent read on the same content.

## STEP 3 · SYNTHESISE → THE OBJECTIVE LESSON
Combine Step 1 (what it actually says) + Step 2 (the outside read). Deliver to King, plain English:
- **The lesson in one line.**
- **What's genuinely useful** (substantiated) vs **what's hype** (be honest).
- **What it means for KD specifically**, money goal, current projects, existing skills (does it confirm,
  upgrade, or conflict with Nate's WAT / his setup?).
- **What to DO about it**, concrete next action(s), or "nothing, here's why."
- Flag anything that would change the foundation → that's a STOP-AND-TALK (Skill Forge guardrail).

## STEP 4 · SAVE IT (write-back, Rule #15)
- Write the lesson to `knowledge/video_studies/<date>_<slug>.md` (title, source URL, the objective lesson,
  the "what to do").
- If it changes how we work or build → also update the relevant `memory/` file and/or master `CLAUDE.md`.
- If it's a skill/tool to acquire → log it in `skill-forge/MANIFEST.md`.

## OUTPUT
A short, honest briefing to King (the objective lesson + what to do) + the saved `knowledge/` note.

## DONE WHEN
- [ ] The video was actually WATCHED (or clearly labelled summaries-only if no key)
- [ ] Watch + online research were combined into ONE objective lesson
- [ ] The lesson is saved to the brain so the next session inherits it
