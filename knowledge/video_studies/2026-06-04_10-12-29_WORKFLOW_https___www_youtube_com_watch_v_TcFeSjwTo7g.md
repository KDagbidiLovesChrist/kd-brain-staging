# Workflow Study: https://www.youtube.com/watch?v=TcFeSjwTo7g
_Analysed: 2026-06-04 10:12_

This tutorial video showcases an AI workflow for rapidly transforming static websites or fresh ideas into dynamic, interactive, and visually rich web experiences. The core idea is to leverage various AI tools to automate the design, content generation, and particularly the scroll-linked animation of website elements, delivering a polished, "premium" feel. The presenter claims this workflow allows a single individual to build such sites quickly, with a focus on an engaging user journey.

---

## 2. THE END-TO-END WORKFLOW (numbered steps)

The workflow progresses through several stages, from conceptualization to deployment:

1.  **Idea & Brand Specification (Claude chat):**
    *   Start with a high-level idea for a website and its purpose (e.g., a wellness brand for a nightly wind-down drink).
    *   Prompt Claude chat to generate a detailed brand specification, including:
        *   Product description and unique selling points.
        *   Positioning and brand voice.
        *   Visual identity (color palette with hex codes, typography/fonts, imagery style).
        *   Detailed site structure (hero section, subsequent content sections, footer) with actual copy suggestions.
2.  **Background Image & Video Generation (Claude chat + KIE.AI Seedance 2.0):**
    *   Prompt Claude chat to generate an image prompt and a corresponding video prompt for the hero section's background. The video prompt specifies a seamless loop, static camera, and specific atmospheric motion (e.g., steam from a mug).
    *   Input the image prompt into KIE.AI's Seedance 2.0 (image generation) to create the static background image, ensuring a 16:9 aspect ratio.
    *   Input the generated image (as both start and end frames) and the video prompt into KIE.AI's Seedance 2.0 (video generation) to create a loopable, subtly animated background video.
3.  **Website Design & Iteration (Claude Design):**
    *   Create a new "High fidelity" prototype in Claude Design.
    *   Optionally, start with a basic sketch within Claude Design to outline the hero section's layout (e.g., video background on the right, text panel on the left, navigation bar).
    *   Upload the generated background video (MP4) to Claude Design.
    *   Provide Claude Design with the comprehensive brand specification (text, colors, fonts, layout descriptions) from step 1, referencing the sketch and the uploaded video.
    *   Claude Design generates the initial website based on the provided context.
    *   **Interactive Tweaking:** Use Claude Design's "Tweaks" panel (sliders and dropdowns) for real-time adjustments to palette, accent hue, display font, headline size/case, hero layout, video dim/grain overlay, section rhythm, card styles, and more.
    *   **Direct Edits:** Use the "Comment" or "Edit" functions within Claude Design to highlight specific elements on the live preview and request targeted changes (e.g., change button color, modify text, adjust spacing). Claude Design processes these requests contextually.
4.  **Exporting the Code (Claude Design):**
    *   Once satisfied with the design in Claude Design, select "Share" and "Download project as .zip" to export the entire website as a downloadable ZIP file containing HTML, CSS, JavaScript, and assets.
    *   Alternatively, use the "Handoff to Claude Code" option, which provides a command to fetch the design directly into Claude Code (though the presenter notes issues with this specific command at the time of recording).
5.  **Local Development & GitHub Push (VS Code + Claude Code):**
    *   Open the exported ZIP file in a local code editor like VS Code.
    *   Utilize the Claude Code extension within VS Code.
    *   Prompt Claude Code to push the project to a new (private) GitHub repository. This involves Claude Code interacting with your linked GitHub account to create the repository and commit the files.
    *   Request Claude Code to open the site in a local HTTP server (localhost) for preview and final checks, especially after manual changes.
6.  **Deployment to the Web (Vercel):**
    *   Create an account on Vercel and link it to your GitHub account.
    *   In Vercel, select "Add New Project," then "Import Git Repository," choosing the GitHub repository created in the previous step.
    *   Vercel automatically detects the project and offers to deploy it. Click "Deploy."
    *   (Crucial Debugging Step): If the deployment fails (e.g., 404 error because Vercel expects `index.html` but the file is named `lull-website.html`), prompt Claude Code in VS Code to rename the HTML file to `index.html` and push this change to GitHub. Vercel will automatically redeploy.
    *   Once deployed, Vercel provides a live public URL for the website.
