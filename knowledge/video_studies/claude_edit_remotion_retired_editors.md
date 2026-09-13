# remotion_retired_editors
https://www.youtube.com/watch?v=oWkUwno6b0E

Here is a precise, actionable, and honest breakdown of the video tutorial on using AI for video editing and motion graphics:

## 1. ONE-PARAGRAPH SUMMARY + the "wow"

This tutorial demonstrates a workflow that combines **Claude AI** (a conversational AI assistant) with **Remotion** (a programmatic video tool) to *semi-automate* the creation of motion graphics for video editing. The "wow" factor is the promise of **significantly accelerating the video editing process** by having AI generate visually complex motion graphics based on a simple script. This means reducing days of manual motion graphics creation to hours, improving content quality and enabling faster video output and growth for creators.

## 2. END-TO-END WORKFLOW

The workflow is broken down into several parts, seamlessly integrating AI generation with traditional video editing tools:

1.  **(00:03 - 00:06) The Problem & The Solution Intro**: The creator introduces the pain point of manual motion graphics creation and then reveals "Claude" as the solution, implying an AI tool will handle this.
2.  **(01:00 - 01:26) Part 1: Claude's Correct Setup**:
    *   **User Action**: The user is instructed to install four prerequisites for Claude to function:
        1.  Claude Desktop App (Downloaded from `claude.ai/download`)
        2.  Git for Windows (Downloaded from `git-scm.com/download/win`) - This is essential for Claude Code to work.
        3.  Node.JS (Downloaded from `nodejs.org/en`) - Necessary for Remotion (the "skill" being installed later) to run.
        4.  Claude Chrome Extension (From the Chrome Web Store) - For managing tabs and workflow.
    *   **AI/System Role**: These are foundational tools required for Claude and its associated skills to operate locally on the user's machine.
    *   **Output**: All four applications/extensions are installed and correctly configured on the user's computer.
3.  **(01:55 - 02:20) Part 2: Installing Remotion**:
    *   **User Action**:
        1.  Goes to `remotion.dev`.
        2.  Copies the `npx create-video@latest` command.
        3.  In Claude's chat, types "install this skill" and pastes the command.
        4.  Follows up with "let me know when it's done."
    *   **AI Action (Claude + Node.JS)**: Claude executes the `npx create-video@latest` command, which uses Node.JS to install Remotion. It then prompts the user to select a project folder and a template.
    *   **Output**: Claude confirms successful installation of Remotion, potentially asking for a project folder and a template choice. The creator selects "3D" for experimentation.
