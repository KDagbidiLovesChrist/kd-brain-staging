# claude_editing_unrecognizable
https://www.youtube.com/watch?v=Aw3BkmhYu4I

This tutorial, "Claude Just Destroyed Every Video Editing Tool" by Nate Herk of AI Automation, showcases an end-to-end AI-powered video editing workflow using Claude Code and HyperFrames. The "wow" factor lies in Claude's ability to act as an orchestrator, taking a raw video file, automatically trimming filler words and mistakes, and then generating motion graphics and captions that are perfectly synced to the speaker's dialogue, all via natural language prompts, drastically reducing manual editing time.

## 1. ONE-PARAGRAPH SUMMARY + the "wow"

Nate Herk demonstrates an impressive AI video editing pipeline that transforms raw footage into polished, motion-graphic-rich videos with minimal manual intervention. Using Claude Code as the central orchestrator, the system integrates tools like Video Use for intelligent trimming of mistakes and dead space, and HyperFrames for generating dynamic, liquid-glass style motion graphics and karaoke-style subtitles. The "wow" is seeing how natural language commands guide Claude to perform complex editing tasks, including synchronizing visuals to specific speech segments and even iterating on aesthetic directives, essentially automating a significant portion of what would typically be a time-consuming manual post-production process.

## 2. END-TO-END WORKFLOW

The workflow simplifies video creation into a few key steps driven by natural language:

1.  **Raw File Ingestion (User Action)**: The user drops a raw video file (e.g., `intro-raw.mp4`) into the project folder. (0:03, 0:28)
2.  **AI Trimming/Editing (Claude + Video Use)**: The user prompts Claude to use the "Video Use" tool to analyze the video, remove filler words ("um," "uh," "hmm"), silences, and retakes. Claude provides an "edit plan" outlining cuts. (0:05, 0:34, 6:39, 10:25, 12:00)
    *   *Input:* Raw video file (`.mp4`), user prompt.
    *   *AI Action:* Transcribes audio (using ElevenLabs or OpenAI Whisper), identifies segments for keeping/cutting based on speech analysis, generates an Edit Decision List (EDL) in JSON format, and outputs an edited `.mp4` and `.srt` (subtitle) file. (12:58)
    *   *Output:* Edited video (`edited.mp4`), SRT subtitle file (`edited.srt`), EDL JSON (`edi.json`), transcript JSON (`transcript.json`).
3.  **AI Motion Graphics & Animation (Claude + HyperFrames)**: The user provides specific instructions to Claude on the desired motion graphics style (e.g., liquid-glass cards, dynamic elements) and how they should sync with the speech from the edited video. Claude then uses HyperFrames to generate these. (0:07, 0:39, 7:01, 14:58, 17:14)
    *   *Input:* Edited video (`edited.mp4`), EDL/transcript, user prompt describing visuals and timing.
    *   *AI Action:* Claude, acting as an orchestrator, uses the HyperFrames framework (which leverages HTML/CSS/GSAP) to create scenes/beats. It aligns these visual elements with the precise timestamps provided by the transcript and EDL. It can generate multiple "beats" (scenes) based on the input. (17:42, 18:33, 18:58)
    *   *Output:* A rendered video with integrated motion graphics.
4.  **Final Render (HyperFrames)**: Once the user approves the generated plan and motion graphics, HyperFrames renders the final video. (0:18, 2:01, 26:10)
    *   *Input:* HTML/CSS/JS compositions from HyperFrames.
    *   *AI Action:* HyperFrames uses FFmpeg and possibly other tools (Docker) to render the final video. (5:44)
    *   *Output:* Final video (`final.mp4`).

## 3. EVERY TOOL + ROLE + COST