7.  **Mobile Optimization (Further Iteration):**
    *   Test the live website on mobile devices or use developer tools to simulate mobile view.
    *   Identify responsiveness issues (e.g., text wrapping, element placement).
    *   Return to Claude Design (or Claude Code directly) and explicitly prompt for mobile optimization, specifying desired changes (e.g., "optimize for mobile," "rearrange hero section for small screens"). This might involve further iterations and consumption of session limits.

---

## 3. EVERY TOOL USED + ITS ROLE

*   **Claude Design (claude.ai/design):**
    *   **Role:** The primary AI tool for visual website design. It ingests brand specifications, text content, sketches, and media files to generate high-fidelity prototypes. It offers interactive "Tweaks" (sliders/toggles for colors, fonts, layouts, animations) and direct editing/commenting capabilities on the visual canvas for iteration.
    *   **Cost:** Needs a paid plan (Pro, Max, Team, Enterprise). Not free. Pro is $20/month.
*   **Claude chat (claude.ai):**
    *   **Role:** Used as a conversational assistant for initial brand specification, generating specific image and video prompts (text-to-image/video). Also used to clarify instructions for Claude Design and to prompt Claude Code.
    *   **Cost:** Part of the Claude API pricing. Opus 4.7 is the most expensive model. Presenter mentions spending $200+ on extra usage for prompts.
*   **KIE.AI Seedance 2.0 (kie.ai/seedance):**
    *   **Role:** An AI image and video generation platform (powered by ByteDance). Used to create the static background image from a text prompt and then animate that image into a loopable video based on a detailed video prompt.
    *   **Cost:** Paid API. The presenter notes spending over $200 in "extra usage" just playing around, implying per-generation or token-based pricing.
*   **MotionSites.ai:**
    *   **Role:** A gallery and library of animated backgrounds and website templates. Used for inspiration and to potentially obtain prompt ideas for backgrounds/layouts.
    *   **Cost:** Offers free resources; presenter mentions a $99 lifetime membership for full access.
*   **VS Code (with Claude Code extension):**
    *   **Role:** The Integrated Development Environment (IDE) where the actual code files (HTML, CSS, JS) are managed. The Claude Code extension acts as an AI coding agent within the IDE, capable of reading, writing, and executing code, and interacting with Git repositories.
    *   **Cost:** VS Code is free. Claude Code extension is part of the Claude API (paid).
*   **GitHub (github.com):**
    *   **Role:** A web-based platform for version control and collaborative software development. Used to store the website's code repository. Claude Code pushes the local project files to GitHub.
    *   **Cost:** Free for public repositories; private repositories may require a paid account (though basic private repos are often free now).
*   **Vercel (vercel.com):**
    *   **Role:** A cloud platform for developers to deploy web applications and static websites. It integrates with GitHub for continuous deployment. Used to host the final website and make it accessible via a public URL.
    *   **Cost:** Free hobby tier available; paid plans for professional use.

---

## 4. WHAT THE FINAL WEBSITES ACTUALLY LOOK LIKE

The final websites look premium and highly interactive. The "3D/animation" is not real-time 3D (like WebGL/Three.js). Instead, it's a **pre-rendered AI video** (or an image sequence) that is dynamically scrubbed frame-by-frame as the user scrolls.

*   **Technique:** The background often features a static scene (like floating islands, a steaming mug, a person working in space) with subtle, continuous motion (e.g., steam rising, stars twinkling). This video is generated using text-to-video AI.
*   **Quality:** The visual quality is high-resolution (3x image resolution, 2,576px long edge as mentioned for Opus 4.7). The animations are smooth due to the frame-by-frame scrubbing.
*   **Premium Feel:** This is achieved through:
    *   **Dynamic Backgrounds:** Moving backgrounds immediately elevate the visual appeal over static images.
    *   **Parallax Scrolling:** Elements in the foreground (text, content cards) scroll at a different rate than the background video, creating a sense of depth and immersion.
    *   **Content Cards:** Interactive, 3D-like cards (sometimes with subtle hover effects or pop-ups) appear dynamically as the user scrolls, presenting information in an engaging way.
    *   **Curated Typography & Color Schemes:** Claude Design helps select aesthetically pleasing fonts and color palettes that fit the brand's mood (e.g., dark, warm, tactile for "Lull" brand).
    *   **Seamless Transitions:** The smooth animation of background video and dynamic appearance of content sections create a cohesive "journey" for the user.

---

