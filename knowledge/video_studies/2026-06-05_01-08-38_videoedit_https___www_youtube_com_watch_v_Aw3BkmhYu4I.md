# Video-Edit Tutorial Study: https://www.youtube.com/watch?v=Aw3BkmhYu4I
_Analysed: 2026-06-05 01:08_

Here is a precise, actionable, and honest breakdown of the video tutorial for King:

## 1. ONE-PARAGRAPH SUMMARY

This tutorial showcases a workflow that leverages AI (specifically Claude Code orchestrated with HyperFrames and a custom "Video Use" skill) to automate significant portions of video editing, from trimming raw footage to syncing sophisticated motion graphics. The core idea is to transform traditional, manual video editing into a natural language prompting and iterative refinement process, drastically reducing the time and skill required. The "wow" claim is the ability to generate polished, dynamically animated videos end-to-end with minimal human intervention beyond providing text-based instructions and raw footage.

## 2. THE END-TO-END WORKFLOW (numbered steps)

The workflow consists of several key stages, blending AI automation with human oversight:

1.  **Project Setup (Initial Phase):**
    *   **User Action (3:48-4:56):** King opens the Claude Desktop app and selects an empty folder (or clones the `hyperframes-student-kit` GitHub repo, which is recommended). He provides Claude with the URLs of two GitHub repositories: `heygen-com/hyperframes` and `browser-use/video-use`, along with a natural language prompt instructing Claude to integrate these video editing tools into the workspace, pulling in necessary skills for trimming, editing, animating, and rendering the full pipeline.
    *   **AI Action (5:02-6:00):** Claude initializes a session, analyzes the GitHub repos, pulls in relevant files and "skills" (functions), and sets up the project environment. It confirms that the full pipeline is "wired up" and ready.
    *   **Output:** A configured Claude Code workspace with integrated video editing capabilities.

2.  **Raw Video Ingestion & Initial Trim/Edit:**
    *   **User Action (6:05-7:00):** King drops his raw `.mp4` video file (e.g., `Edit Demo Raw.mp4`) into the project folder. He then inputs a natural language prompt to Claude, tagging the video file (e.g., `@Edit Demo Raw.mp4`), instructing it to use the `video-use` tool to analyze, remove filler words, silences, and retakes, and to prepare for HyperFrames motion graphics. He can specify a "punchy" edit style (12:30).
    *   **AI Action (9:44-12:40):** Claude analyzes the video, transcribes it (using ElevenLabs API in this demo), identifies potential cuts (false starts, stutters, silences), and presents an "Edit plan" (a table showing action, time, and reason for each cut). It also calculates an "Estimated runtime." Claude asks for approval or revisions.
    *   **User Action (12:17-12:40):** King reviews the edit plan and provides feedback (e.g., "yep, make this as punchy as possible").
    *   **AI Action (12:40-12:56):** Claude processes the feedback, refines the edit plan, and executes the cuts.
    *   **Output (12:56-13:55):** An `edited.mp4` file (shorter, trimmed), an `edited.srt` subtitle file, an `edl.json` (Edit Decision List) file documenting the cuts, and a `transcript/Edit Demo Raw.json` (word-level transcript).

3.  **Motion Graphics Integration (Iterative Design):**
    *   **User Action (14:34-17:13):** King gives Claude detailed natural language instructions for motion graphics, referencing specific timestamps or phrases from the edited video. For example, "At the beginning... pop up a liquid glass-style card... words to appear as karaoke-style subtitles... title of a video" (15:12). For another section, "add a card at the bottom of the screen that says 'Mistakes will be cut'" (15:40).
    *   **AI Action (17:13-17:49):** Claude, put in "Plan mode" (17:17), reviews the entire conversation and the transcript. It then proposes a detailed "HyperFrames Motion Graphics Plan" outlining the aesthetic direction (e.g., "Motion-Philosophy × Liquid Glass Fusion"), color palette, and a "Beat Timeline" showing specific elements (cards, text, animations) with their anchor words and timings (17:49-18:57).
    *   **User Action (18:57-19:50):** King reviews the detailed plan, potentially highlighting sections or specific details (e.g., "Beat A: liquid-glass card positioned... covers empty wall + door area; does not cover speaker"). He can leave comments on specific elements if using the VS Code interface (19:08). He can then approve or revise the plan (19:51).
    *   **AI Action (19:51-20:30):** Claude incorporates revisions (e.g., adding an outro scene, shifting face-cam) and presents a revised plan.
    *   **Output:** A detailed plan for all motion graphics elements, their styles, and precise timings. Claude will then proceed to render based on this plan.

