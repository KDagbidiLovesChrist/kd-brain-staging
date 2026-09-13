# Loom Video URLs Awaiting Transcript Extraction
*Captured 2026-05-23 during AIS+ classroom audit. All AIS+ lesson videos are Loom-hosted (not YouTube). The youtube-transcript-api script won't work on these. Need a Loom-specific pipeline.*

## Pipeline options
1. **Loom's own transcript API**, `https://www.loom.com/transcribe/<video_id>`, may require auth
2. **Download via yt-dlp + Whisper local**, slow but works fully offline
3. **Loom MCP**, if one exists, would be cleanest
4. **Browser-side scrape**, navigate to non-embed Loom URL and grab the transcript element

Recommended: Option 2 (yt-dlp + Whisper) for resilience, no auth required, fully local.

## Captured URLs (16 priority AIS+ lessons → 9 had Loom embeds visible)

| Lesson | Loom Embed URL | Video ID |
|---|---|---|
| AIS+ Claude Code 1.3 · **The WAT Framework** | https://www.loom.com/embed/559d5d8f6b97461b9ff2fdd29e2367f7 | 559d5d8f6b97461b9ff2fdd29e2367f7 |
| AIS+ Claude Code 1.10 · Token Management | https://www.loom.com/embed/22fb766495034f7aafb276439d7b453c | 22fb766495034f7aafb276439d7b453c |
| AIS+ Build Portfolio Phase 3.1 · Intro to Phase 3 | https://www.loom.com/embed/0365061b86f146c786373aa1d009a9a7 | 0365061b86f146c786373aa1d009a9a7 |
| AIS+ Build Portfolio Phase 3.2 · The Time Lens for Businesses | https://www.loom.com/embed/49699ace91af4e52a1be329bee1c1161 | 49699ace91af4e52a1be329bee1c1161 |
| AIS+ Build Portfolio Phase 3.3 · The Income Lens for Businesses | https://www.loom.com/embed/43ec12ca846140eba3e47d5841bfdb05 | 43ec12ca846140eba3e47d5841bfdb05 |
| AIS+ Build Portfolio Phase 3.4 · The SOP Audit: Inventory vs Creation | https://www.loom.com/embed/4f34918780114a92a434b2c552451583 | 4f34918780114a92a434b2c552451583 |
| AIS+ Build Portfolio Phase 3.5 · Scoring Before Mapping (Business ICE) | https://www.loom.com/embed/b6e4bfe8f96b4f98a5d9e87fcafe4a93 | b6e4bfe8f96b4f98a5d9e87fcafe4a93 |
| AIS+ Build Portfolio Phase 3.6 · The Live Blueprint: Mapping in the Room | https://www.loom.com/embed/bb4956d1cc6d4ef7899e5c3e946bb9a1 | bb4956d1cc6d4ef7899e5c3e946bb9a1 |
| AIS+ Build Portfolio Phase 3.7 · Should you charge for the Opportunity Map? | https://www.loom.com/embed/3fc73a4dd4b3403ca2eb670f950534b7 | 3fc73a4dd4b3403ca2eb670f950534b7 |

## Lessons WITHOUT visible Loom embed at extract time (need re-extraction or alternate)
- AIS+ Live Call TrueHorizon Parts 1-3 + Discovery Call SOP (4 lessons), videos may need page interaction to reveal player
- Nate's Business Talks (Your First Client, Pricing Workflows, Stop Selling Agents), same

## When the Loom pipeline is built
Run extraction on every URL above → save transcripts to `knowledge\ais_resources\transcripts\loom_<video_id>.md`. Then update this file to mark each as `[TRANSCRIBED]`.
