---
description: Trigger the Built With AI autopilot pipeline (research → script → voice → video → captions → publish)
---

# /autopilot · Built With AI Pipeline Trigger

> **PATH CORRECTED 2026-08-21.** This skill pointed at the Documents folder, which does not exist: King's Documents is redirected into OneDrive. The same dead path was silently breaking every video render and the Fiverr publish pack. All paths now point at the real location under OneDrive.


**Triggers:** User types `/autopilot` OR says "run the autopilot", "ship the next video", "trigger the pipeline", "run built with ai"

**Purpose:** Kick off the 6-step pipeline in `C:\Users\Dell\OneDrive\Documents\Built With AI\tools\pipeline_orchestrator.py` (LAPTOP-ONLY: lives outside the synced brain). King David's one command to ship a video. Also fires automatically every Saturday 20:00 Europe/Dublin via Claude Code Routine.

> ⛔ **HITL GATE (Rule 21 + the aide hands-law):** the pipeline may run end-to-end to PRODUCE the video, but **step 6 (Publish) never posts to YouTube / Twitter / Buttondown without King's explicit yes.** The Saturday 20:00 Routine PREPS and queues the video for King's review; he approves before anything goes public. No auto-publish (matches `/website-sales`, `/apply`, `/upwork`, where King does the actual send). If the laptop orchestrator currently auto-publishes, gate step 6 behind a manual confirm.

---

## What this skill does

1. Reads the current 12-video calendar position from `knowledge\built_with_ai_brand.md` to figure out which video is next.
2. Calls `python "C:\Users\Dell\OneDrive\Documents\Built With AI\tools\pipeline_orchestrator.py" --position N --topic "..."` (LAPTOP-ONLY: lives outside the synced brain).
3. Streams the orchestrator output. Each step writes to `outputs\runs\<ts>\` with numbered intermediate files (01_topic_brief.md → 06_publish_receipts.json).
4. On any step failure: orchestrator emails King David automatically + stops at the failed step. Resume command shown in the email.
5. On success: shows the run dir + cost.json total + publish receipts.

## Spec + Architecture

**Read first:** `C:\Users\Dell\.claude\knowledge\autopilot_pipeline_spec.md` (the contract)

6 steps, in order:
1. Topic research (Perplexity + Claude Sonnet 4.6)
2. Script generation (Claude Opus 4.7, beat schema output)
3. Voice (ElevenLabs cloned Irish voice), wired Session 2
4. Video (Remotion + Pexels + ffmpeg), wired Session 2
5. Captions (Whisper + ffmpeg subtitles), wired Session 3
6. Publish (YouTube + Buttondown + Twitter + kie.ai thumbnail), wired Session 3. **HITL: prepared + queued for King's approval, never auto-posted.**

## Usage patterns

*(All commands below are LAPTOP-ONLY: `pipeline_orchestrator.py` lives outside the synced brain, in `Documents\Built With AI\`.)*

| Intent | What to do |
|---|---|
| Run the full pipeline for the next calendar video | `cd "C:\Users\Dell\OneDrive\Documents\Built With AI" && python tools\pipeline_orchestrator.py` (LAPTOP-ONLY) |
| Only run a subset of steps | `python tools\pipeline_orchestrator.py --steps 1,2` (LAPTOP-ONLY) |
| Resume a failed run | `python tools\pipeline_orchestrator.py --resume outputs\runs\2026-05-30_20-00` (LAPTOP-ONLY) |
| Override calendar position + topic for an ad-hoc video | `python tools\pipeline_orchestrator.py --position 5 --topic "Cold email automation that booked 3 clients in a week"` (LAPTOP-ONLY) |

## When stub `NotImplementedError` fires

Until Sessions 2 + 3 wire steps 3-6, the orchestrator stops cleanly when it hits a stub step. That's expected. It's not a failure. Run steps 1-2 today, then pick up at step 3 once ElevenLabs is signed up Wednesday.

## What King David sees

Terminal streams each step's status. End of run prints either:
- `[orchestrator] full pipeline complete for <run_dir>` + cost total
- `[orchestrator] stopping at step N (stub not yet wired)`, early stop, expected during build phase
- `[orchestrator]   FAIL, <err>` + an email lands in iCloud inbox with the traceback + resume command

## Hard rules from the spec

- **No silent failures**, every error goes to `Kingdavidagb@icloud.com` via Gmail OAuth.
- **YouTube AI disclosure**, Step 6 publisher MUST set the "Altered or Synthetic Content" field. Missing = permanent ad-rev ban.
- **Sunday rest**, cron never runs Sunday. Manual `/autopilot` Sunday is technically allowed but discouraged.
- **Idempotent resume**, never re-run a step that already wrote artifacts. State in `00_state.json`.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
