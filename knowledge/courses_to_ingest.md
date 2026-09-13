# Courses to Ingest · Built with AI Pipeline Build

**Created:** 2026-05-26 12:30pm
**Purpose:** Course material King David wants Claude to learn from before building the autopilot pipeline.
**Method:** YouTube Transcript Extractor (`tools\transcript_extractor\extract_youtube_transcript.py`) pulls transcripts. Claude learns patterns. Apply to pipeline build.

---

## Drop URLs here (paste freely, no formatting needed)

King David adds URLs as he remembers them. Format: just paste the URL on a new line. Title optional.

### AIS+ modules

(Specific AIS+ classroom URLs he wants Claude to learn from, module names + URLs if he has them)

-

### Liam Ottley YouTube

(Specific Liam Ottley videos worth modelling)

-

### Nick Saraev YouTube

(Specific Nick Saraev videos worth modelling)

-

### Mubashir tutorials

(Any "how to edit cash cow videos" / "how to make faceless YouTube" Mubashir tutorials)

-

### Other YouTube channels / videos

(Anything else King David has watched that we should learn from, AI Andy, Income Stream Surfer, Helena Liu, AI Foundations, etc.)

-

### Free courses / paid courses

(Skool communities, Udemy courses, etc., name + URL)

-

---

## What Claude will find autonomously

Even if King David shares 0 URLs, Claude will research:
- Top 5-10 "how to build faceless YouTube automation" tutorials on YouTube
- Top 3-5 "AI YouTube channel pipeline" tutorials
- AIS+ classroom transcripts (if accessible via existing setup)
- Open-source faceless YouTube automation projects on GitHub

Add findings to this file under "## Claude-sourced material" once extracted.

---

## Extraction process

For each URL:
1. Run: `python tools\transcript_extractor\extract_youtube_transcript.py <url>`
2. Save transcript to `AIS_Audit\transcripts\` or similar
3. Claude reads transcripts, extracts patterns
4. Synthesised learnings → `knowledge\autopilot_pipeline_spec.md`

---

## Drop URLs below