## 5. THE SCROLL-ANIMATION TECHNIQUE (be specific)

The scroll-animation technique relies on **pre-rendered video assets** and tying their playback to the user's scroll position.

1.  **Video Generation:** A key asset is a short, loopable background video (e.g., 8-second clip of a steaming mug). This video is generated by AI (KIE.AI Seedance 2.0) with specific prompts ensuring:
    *   **Static Camera:** No camera movement whatsoever (no pan, zoom, tilt, drift, parallax).
    *   **Seamless Loop:** The start and end frames are identical for smooth looping.
    *   **Controlled Motion:** Only specific elements are animated (e.g., steam rising from a mug, light flicker, subtle liquid shimmer).
    *   **Resolution:** High resolution for visual quality.
2.  **Integration in Claude Design:** Claude Design is instructed to use this video as a background. The crucial part for scroll-animation is that Claude Design then *associates each frame of the video with a specific scroll position*. This is implied by the presenter's description of how the AI Automation Society website (which uses this technique) was built by "telling it to only associate each frame with a scroll position so that as I scroll down or up the video goes forwards or reverses."
3.  **Frame Scrubbing:** As the user scrolls down the page, the website displays subsequent frames of the pre-rendered video. Scrolling up reverses the video playback. This creates a visual effect where the background "moves" or "evolves" in direct response to the user's scroll input, giving the impression of a guided journey through the site's content.
4.  **Content Overlay & Parallax:** Static or dynamically appearing content cards/text are overlaid on top of this animated background, often with their own entrance animations (fade-ins, pop-ups) and sometimes with slight parallax effects to enhance depth.

Essentially, it's not generating new frames in real-time based on scroll, but rather "scrubbing" through a pre-existing video sequence.

---

## 6. COSTS + WHAT YOU NEED

To replicate this workflow for a single site, the costs and requirements are:

*   **Claude Design:** Requires a paid tier. The Pro tier is **$20/month**. The presenter notes "1 session total. 30 minutes of real use ate 80% of weekly quota" on the Pro tier, indicating usage limits. Higher tiers (Max 5x, Max 20x, Team/Enterprise) are more expensive ($100/month, $200/month respectively).
*   **KIE.AI (Seedance 2.0):** Paid API. The presenter notes spending "$225.37 spent" on extra usage in a month just playing around, suggesting significant costs if many image/video generations are needed. No exact per-generation cost is stated in the video.
*   **MotionSites.ai:** Optional, but useful for inspiration. Offers a **$99 lifetime membership**.
*   **GitHub:** A free account is sufficient for basic repository hosting. For private repositories, the free tier usually offers enough now, but advanced team features might require paid plans.
*   **Vercel:** Free hobby tier is sufficient for hosting personal/small projects. More extensive usage or enterprise features would require paid plans.
*   **VS Code:** Free to download and use.
*   **Claude Code Extension:** Part of the Claude API, so paid usage of Claude chat translates here.

**Total Tool/API Cost (Estimated):**
*   **Upfront:** If purchasing MotionSites.ai ($99) and consuming KIE.AI usage (e.g., $200), it's around **$300**.
*   **Monthly:** Claude Design Pro ($20/month) + potential ongoing KIE.AI usage.

**Required Accounts/Keys:**
*   Anthropic API key (for Claude chat, Claude Design, Claude Code).
*   KIE.AI API key (for Seedance 2.0).
*   GitHub account.
*   Vercel account.

---

## 7. THE BUSINESS / PRICING CLAIM

The presenter frames this workflow with the potential for a "small one-person studio" to build "premium" websites in "20 minutes" (for the design transformation) and implies high value. While the video doesn't explicitly state a "$15k" price for *these specific* AI-generated sites, the presenter's previous content and general framing of AI automation often involve targeting high-ticket clients or services. The implication is that this AI-powered workflow allows a solo builder to produce results comparable to traditional web design agencies, potentially commanding premium prices.