*   **Claude (Anthropic's Claude Code)**:
    *   **Role**: The primary AI orchestrator. It receives natural language prompts, understands the intent, identifies necessary tools/skills (Video Use, HyperFrames), breaks down the task, executes commands, and presents results. It can review output and iterate based on user feedback. It runs on a local desktop app or via VS Code. (0:01, 3:17, 3:25, 3:45, 4:32)
    *   **Cost**: Requires a paid Claude plan (e.g., Claude Pro or Team) for access to Claude Code and its larger context window. (3:45)
*   **Video Use**:
    *   **Role**: An AI-powered skill/tool within Claude Code that specializes in trimming and editing raw video. It leverages speech-to-text transcription to detect and cut filler words, dead space, and false starts. (2:12, 6:41, 10:19)
    *   **Cost**: Functionality seems integrated into Claude Code or the HyperFrames student kit. Transcription APIs like ElevenLabs or OpenAI Whisper might incur separate costs based on usage.
*   **HyperFrames (by HeyGen)**:
    *   **Role**: An HTML-native motion graphics video workspace. It takes structured data (like the EDL from Video Use) and generates dynamic visual elements, animations, and subtitles. It also handles the final video rendering. (0:18, 1:58, 4:16)
    *   **Cost**: Accessible via a GitHub repo (`heygen-com/hyperframes` and `browser-use/video-use`) which implies an open-source or free-tier model, but complex features or hosting might incur costs. (4:16-4:22)
*   **HeyGen**:
    *   **Role**: Mentioned as a tool for automating raw video recording using AI avatars. While not explicitly used in the demo's main editing loop, it’s presented as a way to fully automate content creation pre-editing. (2:35, 2:43)
    *   **Cost**: HeyGen is a separate paid service. (2:35)
*   **FFmpeg, Chrome, Node, Docker**:
    *   **Role**: These are underlying technologies that HyperFrames CLI (Command Line Interface) uses. FFmpeg for video processing, Chrome/Node for rendering HTML-based motion graphics, and Docker for archival renders. (5:44)
    *   **Cost**: Generally free open-source tools, though Docker might have enterprise pricing.
*   **ElevenLabs API / OpenAI Whisper API**:
    *   **Role**: Used for high-quality speech-to-text transcription, providing precise timestamps for each word. This data is crucial for accurate cutting and syncing motion graphics. (10:30, 10:40)
    *   **Cost**: Both are paid APIs based on usage. (10:39-10:49)
*   **VS Code / Claude Desktop App**:
    *   **Role**: The Integrated Development Environment (IDE) or dedicated app where the user interacts with Claude Code, manages project files, and views code. (3:17, 3:25, 5:19)
    *   **Cost**: VS Code is free. Claude Desktop App requires a paid Claude plan. (3:45)

## 4. THE ACTUAL EDITING TECHNIQUE

1.  **Cutting Filler/Silence**: Claude utilizes a transcription API (like ElevenLabs or OpenAI Whisper) to generate a detailed transcript with word-level timestamps. The "Video Use" skill then analyzes this transcript to identify filler words, long pauses (dead space), and retakes. It constructs an Edit Decision List (EDL) specifying "KEEP" and "CUT" segments. For instance, in the demo, it identifies a "false start" and a "stutter retake" for removal. (10:25, 12:00-12:15) Audio fades of 30ms are applied at each boundary for smooth cuts. (12:16)
2.  **Syncing Motion Graphics**: After the video is trimmed, Claude uses the timestamped EDL/transcript to precisely align motion graphics generated by HyperFrames. The prompt specifies "anchor words" which trigger the start or end of a visual element. For example, a motion graphic might appear when the speaker says "this" at 0.47 seconds. (14:10-14:30, 18:54) This ensures dynamic visuals pop in exactly when relevant speech occurs.
3.  **Rendering**: HyperFrames compositions (HTML/CSS/JS beats) are rendered into a final video file. For efficiency and control, previews can be generated locally (21:47), and a final render involves tools like FFmpeg, potentially leveraging Docker for consistency. (5:44) The output can include a burned-in `.mp4` and a separate `.srt` file for subtitles. (12:58)

## 5. WHAT YOU NEED TO REPLICATE IT

1.  **Claude Account & Paid Plan**: Essential for accessing Claude Code. (3:45)
2.  **Claude Desktop App / VS Code**: Choose your preferred interface. The desktop app is beginner-friendly (3:25).
3.  **HyperFrames Student Kit**: Clone the GitHub repo (`natherk/hyperframes-student-kit`). This kit includes necessary scripts, project structures, and a "Motion Philosophy" document. (4:01)
4.  **GitHub Repos (HyperFrames & Video-Use)**: Claude Code will "learn" from these repos, pulling in skills and information. (4:16-4:22)
5.  **API Keys**: An ElevenLabs or OpenAI API key is needed for transcription. You'll place this in a `.env` file within your project. (10:39, 10:59)
6.  **Local Environment**: A functional development environment capable of running Node.js, FFmpeg, and potentially Docker is required, although Claude Code can assist with some installations. (5:44)
7.  **Skill Level**: While advertised as "beginner friendly" and "no coding required" (0:15), a non-technical person will need a strong understanding of prompt engineering, the ability to read and interpret file paths, and patience for iterative feedback loops with the AI. The hardest part for a non-coder will be initial environment setup, understanding GitHub repos, and crafting very specific prompts to get the AI to produce desired results. (9:47-10:11)

## 6. HONEST FEASIBILITY

The core idea of automating editing with AI is highly feasible and demonstrated effectively. Nate has clearly integrated these tools to work together. If you already have a Claude Code paid subscription and are comfortable with CLI tools or navigating a desktop app like Claude Code, the setup using the provided GitHub repos is straightforward (4:01-4:12). For someone completely new, the initial setup might be daunting, especially installing local dependencies or managing API keys. The value proposition is strong: significant productivity boosts once the workflow is established and trained to your style. The ability to iterate on visual plans (17:18) before full rendering is a huge time-saver and makes it very practical.

## 7. HOW TO USE IT FOR SHORT PROMO ADS

For short promo ads (e.g., 30-second clips):

1.  **Record Raw Footage**: Film your raw promo video. Include intentional pauses for motion graphics. (2:28)
2.  **Ingest & Initial Trim**: Drop the raw `.mp4` into your Claude Code project. Prompt Claude to "Use the `video-use` tool to edit this video. Analyze it, remove filler words, silences, and retakes. Make it as punchy as possible." (6:39-6:59, 12:30)
3.  **Motion Graphics Plan**: Review the trimmed video. Identify key moments where you want visuals. Prompt Claude with specific instructions: "I need you to add motion graphics using HyperFrames to this video. At [timestamp], when I say '[keyword]', pop up a liquid-glass style card on the left half of the screen with karaoke-style text. Make the text of the card '[specific text]'." (14:58-17:12) Repeat for all desired visual elements.
4.  **Iterate on Design**: If the first iteration isn't perfect, use Claude's plan mode to revise. For instance, if a card covers your face, prompt: "In Beat 1, the liquid glass looks good, but it's actually covering my face a little bit. Please scale this down and crop off the right side a little bit so it doesn't cover my face." (23:11-23:25, 24:06-24:08)
5.  **Final Render**: Once satisfied with the preview, confirm with Claude to render the final `.mp4`. (26:09)

## 8. HYPE vs REAL

*   **Hype**: "Claude Just Destroyed Every Video Editing Tool," "No coding required," "No video editing skills required." (0:15)
*   **Real**: While it offers significant automation, it doesn't "destroy" traditional tools as it often *integrates* them (like FFmpeg). "No coding" is true for *using* Claude, but initial setup and advanced customization of HyperFrames components might involve some familiarity with code (5:44, 26:35). "No video editing skills" is also an overstatement; you still need a good eye for timing, aesthetics, and understanding how to effectively *direct* the AI.
*   **Limitations & Manual Steps**:
    *   **Recording** is still manual (2:28).
    *   **Iteration** is key: Claude won't get it perfect on the first try. You'll need to provide clear, specific feedback. (9:47, 22:35)
    *   **Prompt Engineering**: Achieving good results requires highly specific and detailed natural language prompts. This is a skill in itself. (20:41)
    *   **Context Window Limits**: Claude's context window has limits (27:28), which could restrict the complexity or length of videos it can handle in a single session without careful management.
    *   **Costs**: Token usage can add up (27:28), and API keys for transcription services are paid.
    *   **Beginner Stuck Points**: Setting up the environment (cloning repos, installing Node.js, etc.) can be a hurdle. Debugging AI output, especially visual glitches in previews (24:10), can be frustrating without technical know-how.

## 9. THE LOOK / EDIT STYLE

The output style is modern, clean, and highly engaging, leveraging several visual elements:

*   **Cut Rate**: Extremely fast-paced with tight cuts, removing all dead air and filler words, resulting in a very concise and dynamic presentation. (0:38)
*   **Motion Graphics**: Utilizes "liquid glass" style cards that animate smoothly onto the screen. These contain key text, dynamic elements like bar charts or pixelated effects, and often move from left/right or bottom. (0:07-0:10, 7:40-7:43)
*   **Captions**: Karaoke-style, word-by-word reveal of text, perfectly synced to the audio. (0:11, 7:43, 15:24)
*   **Backgrounds/Transitions**: Often features subtle animated wave patterns or abstract textures. Transitions between full-screen facecam and split-screen layouts are smooth and intentional. (8:48-9:07)
*   **Facecam Placement**: Dynamic facecam placement, often shifting from full-screen to a smaller Picture-in-Picture (PIP) view (typically lower-right corner) when motion graphics are on screen. (8:35, 8:48, 20:15)

## 10. CREATOR + VIDEO TITLE

*   **Creator**: Nate Herk, AI Automation Society (`@natherk`, `@AIAutomationSociety`)
*   **Video Title**: "Claude Just Destroyed Every Video Editing Tool"