4.  **Final Rendering & Iteration on Visuals:**
    *   **AI Action (21:39-21:55):** Claude renders a preview version of the video with all motion graphics applied.
    *   **User Action (22:34-24:06):** King reviews the rendered video, identifying visual issues like a card covering his face, an unwanted grid overlay, or blurry elements. He provides specific natural language feedback (e.g., "liquid glass looks good, but it's actually covering my face a little bit. If you could just scale this down and then maybe crop off the right side a little bit so it doesn't cover my face, that would be beautiful").
    *   **AI Action (24:06-25:02):** Claude implements the visual fixes based on the detailed feedback, regenerates the HTML/CSS/JS for HyperFrames, and re-renders a new preview.
    *   **Output (25:02-26:02):** The final, polished `.mp4` video with all desired edits and motion graphics. Claude can also provide the underlying HTML code for each "beat" (scene) if needed for manual tweaks (26:34).

## 3. EVERY TOOL USED + ITS ROLE + COST

*   **Claude Code (Claude Desktop App / API):**
    *   **Role:** The central orchestration engine. It receives natural language prompts, interprets user intent, interacts with GitHub repos, manages project files, invokes other skills (like `video-use`), and plans/executes video editing and motion graphic generation. It acts as the "orchestrator" or "brain" connecting all parts.
    *   **Cost:** Requires a paid Claude Code plan (e.g., "Opus 4.7" is mentioned, which comes with a usage limit of 1M tokens per 5 hours, and weekly limits). The video mentions a project consumed "238.6k tokens" for one iteration (27:28), indicating a cost tied to usage.
    *   **Runs:** Locally (Desktop app) or in the cloud (API). The demo uses the Desktop app for user interaction.

*   **HyperFrames:**
    *   **Role:** An HTML-native motion graphics video workspace. It defines the structure and animations for the motion graphics using HTML, CSS, and GSAP. It processes transcription data to sync elements precisely. It generates the rendered video output. The HyperFrames *Editor* provides a visual interface for previewing and adjusting elements (0:43).
    *   **Cost:** Not explicitly stated as paid in the video, but it's a tool from "HeyGen" (a company) implying potential licensing or usage fees. The video mentions its CLI (Command Line Interface) and "Gate 0" (a validation/preview step), suggesting a robust framework.
    *   **Runs:** Local (CLI, Editor) or potentially cloud-based rendering (not specified for this demo).

*   **Video Use:**
    *   **Role:** A specific "skill" (collection of scripts/functions) within the HyperFrames ecosystem, invoked by Claude. Its primary function is to edit raw video clips by cutting filler words, mistakes, and silences based on a transcript. It can also perform basic color grading.
    *   **Cost:** Likely included within the HyperFrames framework or accessible via Claude Code's capabilities. Transcription APIs (ElevenLabs/OpenAI) used by Video Use have their own costs.
    *   **Runs:** Integrated into the Claude Code environment; processing occurs locally or via integrated APIs.

*   **FFmpeg:**
    *   **Role:** A powerful open-source multimedia framework used for handling video and audio. It is implicitly used by HyperFrames to perform the actual video encoding and rendering of the final `.mp4` file (5:41).
    *   **Cost:** Free and open-source.
    *   **Runs:** Locally, typically as a dependency of HyperFrames.

*   **ElevenLabs API / OpenAI Whisper API:**
    *   **Role:** Used by the `video-use` skill to transcribe the raw audio from the video into text with word-level timestamps. This timestamped transcript is crucial for precise cutting and motion graphic synchronization.
    *   **Cost:** Paid API services. The video shows generating an API key for ElevenLabs (11:00). OpenAI Whisper also has usage costs.
    *   **Runs:** Cloud-based API services. A local Whisper tool is also mentioned as a free alternative (10:33).

*   **VS Code (Visual Studio Code):**
    *   **Role:** A code editor used in conjunction with Claude Code, allowing users to see the project's file structure, modify files (like the `.env` for API keys, or potentially HTML/CSS directly if desired), and interact with Claude's terminal.
    *   **Cost:** Free.
    *   **Runs:** Locally.

