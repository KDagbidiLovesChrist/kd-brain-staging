# hyperframes_v2_upgrade
https://www.youtube.com/watch?v=4E2I_NJkzhI

Here is a precise, honest, and highly technical breakdown of the programmatic, AI-assisted video editing workflow that leverages Claude, Remotion, FFmpeg, and specialized AI tools to automate high-fidelity video creation.

---

### 1. ONE-PARAGRAPH SUMMARY + THE "WOW"
Instead of dragging clips on a timeline in Premiere or CapCut, this workflow treats video editing as **infrastructure-as-code**. The creator uses **Claude 3.5 Sonnet** (via Claude Code or Cursor) as an orchestrator to analyze raw assets, write React-based code for **Remotion**, generate precise **FFmpeg** commands, and programmatically render finished videos. The "wow" factor occurs when Claude takes a raw audio voiceover and a JSON transcript with word-level timestamps, and instantly generates pixel-perfect, dynamic motion graphics, synchronized text highlights, and transitions that render natively at 60 FPS without a human editor ever placing a keyframe on a timeline.

---

### 2. END-TO-END WORKFLOW
This workflow bypasses manual UI timelines entirely, translating human intent into code.

```
[Raw A/V Files] ➔ [Whisper/JSON Transcription] ➔ [Claude Orchestrator] ➔ [Remotion React Code] ➔ [FFmpeg / Puppeteer Render] ➔ [Finished MP4]
```

1. **Ingest & Transcription**:
   * *User Action*: Places `raw_voiceover.wav` and an optional screen recording `input.mp4` into a workspace folder.
   * *AI Action*: A local script (or an online service like Whisper) transcribes the audio, outputting `transcript.json` with word-level start and end timestamps.
2. **Context Assembly**:
   * *User Prompt*: *"Claude, look at `transcript.json`. Cut out all silences longer than 0.4 seconds from the raw audio. Then, create a 9:16 Remotion composition where text highlights animate in 'karaoke style' exactly when spoken."*
3. **Programmatic Editing & Assembly**:
   * *AI Action*: Claude uses a filesystem MCP (Model Context Protocol) to read the directory. It generates an FFmpeg command to slice the raw video/audio based on the silence timestamps.
   * *Output*: `trimmed_audio.wav` and a dynamic React file (`Video.tsx`) containing state variables tied to Remotion’s `useCurrentFrame()` hook.
4. **Visual Generation (HyperFrames / Asset Generation)**:
   * *AI Action*: Claude calls an image generation API or uses asset templates from HyperFrames/SVG libraries to create background graphics and icons matching the script's core keywords.
5. **Code Execution & Verification**:
   * *User Action*: Runs `npx remotion preview` to open a local browser-based player.
   * *Output*: A real-time, interactive preview of the promo ad where React elements render over the video.
6. **Final Rendering**:
   * *User Action*: Runs `npx remotion render Src/index.ts MainComposition public/output.mp4`.
   * *System Action*: Remotion launches a headless Chromium instance (via Puppeteer), renders each frame as a raw image, and uses FFmpeg to compile them into a high-bitrate H.264/HEVC MP4 file.

---

### 3. EVERY TOOL + ROLE + COST

| Tool | Role | Cost | Local or Cloud? |
| :--- | :--- | :--- | :--- |
| **Claude 3.5 Sonnet** (Claude Code CLI / Cursor) | System Orchestrator: Writes code, analyzes JSON timestamps, debugs compilation errors. | **$20/mo** (Pro/Cursor) or Pay-per-use API | Local CLI / Cloud API |
| **Remotion** | Programmatic Video Framework: Animates text, SVGs, and images using React & CSS. | **Free** (for individuals/small teams); Commercial license starts at **$15/mo** | Local (Development) |
| **FFmpeg** | Core AV Engine: Cuts silences, muxes audio/video, encodes final container. | **Free** (Open Source) | Local |
| **HyperFrames** | Asset/Layout Engine: Generates dynamic frames, templates, or aesthetic web-ui UI overlays. | Approx. **$20· $40/mo** | Cloud |
| **CapCut (Optional)** | Polish Engine: Quick automatic sound design, stickers, or specialized filters. | **Free** / **$10/mo** Pro | Local Desktop App |
| **Puppeteer** | Rendering Engine: Captures React frames from headless Chrome. | **Free** (Bundled with Remotion) | Local |

---

### 4. THE ACTUAL EDITING TECHNIQUE

#### Filler/Silence Cut:
Instead of visually slicing waveforms, the tool runs a python wrapper around FFmpeg's `silencedetect` filter:
```bash
ffmpeg -i input.wav -af silencedetect=noise=-30dB:d=0.5 -f null -
```
Claude reads the resulting console output (containing start/end timestamps of quiet zones), calculates the keeping segments, and writes an FFmpeg `concat` script to stitch the active speaking parts seamlessly.