**Is that realistic, and for whom?**
*   **Realistic for *some* aspects:** The *speed of prototyping* and generating aesthetically pleasing layouts/animations is significantly increased. A skilled designer/developer who *already* commands premium rates for their overall services could leverage this to increase their output, reduce turnaround time, and thus boost their effective hourly rate.
*   **Unrealistic for *a non-coder* to solely rely on for $15k sites:** While the AI does a lot of heavy lifting, achieving a *truly* polished, fully functional, mobile-optimized, accessible, SEO-friendly, and maintainable website for a $15k client often requires human expertise in:
    *   **Advanced UX/UI:** Beyond basic layouts.
    *   **Custom Features:** AI-generated code is a starting point, but bespoke features need coding.
    *   **Debugging & Edge Cases:** AI-generated code will likely have bugs, especially with complex interactions or responsiveness.
    *   **Performance Optimization:** Ensuring fast loading times and smooth performance.
    *   **Accessibility (ADA compliance):** Crucial for many clients.
    *   **Advanced SEO:** Beyond just content, includes technical SEO.
    *   **Client Management & Revisions:** Handling specific client demands that might break the AI's current capabilities.

Therefore, the "$15k" framing is likely realistic for someone who can *integrate* this powerful AI prototyping/generation into a broader skillset that includes traditional web development, design refinement, and project management. For a solo non-coder, it's a powerful tool for *prototyping* and *idea validation*, but selling a fully polished, high-value product would require substantial learning or collaboration.

---

## 8. HONEST FEASIBILITY FOR A SOLO NON-CODER USING CLAUDE CODE

**Genuinely Easy:**
*   **Initial content generation:** Claude chat excels at generating text, brand voice, and content outlines based on high-level prompts.
*   **Visual tweaking with sliders:** Claude Design's "Tweaks" panel allows for easy, real-time adjustments of colors, fonts, spacing, and basic layout without any coding. This is genuinely user-friendly.
*   **Direct text editing:** The ability to click and edit text directly in Claude Design's preview is straightforward.
*   **Getting a basic working prototype:** The core steps of providing spec, generating assets, and having Claude Design create a first iteration are very fast and accessible.

**Hard / Could Break / Needs Real Skill or Paid Tools:**
*   **KIE.AI Prompt Engineering for Video (Real Skill):** Creating precise, loopable, high-quality, and aesthetically consistent images and videos (especially with specific animated elements like steam) from text prompts is an advanced skill. The presenter likely has significant experience here. Inconsistent video generation or difficulty getting a perfect loop would significantly degrade the "premium" feel.
*   **Cost (Specific Paid Tool):** Claude Design is *not free*. This is a hard blocker for someone expecting a free workflow. KIE.AI usage can quickly accumulate costs.
*   **Debugging (Real Skill/Blocker):** The presenter encounters a deployment bug (`404 not found` due to incorrect HTML filename for Vercel). While Claude Code *helps* debug by identifying the cause and suggesting the fix (renaming `lull-website.html` to `index.html`), understanding *why* this happens and effectively applying the fix within a terminal (even with AI assistance) requires basic familiarity with web development and Git concepts. A complete non-coder could be blocked here.
*   **Mobile Optimization (Real Skill + Iteration):** Claude Design does not *automatically* optimize for mobile responsiveness. It requires explicit prompts and further iterations. This means more token usage, more time, and the need for a non-coder to have a good eye for mobile UX/UI, even if they're not writing the CSS.
*   **"Long Agentic Threads" (Skill/Cost):** The presenter highlights that lengthy AI conversations ("long agentic threads") consume session limits rapidly. Effectively managing the conversation, breaking down complex tasks, and providing precise instructions to avoid unnecessary AI computation is a skill.
*   **Integrating Complex Interactions (Real Skill):** For features beyond simple scroll-linked video, a non-coder would eventually hit limits. Building custom forms, dynamic data fetching, e-commerce integrations, or complex user interactions would likely require actual coding expertise.
*   **Not a Figma Replacement (Limitation):** The tool is in "research preview" and lacks features like version control and multiplayer editing common in professional design tools like Figma. This makes collaborative work or tracking complex design history challenging.
*   **Reverting Changes (UI Limitation):** The presenter notes a lack of a clear "revert" button within Claude Design, meaning if an iteration goes wrong, it might be difficult to go back efficiently without starting a new project or using Git directly (which again, implies coding knowledge).
*   **"Opus 4.7 tokenizes about 35% faster":** This means costs can quickly escalate during iterative design, potentially leading to frequent interruptions if budget is tight.

In summary, for a solo non-coder, this workflow is an incredible leap for *prototyping and visualizing ideas rapidly*. However, successfully deploying a *production-ready, bug-free, mobile-optimized* premium website requires either a steep learning curve in fundamental web development concepts (HTML, Git, deployment) to navigate the rough edges of an AI research tool, or the budget to hire a developer to handle those aspects. It’s a powerful *accelerator* for those with some coding/design knowledge, but a less stable *replacement* for those without.