## 4. THE ACTUAL EDITING TECHNIQUE (be precise)

*   **Cutting Stutters/Filler Words/Silences:**
    *   The `video-use` skill (invoked by Claude) performs this.
    *   It first transcribes the video using an API (e.g., ElevenLabs or OpenAI Whisper) to generate a word-level transcript with precise start and end timestamps for each word (14:12).
    *   It then analyzes this transcript to identify common filler words ("um," "uh," "hmm"), prolonged silences, and retake moments.
    *   Based on user instructions (e.g., "make this as punchy as possible"), it uses these timestamps to create an Edit Decision List (`edl.json`), marking segments to `KEEP` or `CUT` (9:48). It can "snap to word boundaries" and apply lead/padding to cuts (12:27).
    *   Audio fades (30ms) are applied at each boundary for smooth transitions (9:45).

*   **Syncing Motion Graphics/Animations:**
    *   HyperFrames is responsible for this.
    *   It uses HTML/CSS/GSAP to create motion graphics and overlays.
    *   Crucially, it uses the word-level timestamps from the `transcript.json` to synchronize the appearance and disappearance of specific text and graphical elements with the speaker's words. For example, if King says "you" at 11.199 seconds, a motion graphic tied to that word will appear at that exact timestamp (14:26).
    *   The system creates "beats" (scenes) that are triggered by "anchor words" in the transcript (18:55).

*   **How the Final Video is Actually Rendered:**
    *   After all editing and animation plans are finalized and approved, HyperFrames uses its CLI (Command Line Interface) to render the final video.
    *   While not explicitly stated, HyperFrames likely utilizes FFmpeg (which is mentioned as "installed, doctor green" at 5:41) under the hood for high-quality video encoding.
    *   The output is a single `edited.mp4` file (12:58).

*   **What File Formats Go In and Come Out:**
    *   **Input:** Raw `.mp4` video file (e.g., `Edit Demo Raw.mp4`).
    *   **Output:**
        *   `edited.mp4` (the final video file).
        *   `edited.srt` (subtitle file with 70 cues on the edited timeline).
        *   `edl.json` (Edit Decision List with 5 ranges, cuts documented with reasons).
        *   `transcripts/Edit Demo Raw.json` (cached Scribe output/word-level transcript).
        *   HTML files (`b01-title.html`, `b02-mistakes.html`, etc.) for each motion graphics "beat" (26:35).

## 5. WHAT YOU NEED TO REPLICATE IT

To replicate this workflow, King would need:

*   **Accounts & API Keys:**
    *   **Paid Claude Code Plan:** Access to Claude Opus 4.7 or higher, including the Claude Desktop App. This is non-negotiable for using Claude Code.
    *   **ElevenLabs or OpenAI API Key:** A paid API key for one of these services for high-quality transcription with word-level timestamps. This key needs to be stored in a `.env` file within the project directory (11:07).

*   **Software & Installs:**
    *   **Claude Desktop App:** The primary interface for interacting with Claude Code (3:25).
    *   **VS Code (Optional but Recommended):** For viewing and managing project files, especially the `.env` file and potentially the generated HTML/CSS (11:29, 26:17).
    *   **Git:** To clone the necessary GitHub repositories.
    *   **Node.js & npm (Implicit):** HyperFrames is an HTML-native framework, implying Node.js and npm are needed to run its CLI and manage dependencies.
    *   **FFmpeg (Implicit):** Likely installed as a dependency or standalone for video rendering by HyperFrames.

*   **Project Setup:**
    *   **HyperFrames Student Kit:** Clone the `nateherkal/hyperframes-student-kit` GitHub repository (or the individual `heygen-com/hyperframes` and `browser-use/video-use` repos) into a local folder. This provides the framework and skills (4:01).

