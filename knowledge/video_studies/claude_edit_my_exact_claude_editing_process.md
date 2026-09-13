# my_exact_claude_editing_process
https://www.youtube.com/watch?v=1w_H6uA3N-g

Here is the technical, actionable breakdown of the video editing workflow demonstrated in the tutorial.

---

## 1. ONE-PARAGRAPH SUMMARY + THE "WOW"
The tutorial demonstrates an agentic, code-driven video editing workflow that replaces traditional timeline GUI editors with a natural language terminal interface powered by **Claude** (`01:55`). By pairing Claude with local developer tools (**FFmpeg**, **Whisper**, and **Remotion**) and cloud APIs (**Tella MCP**), the user can clean footage, extract assets, and render styled vertical clips using simple conversational commands. The "wow" factor is the hands-off automation: watching Claude dynamically generate and execute custom Python scripts to slice out dead air (`02:55`), pull slides from a link, crop out background padding, and reframe horizontal footage into a split-screen 9:16 layout without opening Premiere Pro or CapCut.

---

## 2. END-TO-END WORKFLOW
1. **Raw Video Input:** Place the raw `.mp4` file into a local working directory (`02:11`).
2. **First Cut (Silence & Filler Removal):** Run the `/cut-video` tool within Claude's terminal interface (`01:57`). Claude calls Whisper to transcribe the audio, matches word-level timestamps to audio amplitudes, and runs a Python script using FFmpeg to slice out silences, "ums", and "ahs" (`02:56`).
3. **Asset Sourcing:** Paste a link to Google Slides or a PDF into the terminal and ask Claude to extract the images (`05:07`). Claude downloads the file, runs a script to extract each slide, and automatically crops out white borders (`06:52`).
4. **Contextual Overlays:** Prompt Claude to analyze the transcript and overlay the extracted slides over the video during relevant moments (`07:00`). Claude compiles the FFmpeg filter chain to bake the images into the timeline (`07:16`).
5. **Sound & Meme Integration:** Use a custom Slack bot to drop asset links (like a YouTube sound effect at `08:58`). Claude automatically downloads the audio/video into a local `/assets` directory and maps them to the timeline based on context cues (e.g., placing the "Duolingo Correct" chime when a question is answered correctly at `09:23`).
6. **Programmatic Zooming:** Ask Claude to apply zooms (`12:06`). Claude scans the transcript for awkward pauses or jokes and applies camera scale animations at those exact timestamps (`13:43`).
7. **Social Clipping (`/clipify`):** Run the `/clipify` tool (`14:25`). Claude selects high-engagement moments, reframes the 16:9 layout to 9:16 (applying screen splits or zoom-tracking at `15:31`), and burns in styled captions (`15:20`).

---

## 3. EVERY TOOL + ROLE + COST
* **Claude 3.5 Sonnet / Opus (via Claude Code / CLI):** The orchestrator executing terminal scripts. **Cost:** API-dependent usage (approx. $1, $10/hr of heavy rendering).
* **Tella (with MCP Server):** Cloud-based browser screen recorder with a Model Context Protocol (MCP) server integration, allowing Claude to edit and layout recordings directly (`16:35`). **Cost:** Premium subscription.
* **FFmpeg:** Command-line program used locally for all cutting, rendering, overlays, and asset resizing. **Cost:** Free (Open Source).
* **Whisper:** Local AI speech-to-text engine used to generate timestamped transcriptions. **Cost:** Free (Open Source).
* **Remotion:** React-based programmatic video framework used to render dynamic motion graphics and programmatic B-roll (`17:28`). **Cost:** Free (Open Source; commercial license required for large enterprises).
* **Slack API Bot:** Custom script to relay assets from web links into local finder folders. **Cost:** Free.

---

## 4. THE ACTUAL EDITING TECHNIQUE
* **Filler & Silence Cutting:** Whisper maps text characters to strict millisecond markers. FFmpeg runs `silencedetect` to find quiet zones. A Python helper script matches silent blocks with Whisper's word gaps to cleanly excise dead space while preserving natural laughter (`02:56`).
* **Graphics Synchronization:** Remotion elements (written in React code) are mapped directly to JSON arrays containing start/stop cues derived from the transcript.
* **File Formats:** 
  * **In:** Raw H.264/HEVC `.mp4`/`.mov` files and PDF documents.
  * **Out:** Finished H.264 `.mp4` video with AAC audio.

---

## 5. WHAT YOU NEED TO REPLICATE IT
* **Accounts/Keys:** Anthropic Claude API Key, Tella account, and Slack App credentials (optional).
* **Software Installs:** Node.js, Python 3, FFmpeg, git.
* **Git Repositories:** Clone the creator’s open-source packages: `cut-video` (`01:42`) and `clipify` (`15:02`).
* **Required Skill Level:** **Intermediate Developer.** Non-technical users will struggle to debug terminal errors, path issues, Node dependencies, and FFmpeg command errors.

---

## 6. HONEST FEASIBILITY
While highly innovative, this setup is brittle. It is perfect for developers who want to avoid traditional timeline scrubbing, but a standard creator with zero coding experience will struggle to maintain it when Python dependencies or API calls break. However, once configured locally, it is completely functional and eliminates manual slicing.

---

## 7. HOW TO USE IT FOR SHORT PROMO ADS
To generate product promo ads automatically:
1. Record a continuous, unedited 2-minute product screen recording and voiceover.
2. Store your standard assets (intro graphic, outback music, end card) in a local `/assets` directory.
3. Instruct Claude: 
   > *"Run `/cut-video` on `raw_walkthrough.mp4`. Look for spots where I mention 'easy dashboard' and overlay `dashboard_screenshot.png` from `/assets`. Run `/clipify` to generate a 30-second vertical ad with split-screen tracking and active word-by-word captions."*

---

## 8. HYPE vs REAL
* **The Hype:** Fully automated, "one-click" flawless editing.
* **The Real:** Code execution takes time (`03:19`), and the AI can easily misinterpret transcripts, placing overlays or chimes a few seconds off (`07:43`). You will need to manually refine timestamps using prompts like: *"Nudge the third overlay back by 2 seconds."*

---

## 9. THE LOOK / EDIT STYLE
* **Vibe:** Highly optimized, fast-paced "retention-editing" typical of TikTok, Shorts, and Reels.
* **Key Elements:** Rapid-fire jump cuts (no dead air), active speaker split-screens (`15:31`), sudden punchline zooms (`14:05`), clean animated B-roll (`19:49`), and prominent, dynamic burned-in word-by-word captions.

---

## 10. CREATOR + VIDEO TITLE
* **Creator:** Louise de Sadeleer
* **Video Title:** *How to Edit Videos with Claude AI (End-to-End Workflow)*