4.  **(03:00 - 04:55) Part 3: Enhance Claude (Instructions & Resources)**:
    *   **User Action**: The user creates a new folder (`LEARN V1`) containing two subfolders: `Resources` and `Skill`.
    *   **User Action**: Inside the `Resources` folder, the user places several `.docx` files:
        *   `1. Text Style`: Guidelines for headings (bold, premium, tight spacing, Poppins Extrabold font).
        *   `2. Scene Composition`: Rules for motion graphics (translate script meaning into visuals, use minimal UI, visual metaphors, icons, timelines, etc.; *not* word-for-word subtitles).
        *   `3. Scene Revision & Versioning Behavior`: A workflow for handling changes (duplicate scenes, create new versions, don't overwrite).
        *   `4. CREATIVE_UNLOCK_RULE_SIMPLE`: Permission for Claude to think beyond literal sentences and use creative metaphors/structure.
        *   Fonts (e.g., Poppins Bold, Poppins SemiBold).
        *   `REVISION PROMPTS (this is for me - ignore)`: A personal prompt for the creator.
    *   **User Action**: Inside the `Skill` folder, the user places the `SKILL.md` (Antigravity protocol) file.
    *   **AI Role**: These documents serve as prompt engineering instructions, guidelines, and an AI "skill" to direct Claude's behavior and enhance its output.
    *   **Output**: A structured project folder with specific stylistic and behavioral guidelines for Claude.
5.  **(06:55 - 08:43) Part 4: Activate Claude Boosts (Installing Antigravity Skill & Teaching Resources)**:
    *   **User Action**:
        1.  In Claude's chat, the user first "sets" the main project folder (`LEARN V1`) by pasting its path.
        2.  Instructs Claude: "First - Install and activate antigravity protocol skill. Let me know when it is complete and what you are enhanced now."
        3.  Instructs Claude: "Read the content in Resources Folder. Learn it. Tell me when you are done."
    *   **AI Action (Claude + Antigravity Skill)**: Claude installs the Antigravity protocol (a custom skill for token efficiency and strict modes). It then reads and internalizes the content of the four `.docx` files in the `Resources` folder, confirming what it has learned.
    *   **Output**: Claude is "enhanced" with strict modes (Investigatory, Fast Path, Planning) and a prioritized tool workflow, along with understanding the text style, scene composition rules, versioning behavior, and creative unlock rules.
6.  **(08:43 - 10:50) Part 5: How to Open Remotion**:
    *   **User Action**: The user navigates back to `remotion.dev/templates`, selects the "3D" template, and then types "Open Remotion" in Claude.
    *   **AI Action (Claude + Remotion)**: Claude launches Remotion Studio in the default browser (Chrome, thanks to the extension). The selected template (`React Three Fiber starter composition`) is loaded.
    *   **Output**: Remotion Studio is running locally at `localhost:3000`, displaying a blank scene or the selected template.
7.  **(10:50 - 14:15) Part 6: Generate Motion Graphics (from a Script)**:
    *   **User Action**: The user drops a prepared `.docx` video script (`3 Reasons MrBeast Has Mastered The Art of Retention`) into the project folder.
    *   **User Action**: In Claude's chat, the user instructs: "I added a script to the folder. [path to script]. Read it - Then draft out scenes for a the script." (And later, changes the "creative direction lock" for more varied outputs).
    *   **AI Action (Claude + Remotion + Skills)**: Claude reads the script, applies the learned "Text Style", "Scene Composition", "Creative Unlock Rule", and "Antigravity Protocol" to draft detailed scene descriptions (concept, visuals, text, motion feel, labels, timing). It then generates the motion graphics for these scenes using Remotion, exporting them as MP4 files.
    *   **Output**: A series of MP4 video files (e.g., 20 scenes, 1080p resolution) are generated and saved in an `out` folder within the project, perfectly timed with the spoken words from the script.
8.  **(14:27 - 15:58) Part 7: Render the Scenes (into Editing Software)**:
    *   **User Action**: The user imports the generated MP4 scenes into a video editing software (DaVinci Resolve is used).
    *   **User Action**: The user manually marks timestamps in DaVinci Resolve on their main speaking track (e.g., using markers for "Scene 1," "Scene 2").
    *   **User Action**: The user drags and drops the generated MP4 motion graphic scenes from the `out` folder onto the timeline in sync with the markers.
    *   **Output**: A rough edit of the video with motion graphics aligned to the script.
9.  **(15:58 - 20:26) Part 8: Add Scenes to Your Video (Post-Production)**:
    *   **User Action**: The user refines the integration in DaVinci Resolve by:
        1.  Aligning motion graphics precisely with audio (using markers).
        2.  Adding transitions (e.g., "Push" effect) between motion graphic clips.
        3.  Adjusting clip durations and removing small gaps.
        4.  Adding background music.
    *   **Output**: A polished video combining the speaker's footage with dynamically animated motion graphics, ready for final review.
10. **(20:53 - 21:18) Part 9: Revise Scene Layouts (for Facecam)**:
    *   **User Action**: The user provides a "REORIENTATION FITTING (LEAVING SPACE FOR WEBCAM)" prompt to Claude (from the `REVISION PROMPTS` doc). They specify a scene number (e.g., "Scene 13") and a screen division (e.g., "left 35% side of the screen only").
    *   **AI Action (Claude + Remotion)**: Claude re-generates the specified motion graphic scene, automatically adjusting its layout to fit the specified screen area (e.g., leaving space for a facecam).
    *   **Output**: A revised MP4 motion graphic scene, repositioned to accommodate a facecam or other on-screen elements, without manually scaling or cropping in the editing software.
11. **(21:18 - 23:18) Part 10: Remove the Background (Green Screen)**:
    *   **User Action**: The user provides a "BACKGROUND REMOVAL (GREEN SCREEN)" prompt to Claude. They specify the scene number to apply it to.
    *   **AI Action (Claude + Remotion)**: Claude re-generates the motion graphic scene with a pure green background (`#00FF00`), ensuring no gradients, shadows, or textures that would hinder greenscreen removal. It also converts UI elements, panels, cards, and overlays to solid/opaque colors that are *not* green, facilitating clean keying.
    *   **User Action**: In DaVinci Resolve, the user applies the `3D Keyer` effect to the greenscreened clip.
    *   **Output**: A greenscreened motion graphic clip that is easily keyed in editing software, making the background transparent and allowing it to overlay other footage.
12. **(25:05 - 26:54) Part 11: Add Images into Remotion**:
    *   **User Action**: The user gathers images (e.g., MrBeast-style thumbnails generated by ChatGPT) and places them into a `pngs` folder within the project.
    *   **User Action**: In Claude's chat, the user instructs: "Now remove the text on the phone. And select one image to be on the phone for each slide. Images are in this folder [path to pngs folder]."
    *   **AI Action (Claude + Remotion)**: Claude, using its creative judgment and access to the image folder, integrates the specified images directly into the motion graphic scenes displayed on the phone screen elements.
    *   **Output**: Motion graphics with custom images embedded, adding specific visual context beyond what Remotion natively generates.

## 3. EVERY TOOL + ROLE + COST

*   **Claude Desktop App**: Primary AI interface, executes commands, manages sessions. (Subscription-based AI, Anthropic's Claude.ai, costs vary by model and usage.)
*   **Git for Windows**: Provides the Bash environment for Claude Code commands. (Free, open-source).
*   **Node.JS**: JavaScript runtime environment, required for Remotion to function. (Free, open-source).
*   **Claude Chrome Extension**: Facilitates workflow switching between browser and Claude Desktop. (Free, provided by Anthropic).
*   **Remotion**: Programmatic video creation tool (likely running locally via Node.JS) that generates motion graphics based on code/instructions. (Open-source, free for local use, but cloud rendering would incur costs).
*   **FFmpeg**: (Implied, not explicitly mentioned in the tutorial as a direct user interaction, but is often used by Remotion or underlying processes for video encoding/decoding). (Free, open-source).
*   **DaVinci Resolve**: Professional video editing software. (Free version available, Studio version is paid).
*   **ChatGPT**: Used by the creator to generate MrBeast-style thumbnail images for demonstration. (Free version available, Plus subscription is paid).
*   **Local Machine**: All local software runs on the user's computer.

**Cost Summary**: Claude is a paid AI service (e.g., Claude Pro). Remotion is open-source and free to run locally, but cloud rendering would have costs. Git and Node.JS are free. DaVinci Resolve has a powerful free version. ChatGPT has free and paid tiers. The main costs would be Claude subscription and potentially high-performance hardware or cloud rendering for complex Remotion projects.

## 4. THE ACTUAL EDITING TECHNIQUE

*   **Script-to-Scene Generation**: Claude reads a raw script (`.docx` format) and, guided by the provided "Resource" documents (text style, scene composition, creative unlock rules), drafts detailed scene descriptions.
*   **Motion Graphics Creation**: Using these detailed scene descriptions and Remotion, Claude generates individual motion graphic clips (`.mp4` format, often 1080p or 4K) where visual elements (text, icons, animations) are synchronized with the script's content.
*   **Token Efficiency**: The "Antigravity Protocol" skill teaches Claude "token wisdom," allowing it to generate 3-4x more scenes per session by optimizing its "thinking" process, reducing token waste, and avoiding verbose output. This directly impacts usage limits and efficiency.
*   **Versioning**: Claude's scene versioning rule dictates that instead of overwriting an edited scene, it duplicates the original and creates a new version (e.g., "Scene 2 V2"), making it easy to track revisions and revert if needed.
*   **Visual Interpretation**: The "Scene Composition" rule instructs Claude to *translate the meaning* of the script into visuals, rather than simply replicating word-for-word subtitles. It emphasizes minimal UI, visual metaphors, icons, and timeline animations.
*   **Rendering**: The generated scenes are rendered locally as individual MP4 files by Claude via Remotion.
*   **Editing Software Integration**: The user manually brings these pre-rendered motion graphic clips into their preferred video editing software (e.g., DaVinci Resolve).
*   **Synchronization**: The user manually places markers on their original video timeline to indicate where each motion graphic scene should be inserted, then drags and drops the generated clips to match these markers.
*   **Dynamic Layouts**: Claude can reorient motion graphics to fit specific screen regions (e.g., leaving 35% of the screen for a facecam) without manual scaling in the editor. This is achieved by precise prompt engineering (`"redesign the motion graphics to sit on the left 35% side of the screen only..."`).
*   **Background Removal (Green Screen)**: Claude can generate motion graphics with a pure green background, converting all elements to solid colors (non-green) for easy chromakeying in video editing software.
*   **Image Integration**: Claude can embed custom images (e.g., user-provided PNGs) into the motion graphics, allowing for highly customized visuals beyond text and abstract shapes.

## 5. WHAT YOU NEED TO REPLICATE IT

1.  **Accounts/API Keys**:
    *   **Claude Account**: Access to Claude's AI models (requires subscription for continuous use beyond free tier).
    *   **Remotion**: While open-source, continuous cloud rendering might require specific accounts or setup (not explicitly detailed as paid, but implied for heavy use).
    *   **ChatGPT/Midjourney/DALL-E**: (Optional, for generating custom images/thumbnails, potentially paid subscriptions).
2.  **Software Installation**:
    *   **Claude Desktop App**: For direct interaction with the AI.
    *   **Git for Windows**: Essential for running Claude Code scripts (ensure it's installed and path is correctly set).
    *   **Node.JS**: Runtime environment for Remotion (ensure correct version and npm/npx are working).
    *   **Claude Chrome Extension**: For browser-based workflow efficiency.
    *   **Video Editing Software**: DaVinci Resolve (free version), Adobe Premiere Pro, Final Cut Pro, etc.
3.  **Local Project Setup**:
    *   **Structured Folder**: A main project folder (e.g., `LEARN V1`) with `Resources` and `Skill` subfolders.
    *   **Resource Documents**: The `.docx` files containing Text Style, Scene Composition, Scene Revision/Versioning, and Creative Unlock rules. These are critical for guiding Claude's output. (Available in the video description for download).
    *   **Skill Files**: The `SKILL.md` for Antigravity Protocol (from Kingstar Omega's GitHub, linked in description).
    *   **Video Script**: Your original video script in `.docx` format.
    *   **Custom Images**: (Optional) PNG images you wish to integrate into the motion graphics.
4.  **Skill Level**:
    *   **Non-coder**: The creator suggests this is replicable for non-coders, but installing Git Bash and Node.JS can be a challenge if encountering common setup errors (as highlighted by the creator himself in the video with comments on his troubleshooting video). Understanding environment variables might be required.
    *   **Prompt Engineering**: A good understanding of how to craft clear, concise, and detailed prompts is crucial, especially when applying "creative unlock rules" or requesting specific revisions.
    *   **Basic Video Editing**: Familiarity with your chosen video editor (importing, cutting, markers, transitions, chromakeying) is necessary for assembly and final polish.

**Hardest Part for a Non-Coder**: The initial setup of **Git for Windows** and **Node.JS**, and ensuring they are correctly configured with environment variables, can be the most daunting step. While the creator provides troubleshooting videos, this often requires command-line interaction which can be unfamiliar.

## 6. HONEST FEASIBILITY

This workflow is **honestly feasible** for significantly speeding up the *motion graphics creation phase* of video editing, particularly for short promotional ads. It successfully leverages AI to automate tasks that are typically very time-consuming and skill-intensive.

*   **Overlaps**:
    *   **Claude Code + FFmpeg**: The integration of Claude Code with underlying tools like Remotion and implicitly FFmpeg (for rendering) is effective. Claude acts as the orchestrator, translating natural language prompts into executable commands for Remotion.
    *   **Remotion (owned)**: If a user already understands Remotion's programmatic approach, Claude simplifies the coding aspect by generating the underlying code or executing commands. If a user does *not* know Remotion, Claude offers a powerful entry point to leverage it without extensive coding.
*   **New Things Needed**:
    *   **Effective Prompt Engineering**: This is not just about typing commands but learning *how* to instruct Claude effectively using the provided "Resource" documents. This is a new skill for many and requires practice.
    *   **Custom AI Skills**: The "Antigravity Protocol" and similar custom skills are key to optimizing Claude's performance for this specific task. These need to be downloaded and correctly placed.
*   **Worth It?**: For a one-person studio aiming to produce a high volume of visually engaging content (especially short-form like promo ads) without hiring a dedicated motion graphic designer, this workflow is **absolutely worth the initial learning curve and setup time**. It allows for rapid iteration and significantly boosts output capacity and quality.

## 7. HOW TO USE IT FOR SHORT PROMO ADS

This workflow is perfectly suited for generating short promo ads. Here's how:

1.  **Script your Ad**: Write a concise script (e.g., 30-60 seconds) highlighting key benefits or calls to action.
2.  **Enhance Claude**: Use the provided "Resource" documents to teach Claude your desired brand style (fonts, colors, animation feel) and creative direction (e.g., "fast-paced, exciting, product-focused visuals"). The "Creative Unlock Rule" is key here to allow Claude artistic freedom.
3.  **Generate Scenes**: Provide your ad script to Claude, instructing it to draft scenes with motion graphics. For example, "Draft 10 scenes for a 30-second promo ad. Use bold, high-impact text. Translate calls to action into dynamic icons. Ensure smooth, fast transitions between visuals."
4.  **Incorporate Custom Images**: Use the image integration feature to add product shots, branding elements, or testimonial images directly into the motion graphics.
5.  **Adapt for Platforms**: If creating vertical ads for social media, use the reorientation prompt to ask Claude to redesign scenes to fit a "top 50% of screen" or "bottom 50% of screen" layout, leaving space for other UI elements or your speaking head.
6.  **Review and Refine**: Quickly generate several versions of scenes or entire short ads. The versioning system allows for easy comparison and iteration. Ask Claude for revisions (e.g., "Make Scene 3 more energetic," "Change the font in Scene 5 to a sans-serif style").
7.  **Final Edit**: Drop the greenscreened/transparent MP4 motion graphics into your video editor, overlay them on your footage, and add any final touches, music, and sound effects.

## 8. HYPE vs REAL

*   **Hype**: "I manually never have to create motion graphics like this ever again." (00:01) "Days of my life come back to me as it edits my videos for me and creates these beautiful motion graphics." (00:08) "I have retired from that part of my workflow." (00:28)
*   **Reality**: While the *manual creation* of individual motion graphics is largely retired, the process still requires significant **manual oversight, creative direction, and refinement**.
    *   **Manual Steps**: Initial software setup, ongoing prompt engineering (especially for complex or nuanced visuals), reviewing generated scenes, managing file versions, and final assembly/editing in a traditional video editor are all human tasks.
    *   **Hidden Costs**: Claude is a paid AI. While Remotion is open-source, advanced features or large-scale cloud rendering would likely incur costs not detailed in the video. The "token wisdom" aims to *reduce* these costs, indicating they exist.
    *   **Where a Beginner Gets Stuck**:
        1.  **Technical Setup**: Installing Git Bash and Node.JS, configuring environment variables, and troubleshooting command-line issues can be intimidating for non-coders.
        2.  **Effective Prompting**: Crafting clear, detailed, and iterative prompts that align with the AI's capabilities and your vision requires practice. Misunderstandings lead to irrelevant outputs.
        3.  **Creative Oversight**: The AI generates, but the human directs. Knowing *what* looks good, *what* to ask for, and *how* to refine the AI's output is still a creative skill.
        4.  **Editing Software Skills**: While the AI handles graphic creation, integrating, timing, and refining these clips in a video editor still requires basic editing proficiency.

## 9. THE LOOK / EDIT STYLE

The output of this workflow, as demonstrated, results in a **modern, clean, and dynamic infographic style** well-suited for explainer videos and online content.

*   **Cut Rate**: Fast-paced, designed for high retention, often changing visuals with each sentence or key phrase.
*   **Motion Graphics**: Primarily text-based animations, icons, visual metaphors, floating cards, timeline animations, and simple diagrams. They are visually engaging and translate spoken words into clear, concise graphical representations. The "Creative Unlock Rule" pushes for more dynamic and visually compelling compositions rather than static text.
*   **Captions**: The initial video showcases burned-in captions, which the AI is instructed *not* to simply recreate, but to interpret visually.
*   **B-roll**: Not directly generated by the AI in this tutorial, but the motion graphics are designed to overlay existing footage (like the speaker's facecam), adding a layer of visual interest.
*   **Transitions**: Simple, effective transitions are used between motion graphic scenes (e.g., a "push" transition in DaVinci Resolve).
*   **Color Palette/Typography**: Guided by the "Text Style" and implied design rules, the output features a cohesive color palette (e.g., dark backgrounds, orange/blue accents, off-white text) and specific fonts (e.g., Poppins ExtraBold) for high impact.

## 10. CREATOR + VIDEO TITLE

*   **Creator**: Chronixel Studios
*   **Video Title**: CLAUDE AI + REMOTION. This is How To Master Motion Graphics. (Full Course)