*   **Skill Level Required:**
    *   **Non-coder friendly (but with caveats):** While the video claims "no coding required" and "beginner friendly," this is more accurate for the *interaction* with Claude via natural language *after* initial setup.
    *   **Hardest Part for a Non-coder:**
        1.  **Initial Environment Setup:** Cloning GitHub repos, installing Node.js/npm, resolving dependencies, and correctly placing API keys in a `.env` file can be intimidating and prone to errors for someone unfamiliar with command-line interfaces and development environments.
        2.  **Prompt Engineering:** Achieving desired stylistic outcomes for motion graphics requires highly specific and iterative prompting. While Claude helps "plan," guiding it to an exact vision takes practice and a good understanding of what AI can and cannot yet do.
        3.  **Debugging/Troubleshooting:** When things don't work as expected (e.g., issues in the preview, unexpected visual glitches), a non-technical user might struggle to diagnose or fix problems without basic coding knowledge or understanding of the underlying tools.

## 6. HONEST FEASIBILITY FOR KING (non-technical, lean budget, already has Claude Code + FFmpeg + Remotion)

King can *realistically attempt* this, but with a significant learning curve and potential costs.

*   **Overlaps with existing tools:**
    *   **Claude Code:** This is central to the workflow, and King already has it. This is a huge advantage as it handles the "brain" of the operation.
    *   **FFmpeg:** King already has FFmpeg. HyperFrames uses it for rendering, so this is another overlap.
    *   **Remotion:** King has Remotion. The video explicitly compares HyperFrames and Remotion for animations (7:37-9:16). While the creator prefers HyperFrames's HTML-native approach for engagement, Remotion is capable of motion graphics. The `video-use` skill can be adapted to integrate with Remotion for animation and rendering if HyperFrames proves too complex or costly.

*   **New things King would actually need:**
    *   **HyperFrames (and its ecosystem):** This is the main new component. It provides the structured HTML-native motion graphics, the "video editing studio" interface, and the logic to sync graphics with audio transcripts.
    *   **Transcription API:** King would need a paid API key for ElevenLabs or OpenAI for high-quality, timestamped transcripts, unless he can find a reliable free local Whisper setup.

*   **Is it worth paying for?**
    *   **Yes, potentially.** If King plans to create many short video ads regularly, the automation for trimming and the precise syncing of motion graphics could be a massive time-saver. The iterative "Plan Mode" (17:17) means he doesn't have to code every animation directly, but can guide Claude with natural language. This significantly reduces the *manual* editing time.
    *   **Cost Factor:** The primary cost would be Claude Code's token usage (27:28) for planning and execution, and the transcription API fees. HyperFrames's direct cost is not clear from the video, but its value lies in the structured HTML approach and editor. If the cost for HyperFrames (as a product) is substantial, King could potentially use only `video-use` for trimming and manually create/sync motion graphics in Remotion, but that would lose some of the "AI orchestration" benefit.

## 7. HOW KING COULD USE THIS FOR HIS OWN VIDEO ADS

King can adapt this workflow to create short promotional/ad videos for his web-design business and client demos:

1.  **Record Raw Ad/Demo Video:** King records his short ad/demo video using his usual setup. He doesn't need to worry about "ums," "ahs," or slight pauses, as these will be edited out. (This is his current manual "Raw file" step).

2.  **Upload to Claude Code Project:** King drags and drops his raw `.mp4` ad video file into his `video-projects/ads/` folder within the HyperFrames Student Kit (managed by Claude Code).

3.  **Initial AI Trim and Edit:** King opens a new Claude Code session and prompts it (using the `video-use` skill):
    > "Hey Claude, use the `video-use` tool to edit this raw video file: `@path/to/my_raw_ad.mp4`. Analyze it, remove any filler words, silences, or retakes. Make the edit as punchy and concise as possible. Generate the transcript with word-level timestamps."
    *   *AI output:* A proposed edit plan, a trimmed `edited.mp4`, `edited.srt`, `edl.json`, and `transcript.json`.

4.  **Review and Approve Edits:** King reviews the edit plan and the trimmed video. If any cuts aren't quite right, he can tell Claude to `Revise` the plan (19:57). Once satisfied, he `Accepts` the edits.

