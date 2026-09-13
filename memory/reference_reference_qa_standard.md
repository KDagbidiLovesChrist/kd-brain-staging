---
name: reference-reference-qa-standard
description: "MANDATORY REFERENCE-QA standard: whenever an output is modeled on a reference/competitor/data (almost always), QA is a MEASURED similarity check against the reference's real numbers (voice wps, cut length, caption + visual format, energy, hook), dimension by dimension, not an internal 'does it render' check. Baked into /content-engine + /find-skills."
metadata:
  node_type: memory
  type: reference
  originSessionId: 377b479b-4ca1-4b54-a7d6-e4d24f3654c3
---

# REFERENCE-QA Standard (match the data, MANDATORY)

**Standing rule (King, his words):** "you need to QA against the results/inspiration we are using to
make sure we match our competitors and data... the similarities are in check for best quality results.
not just for voicing, for the majority of QAs we do, because we get our inspo from data and work from
there."

## The principle
We get our inspiration from data and model the proven winner (Rule #16 + #17). So whenever our output
is built off a reference, a competitor, or data (which is almost always), QA is **NOT** an internal
check ("does it render, no console errors, no overflow"). QA must be a **MEASURED SIMILARITY CHECK
against the actual reference:** pull the reference's real numbers and compare ours to them, dimension by
dimension, then fix until ours matches. **This SUPERSEDES internal-only QA whenever a reference exists,**
and it applies to the **majority of QAs we do**, not just voicing. Internal-only QA is the exact failure
mode that let a slideshow-quality video ship when the references are far tighter. The bar: ours is "not
unlike theirs."

## The method (5 steps)
1. **Pull the real reference(s)** we are modeling. Download the competitor video/asset, do not guess.
   All free, no paid API:
   - **yt-dlp** to download the reference video.
   - **ffmpeg** scene-detect for cut-counting: `select='gt(scene,0.3)'` gives seconds per cut.
   - **faster-whisper** for voice words-per-second + whether a voiceover even exists.
   - **frame extraction + reading the frames** for visual style, caption font/color/grouping/position, format.
2. **Measure the reference** on the dimensions that matter for the medium. For **SHORT-FORM VIDEO**, at
   least:
   - **voice words-per-second** + **is there a voiceover at all**
   - **cut length** (seconds per cut)
   - **caption style** (font, color, word-grouping, position)
   - **visual format** (real footage vs screen-recording vs AI clips vs stills)
   - **energy / pacing**
   - **hook in the first 2-3 seconds**
3. **Measure OURS** on the SAME dimensions.
4. **Build a side-by-side scorecard** (reference target vs ours vs pass/fail) and **FIX every miss**
   until ours matches.
5. **Only then is QA passed.** Never report QA as passed on internal checks alone when a reference exists.

## Use CURRENT data only (King's rule, 2026-06-28)
References must be **present and relevant, not outdated**. A formula that went viral 12-18 months ago may
already be dead, so modeling an old hit can copy a losing pattern. When pulling references:
- **Check the upload date** (TikTok video ID: `datetime.utcfromtimestamp(int(id) >> 32)`). Prefer the last
  ~3-6 months.
- **Prefer recent high-performers.** Sorting by all-time views surfaces old accumulated-view hits, so
  cross-check that the channel's CURRENT posts still use that style and still perform. If recent posts
  switched style or stopped performing, the old pattern is outdated, do not model it.
- **Verify the style is alive** by pulling a recent post before locking the spec. (Example, 2026-06-28:
  the @faceless.inc.proj talking-AI-character format was confirmed against a post from 2 days prior, not
  just a 14-month-old 2.7M-view video, before committing the rebuild to it.)
Outdated data is allowed only when there is a clear reason (a timeless principle, no recent equivalent).

## VOICE specifically
The voiceover must be **EDITED to fit the video**, not left as raw TTS or a raw take. Tighten it to the
reference words-per-second, cut the dead gaps, and align it to the cuts/beats. "Edited to perfect for
the video" is the bar. Voice is just ONE dimension on the scorecard. The rule covers the majority of
QAs, not only voicing.

## Concrete example (the mismatch this rule exists to catch)
- **Reference (hustle.faceless TikTok, measured):** voice ~**3.4 words/sec**, a cut every **~2.2s**,
  a **real masked human** + **real screen-recordings**, **clean white caption pills**. Tight, fast, human.
- **Ours (an earlier @30Kingdavid animatic):** voice ~**2.2 wps** (too slow), **~5s scenes** (too long),
  **AI-image backdrops** and a **cartoon avatar** (wrong visual format). On internal QA it "rendered fine"
  and would have shipped, but on REFERENCE-QA it fails every dimension vs the winner. Fixing to the
  reference numbers (speed up the VO, cut to ~2s, swap to real footage + screen-recordings + caption pills)
  is what makes it competitive.

## Where it is baked in (MANDATORY now)
- **`/content-engine`**: section "REFERENCE-QA (MANDATORY): match the data, not just 'does it render'",
  plus a pointer in Layer 4 (Produce). Supersedes internal-only QA whenever a reference exists.
- **`/find-skills`**: a "REFERENCE-QA" note after the MAXIMUM-DEPTH PRINCIPLE. Any skill/output it builds
  that is modeled on a reference must be verified with REFERENCE-QA, not internal checks alone.
- **Applies to every output modeled on data going forward** (content, ads, client work, the Buka, UGC).
  Add the check to a skill when it next touches reference-modeled production.

## Related
[[reference-deep-storyboard-standard]] · [[feedback-consensus-everything-rule]] ·
[[feedback-qa-before-handover]] · [[project-content-engine]]