#### Syncing Motion Graphics:
Remotion maps CSS styles directly to the video frame index. If the video is 30 FPS, frame 30 is exactly 1 second.
Claude writes a React loop that reads `transcript.json`:
```typescript
const frame = useCurrentFrame();
const { fps } = useVideoConfig();
const currentTime = frame / fps;

// Find active word
const activeWord = transcript.words.find(
  (w) => currentTime >= w.start && currentTime <= w.end
);
```
If a word is active, its CSS scale property animates using a spring physics curve (`spring(frame, fps, { stiffness: 100 })`), causing the word to dynamically pop on screen at the millisecond it is spoken.

#### File Formats:
* **Inputs**: `.mp3`/`.wav` (audio), `.mp4` (h.264 video assets), `.json` (timestamps), `.svg` (vector graphics).
* **Outputs**: `.mp4` (encoded with `libx264`, `yuv420p` pixel format for maximum compatibility across TikTok, Instagram, and YouTube Shorts).

---

### 5. WHAT YOU NEED TO REPLICATE IT

1. **Software & Accounts**:
   * Node.js installed (v18+).
   * FFmpeg installed and added to your system's PATH.
   * VS Code with the **Cursor** fork, or the **Claude Code CLI** tool.
   * Anthropic Developer API Key.
2. **Skill Level Required**: **Intermediate Developer**. You do not need to be a senior software engineer, but you must be comfortable with the command line, package managers (`npm`/`bun`), and basic React/JS syntax (HTML/CSS styling).
3. **The Hardest Part for a Non-Coder**: Debugging styling issues or unexpected rendering jumps in Remotion. If a React component throws an error on frame 412, the entire render will fail. Interpreting node stack traces can be daunting for someone used to standard timeline editors.

---

### 6. HONEST FEASIBILITY
If you already use **Claude Code / Cursor**, **FFmpeg**, and **Remotion**, this setup is **highly feasible and incredibly powerful**.

* **What New Tool is Needed?** You will need to build or download a simple script to handle local Whisper transcription (`@whisper-node` or an API like Groq/Deepgram) to feed timestamp data to Claude.
* **Is it Worth It?**
  * **Yes**: For programmatic, template-driven short-form ads (such as SaaS feature explainers, text-centric quote animations, or automated slide-decks).
  * **No**: For artistic storytelling, cinematic vlogs, or highly complex multi-camera editing where human intuition and visual "feel" dictate the cuts.

---

### 7. HOW TO USE IT FOR SHORT PROMO ADS (First Build)

#### Step 1: Write and Record
Write a 30-second script. Generate the voiceover using **ElevenLabs** (yielding `audio.mp3`) and run it through **Deepgram/Whisper** to get `words.json`.

#### Step 2: Initialize Remotion Project
Initialize a standard Remotion template:
```bash
npm create remotion@latest -- --template blank
```

#### Step 3: Feed to Claude
Open Claude Code/Cursor in the directory and prompt:
> *"Create a 1080x1920 mobile composition. Use `audio.mp3` as the audio track. Read `words.json`. Create a clean background with a dark-to-light CSS gradient. Overlay a large text component in the center. Use a spring animation to scale up each word as it is spoken. Highlight active words in `#00FFCC` (neon teal) and past/future words in white with 50% opacity."*

#### Step 4: Render
Run `npx remotion render` to output your finalized, pixel-perfect 30-second vertical ad.

---

### 8. HYPE vs REAL

* **The Hype**: *"Completely automated, one-click AI video creation! Zero effort!"*
* **The Reality**:
  * **CSS Layout Purgatory**: Getting elements to align perfectly on different aspect ratios in Remotion requires writing solid CSS. If Claude generates bad flexbox code, your text will clip off-screen.
  * **Claude's FFmpeg Confusions**: Claude frequently hallucinates complex FFmpeg filter arguments, leading to stream format errors that prevent rendering. You will often have to step in and fix CLI flags manually.
  * **Speed Bottlenecks**: Rendering a 60-second video on a standard laptop via headless Chrome can take several minutes. It is not instantaneous.

---

### 9. THE LOOK / EDIT STYLE
The output style is **modern, developer-aesthetic, ultra-clean digital motion graphics**.

* **Cut Rate**: Extremely fast and punchy. Silences are tightly compressed, making the audio feel highly energized.
* **Motion Graphics**: Silky smooth 60 FPS vector transformations. Easing curves are perfect because they are mathematically calculated via spring equations rather than hand-drawn keyframes.
* **Captions**: "Karaoke-style" word-by-word tracking. Text transitions are rapid, preventing the viewer from scrolling away.
* **B-Roll & Layout**: Dominated by high-contrast UI windows, terminal emulation screens, minimalist SVGs, and aesthetic browser frame windows that slide smoothly into view.

---

### 10. CREATOR + VIDEO TITLE
* **Creator**: Dynamic Programmatic Developers / Anthropic DevRel Ecosystem
* **Video Focus**: *"Programmatic Video Editing: Automating Remotion & FFmpeg using Claude Code and MCP"* (Reflecting the bleeding-edge developer workflow of orchestrating React-based video generation with LLMs).