5.  **Design Motion Graphics (Iterative with Claude):** King continues the Claude Code session, now focusing on motion graphics for his web-design ad:
    > "Okay, now add motion graphics using HyperFrames to this `edited.mp4`.
    > *   At the beginning, when I introduce my business, show a liquid-glass card on the left with my business name 'King's Web Design' and some text appearing karaoke-style: 'Modern, Responsive, Affordable'.
    > *   When I talk about 'client success stories', show a dynamic bar chart animation on the right side of the screen that increases over time, labeled 'Client Satisfaction: +247%'.
    > *   For the outro, transition the face-cam to the bottom right as a small PIP, and fill the left half with a dark, modern background with a large, glowing 'THANKS FOR WATCHING' text. Add my website address 'kingswebdesign.com' below it in smaller text. Ensure everything syncs perfectly to my words."
    *   *AI Action:* Claude enters "Plan mode" (17:17), researches HyperFrames patterns, and proposes a detailed plan including aesthetic direction (e.g., specific liquid glass styles, colors, text animations), and a timeline for each "beat" (17:49).

6.  **Refine Motion Graphics:** King reviews Claude's detailed plan. He can tell Claude:
    > "This looks great, but for the 'King's Web Design' card, ensure it doesn't cover my face at all, maybe scale it down and shift it slightly left. Also, can the 'Client Satisfaction' chart use a teal gradient instead of orange? For the outro, make the 'THANKS FOR WATCHING' text glow a bit more intensely." (23:01-24:06 demonstrates this feedback loop).
    *   *AI Action:* Claude revises the HyperFrames HTML/CSS/JS and re-renders a new preview.

7.  **Final Render:** Once King is satisfied with the preview, he instructs Claude to "Confirm the fixes land and I'll run the draft render." (25:02)

8.  **Publish:** King uploads the final `edited.mp4` to his social media channels or includes it in client presentations.

## 8. WHAT IS HYPE vs WHAT IS REAL

*   **Hype:**
    *   **"Claude Just Destroyed Every Video Editing Tool" (Video Title):** This is classic YouTube hyperbole. While it automates many steps, it doesn't "destroy" traditional tools or professional editors. It creates a new category of editing, complementing existing tools.
    *   **"No coding required" (0:15):** While direct code writing is minimized, *understanding* the environment, files, and debugging (if errors occur) requires a degree of technical literacy. Setting up repos, API keys, and managing files (especially the `.env` file for credentials, 11:07) isn't "no coding."
    *   **"End-to-end" automation:** While it automates the *pipeline*, the process demonstrated is still heavily iterative and requires significant human oversight, review, and specific direction. It's not a "set it and forget it" solution.

*   **Reality / Caveats:**
    *   **Cost of Tokens:** The usage of Claude Opus 4.7 is expensive. Consuming "238.6k tokens" for *one iteration* (27:28) can quickly deplete a lean budget. The more specific and iterative King needs to be, the higher the token cost. This is a critical hidden cost.
    *   **Time for Iteration:** Each iteration takes time for Claude to process and render. While faster than manual editing, the back-and-forth planning and fixing of visual glitches (e.g., blurry text, cards covering face, unwanted grid overlays, 22:34) means a video won't be perfect on the first try.
    *   **Initial Setup Difficulty:** For a truly non-technical user, cloning GitHub repos, installing command-line tools like Node.js, and correctly configuring API keys and environment variables could be a significant barrier. The video glosses over potential installation issues and error messages.
    *   **Quality Control & Tweaking:** The video showcases instances where Claude's initial output for motion graphics isn't perfect (22:34). King needs to watch the preview carefully and provide precise feedback, which is still a manual skill. The "muffled sound in preview" (22:06) also indicates potential friction points.
    *   **Proprietary Nature of HyperFrames:** While the repos are on GitHub, the core "magic" and how it's specifically integrated with Claude Code (e.g., the "skills" architecture) might be proprietary to HeyGen/Anthropic, making true self-hosting or deep customization challenging without a vendor relationship.
    *   **Learning Curve for AI Style:** Claude needs "training data" (20:59) (i.e., multiple examples) to learn King's preferred style. The first few videos might require extensive prompting and iteration until Claude "gets" his aesthetic.

*   **Where a beginner would get stuck:**
    *   **Command Line & File Paths:** Typing commands and understanding file paths, especially when Claude gives specific output locations (13:08), can be confusing.
    *   **API Key Management:** Correctly generating and securely storing API keys in a `.env` file.
    *   **Debugging:** Understanding why Claude might fail to execute a command or produce a particular visual effect, and how to troubleshoot.

## 9. THE CREATOR + VIDEO (confirm)

*   **Creator/Channel Name:** Nate Herkal / AI Automation Society
*   **Video Title:** Claude Just Destroyed Every Video Editing Tool