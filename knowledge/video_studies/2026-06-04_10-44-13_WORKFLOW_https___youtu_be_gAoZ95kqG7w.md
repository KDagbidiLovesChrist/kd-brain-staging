# Workflow Study: https://youtu.be/gAoZ95kqG7w
_Analysed: 2026-06-04 10:44_

This tutorial video showcases Anthropic's new **Claude Design** platform, powered by **Claude Opus 4.7**, demonstrating an AI workflow for generating visually coherent and interactive web designs. It emphasizes leveraging a pre-defined brand design system and existing codebases to produce prototypes, slide decks, and landing pages with minimal manual coding.

---

## 1. ONE-PARAGRAPH SUMMARY

This workflow produces branded, functional web prototypes, slide decks, and landing pages by first setting up a comprehensive design system within Claude Design, including brand guidelines, logos, and a linked codebase. Users then provide natural language prompts and answer clarifying questions, allowing Claude to generate designs that adhere to the established brand identity. The core idea is to streamline the design process, making it accessible to non-designers and designers alike, and enabling seamless hand-off to Claude Code for further development and deployment into a full-fledged, animated website.

---

## 2. THE END-TO-END WORKFLOW (numbered steps)

1.  **Set Up Design System (in Claude Design):**
    *   Provide a company name and blurb (e.g., "AI Automation Society", "AI Automation Made Easy").
    *   Link to an existing GitHub repository containing the project's codebase (e.g., `nateherkai/AI-Automation-Society-Website`).
    *   Optionally, upload local code files (though not explicitly done for this step in the video, it's an option).
    *   Upload brand assets: fonts (e.g., specific TTF/OTF files), logos (PNG/SVG), and brand guidelines (PDF). The video shows uploading `AIS Brand Guidelines-1.png` and `AIS Logo PNG.png`.
    *   Add any other notes about brand voice or specific design preferences (e.g., "Our brand should feel techie but also modern and professional").
    *   Claude Design then processes these inputs to build out a comprehensive design system (colors, typography, spacing, components, etc.). This step takes about 15 minutes.

2.  **Generate a Project (e.g., Slide Deck or Landing Page):**
    *   Choose a project type (e.g., "Slide Deck" or "Prototype" for a landing page).
    *   Name the project (e.g., "AI Time" for a slide deck, "First Agent Promo" for a landing page).
    *   Ensure the previously created design system is selected as the default.
    *   Provide context: attach additional screenshots, codebases, or directly drop files (e.g., a PDF document).
    *   Provide a natural language prompt describing what you want to create (e.g., "turn that PDF into a branded presentation for me," or a detailed request for a workshop landing page).

3.  **Iterate and Refine within Claude Design:**
    *   **For Slide Decks:** Claude extracts content and structure from the provided document, generating individual slides. Users can then navigate through the slides.
    *   **For Landing Pages:** Claude engages in a conversational Q&A process to gather more specific details about the workshop (name, dates, times, audience, key takeaways, page sections, CTA copy, design variations, desired vibe).
    *   Utilize in-platform tools:
        *   **Tweaks:** Adjust specific design elements using sliders or options (e.g., change accent color, show/hide countdowns, toggle sticky CTA bars).
        *   **Comment:** Add comments directly to specific elements on the design or slide for feedback.
        *   **Edit:** Manually change properties like background color, font size, weight, alignment, opacity, padding, borders, and radii.
        *   **Draw:** Draw directly on the design to highlight areas for modification, which Claude interprets (e.g., drawing a circle and typing "I don't like this" prompts Claude to make changes).

4.  **Export or Hand-off to Claude Code:**
    *   Once satisfied with the design, select "Export."
    *   Options include: Download project as .zip, Export as PDF, Export as PPTX, Send to Canva, Export as standalone HTML, or "Hand-off to Claude Code."
    *   Selecting "Hand-off to Claude Code" generates a CLI command that fetches the design file via an Anthropic API endpoint.

5.  **Implement and Deploy (using Claude Code and external tools):**
    *   Open a local development environment (e.g., VS Code) with the Claude Code extension installed.
    *   Paste and execute the generated "Hand-off to Claude Code" command.
    *   Claude Code will fetch the design bundle, read its `README`, extract assets, colors, and type CSS, and integrate it into the specified project structure (e.g., an existing React website).
    *   Claude Code then runs local build commands (e.g., `npm run dev`) to start a development server, allowing a live preview of the integrated landing page (e.g., on a subdomain like `localhost:5173/first-agent`).
    *   The user would then push the updated project to GitHub for version control and deployment to a live web server (e.g., Vercel, Netlify).

---

## 3. EVERY TOOL USED + ITS ROLE

1.  **Claude Design by Anthropic Labs:**
    *   **Role:** The primary web-based platform for managing design systems, generating design assets (colors, typography, components), and creating prototypes, slide decks, and one-pagers through natural language prompts and iterative feedback. It serves as the visual authoring environment.
    *   **Cost:** Requires a paid Claude subscription (Pro, Max, Team, or Enterprise). Rough cost for Claude Pro is $20/month. No separate API key explicitly shown for Claude Design itself, but it uses Anthropic's models.

2.  **Claude Opus 4.7 (Anthropic's LLM):**
    *   **Role:** The underlying large vision model that powers Claude Design. It interprets natural language prompts, analyzes design resources, generates visual designs, answers clarifying questions, and processes feedback for iterative refinement. Its enhanced visual reasoning capabilities are central to Claude Design's functionality.
    *   **Cost:** Included with Claude Design access via a Claude subscription. Pricing for Opus API usage (which Claude Design and Code likely leverage) varies by token count (e.g., $15 per million input tokens, $75 per million output tokens for Opus).

3.  **Claude Code (Anthropic's AI Coding Agent):**
    *   **Role:** A coding agent (typically run within a VS Code extension) that takes design specifications from Claude Design and implements them into a functional codebase. It reads existing project structures, integrates new design elements, handles routing, and builds/runs the project locally. It also understands Git operations.
    *   **Cost:** Included with Claude Design access via a Claude subscription. API usage costs would apply similarly to Claude Opus.

4.  **GitHub:**
    *   **Role:** Used as a repository for the project's codebase and brand assets. Claude Design reads the GitHub repo to understand the existing brand and code structure. Claude Code (post-handoff) integrates generated designs into this repo for version control and eventual deployment.
    *   **Cost:** Free for public repositories, paid tiers available for private repositories and team features.

5.  **VS Code (Visual Studio Code):**
    *   **Role:** The integrated development environment (IDE) where Claude Code is run as an extension. It provides the terminal interface for interacting with Claude Code commands and browsing the generated or modified project files.
    *   **Cost:** Free.

6.  **`npm` (Node Package Manager) and `Vite` (Build Tool):**
    *   **Role:** `npm` is used to execute development scripts (e.g., `npm run dev`) to start a local web server for previewing the website. `Vite` is likely the underlying build tool and development server, inferred from the `localhost:5173` port typically used by Vite and commands shown in the Claude Code terminal.
    *   **Cost:** Free.

7.  **PDF Parsing Library (e.g., `pdf-parse`):**
    *   **Role:** An internal skill invoked by Claude to read and extract content from PDF documents uploaded by the user, enabling the creation of slide decks from existing reports. The video shows `cdn.jsdelivr.net/npm/pdf-parse@2.4.5` being used.
    *   **Cost:** Presumably integrated into Claude's skills, so no direct cost to the user beyond Claude API usage.

8.  **Canva:**
    *   **Role:** An external graphic design platform mentioned as an export option, indicating potential interoperability for further editing or use of designs generated by Claude Design.
    *   **Cost:** Has free and paid tiers. Its role here is as an export destination, not a core tool in the generation process.

9.  **FFmpeg:**
    *   **Role:** Not used or mentioned in the video. The animations shown (rotating globe, shader wallpapers, text particle effects) appear to be real-time interactive animations, not pre-rendered video frames.

10. **GSAP (GreenSock Animation Platform):**
    *   **Role:** Not explicitly used or mentioned in the video's direct demonstration. However, the examples of "shader wallpapers" and "text particle effects" could technically be achieved using GSAP for intricate JavaScript-based animations, especially when combined with WebGL/Three.js for the "3D" and "shader" aspects. Given the tool's capabilities, it's possible such libraries are either integrated or the AI can generate code that uses them.

11. **Vercel (or similar hosting service):**
    *   **Role:** Not explicitly mentioned but is the standard platform for deploying modern frontend projects (like the one generated) to a live URL, especially when using GitHub for version control. The speaker implies this by mentioning pushing to GitHub for deployment.
    *   **Cost:** Free tier available for personal projects, paid tiers for advanced features and team collaboration.

---

## 4. WHAT THE FINAL WEBSITES ACTUALLY LOOK LIKE

The final websites generated by this workflow, and the examples showcased, aim for a **premium, modern, and interactive aesthetic** consistent with the provided brand guidelines.

*   **Visual Style & Quality:** The generated slide deck and landing page feature a dark theme, sleek typography (matching the user's brand fonts, despite initial "missing fonts" warnings), glowing buttons, and well-structured layouts. The overall look is professional and aesthetically pleasing.
*   **"3D/Animation":** The "3D" and "animation" aspects are **real-time and interactive**, not pre-rendered video.
    *   **Rotating Globe (initial Twitter video):** This appears to be a **real-time 3D rendering** (likely using WebGL/Three.js) with dynamic, glowing paths connecting points on the globe, reacting to user input (mouse hover).
    *   **Shader Wallpapers & Text Particle Effects (Claude Design Examples):** These are described as "interactive" and likely leverage WebGL shaders or advanced CSS/JavaScript animations for dynamic visual effects that respond to user interaction (e.g., mouse position).
*   **Smoothness & Responsiveness:** The demos suggest smooth transitions and interactive elements. The generated landing page for the workshop is a fully functional web page, implying it would be responsive across devices, although this is not explicitly demonstrated in detail.
*   **"Premium" Look:** The combination of a meticulously enforced design system (colors, fonts, spacing, components), dynamic interactive elements, and sophisticated visual effects (like glows and subtle animations) contributes to a premium feel that often requires significant design and development effort to achieve manually.

---

## 5. THE SCROLL-ANIMATION TECHNIQUE (be specific)

The video **does not explicitly show the code or technique for tying motion to scroll** for the complex "animated websites." However, based on the examples and capabilities described:

*   **Real-time Interaction:** The examples like "Shader wallpapers" and the rotating globe clearly indicate **real-time interactive graphics**, rather than pre-rendered video played on scroll.
*   **Techniques (Inferred):**
    *   **WebGL/Three.js:** For the complex "shader wallpapers" and "3D" elements like the rotating globe, **WebGL libraries like Three.js** would be the likely underlying technology. These allow for GPU-accelerated graphics that can be dynamically controlled by JavaScript.
    *   **JavaScript & CSS Animations:** For simpler UI elements, **CSS transitions/animations** combined with **JavaScript** could be used.
    *   **GSAP ScrollTrigger (Hypothesized):** If intricate scroll-tied motion is desired (like elements revealing or transforming at specific scroll points), a library like **GSAP (GreenSock Animation Platform) with its ScrollTrigger plugin** is a very common and powerful solution in professional web development. While not explicitly mentioned or demonstrated, Claude's ability to generate complex UI code makes the generation of GSAP-powered animations plausible if specifically prompted for.
    *   **No FFmpeg/Canvas Image Sequences:** There is no evidence in the video to suggest the use of **FFmpeg for frame extraction** or **canvas `drawImage` for scrubbing image sequences** for scroll-based video animation. The focus is on real-time, interactive graphics and dynamically generated UI components.
    *   **Preloading:** For WebGL or complex interactive elements, efficient **asset preloading** (textures, models, shaders) is crucial, and the generated code would likely incorporate this to ensure smoothness.

Essentially, the AI generates the HTML, CSS, and JavaScript that implements these real-time, dynamic effects, allowing for interactive and branded experiences.

---

## 6. COSTS + WHAT YOU NEED

**Total Tool/API Cost (Estimated for one site):**

*   **Claude Pro Subscription:** ~$20/month (required for Claude Design access). API usage for Opus 4.7 is included in the subscription or billed separately depending on usage, but for a single site generation, it's likely covered or negligible under a standard plan.
*   **GitHub:** Free for public repositories.
*   **VS Code, NPM, Vite:** Free.
*   **Web Hosting:** Free tiers exist for services like Vercel or Netlify for basic deployment. A custom domain typically costs $10-20/year.
*   **Total Estimated Cost (minimum, excluding high-volume API usage or advanced hosting):** ~$20/month for Claude Pro + $10-20/year for a custom domain.

**Required Accounts/Keys:**

1.  **Anthropic/Claude Account:** A paid subscription (Pro, Max, Team, or Enterprise) to access Claude Design and Claude Code.
2.  **GitHub Account:** To link repositories, store code, and manage deployment.
3.  **Local Development Setup:**
    *   VS Code (or compatible IDE) installed.
    *   Claude Code extension for VS Code installed.
    *   Node.js and npm installed (for running the local server and managing dependencies).

---

## 7. THE BUSINESS / PRICING CLAIM

The user's prompt mentions a "$15k framing," but **the video does not explicitly state a $15k pricing claim for building a website.**

However, the video implicitly positions Claude Design and Claude Code for **high-value, professional-grade design and development work.** This is inferred from:

*   **Enterprise Features:** Claude Design is available for "Claude Pro, Max, Team, and Enterprise subscribers," suggesting a tool for professional teams and businesses.
*   **Complex Use Cases:** Examples like "in-store touchscreen kiosks, mobile apps, and websites" (mentioned during design system setup) and "autonomous, cloud-scheduled trading agent" (the subject of the slide deck PDF) indicate the tool is geared towards complex, integrated, and valuable projects.
*   **Time and Efficiency Savings:** The core value proposition is significantly reducing the time and manual effort required for design and frontend development, especially for maintaining brand consistency. By automating repetitive tasks, designers and developers can focus on higher-level problem-solving, which translates to cost savings or faster project delivery, allowing for potentially higher project value/pricing.
*   **"Agent-first approach":** The reference to building a "First AI Agent" workshop and "Claude is the bot" suggests an AI-driven development paradigm where the AI itself is a key component, enabling advanced functionalities.

**Is it realistic?**
For **large enterprises or complex custom applications**, a $15k valuation for a high-fidelity, branded, interactive website or application *is* realistic, and often conservative. The ability of Claude Design/Code to rapidly generate and integrate these elements, while maintaining brand consistency, would indeed command a premium price due to the accelerated time-to-market and reduced human-resource hours.

For a **small one-person studio**, using this tool could enable them to take on more complex projects than previously possible, justifying higher pricing. However, commanding $15k *per site* would depend heavily on the actual complexity, integrations, and ongoing services provided, not solely on the tool's capabilities. It *lowers the barrier to entry* for creating premium designs, potentially increasing earning potential.

---

## 8. HONEST FEASIBILITY FOR A SOLO NON-CODER USING CLAUDE CODE

**What is genuinely easy:**

*   **Design System Setup (Initial):** Uploading logos, brand guidelines, and basic company information is straightforward. Claude's ability to interpret a PDF brand guideline document and extract colors/fonts is powerful for establishing consistency quickly.
*   **Natural Language Interaction:** The conversational interface for generating initial designs, asking clarifying questions, and iterating using text-based prompts (e.g., "turn that PDF into a branded presentation," or answering specific Q&A for a landing page) is genuinely easy and intuitive.
*   **Visual Tweaks:** The "Tweaks" panel allows non-technical users to make quick, impactful visual changes (colors, countdowns, CTA visibility) without touching code.
*   **Collaborative Feedback:** The "Comment" and "Draw" features facilitate easy visual feedback loops, making it simple to convey changes to the AI.
*   **Basic Content Extraction:** Claude's ability to read a PDF and structure its content into a presentation is a significant time-saver.

**What is genuinely hard, needs real skill, or could break:**

*   **"Missing Brand Fonts" Error:** The video shows an persistent "Missing brand fonts" warning, with Claude rendering substitute web fonts. While the speaker claims his uploaded brand guidelines *do* include typography, Claude Design fails to correctly interpret or apply them. This is a critical block for achieving a truly "premium" and on-brand look without manual intervention. A non-coder would struggle to fix this without knowing how to upload custom font files in a specific format or debug font loading issues.
*   **"Internal Error" in Claude Code:** The brief "chat upstream error: agent: sse scan failed: stream error" encountered during PDF processing, even with automatic retries, highlights potential instability in the "research preview" phase. A non-coder would have no way to diagnose or resolve such issues if they persist.
*   **Debugging Code Hand-off:** While "Hand-off to Claude Code" generates a command, a non-coder interacting with a command-line interface (CLI) to execute bash scripts, manage file paths (e.g., `/tmp/design_bundle`), and understand `npm run dev` might be intimidating. If there are integration conflicts or unexpected behavior in the generated code, debugging in VS Code requires actual coding knowledge.
*   **Advanced Customization Beyond Tweaks:** The "Tweaks" panel is great for predefined options. However, if a design requires significant structural changes, integration of complex third-party APIs (beyond what Claude's "skills" can handle), or truly unique interactive elements not covered by direct prompts, a non-coder will hit a wall and require a developer.
*   **Placeholder Images/Assets:** The generated landing page initially featured a placeholder image for the instructor, which Claude Code automatically replaced from the linked GitHub repo. However, if specific imagery or more nuanced asset handling is required, a non-coder might need to manually intervene or provide more explicit instructions/file structures to Claude. The "Logo is PNG only -- no SVG" caveat indicates limitations in asset optimization.
*   **Performance ("My poor PC"):** The speaker's comment about PC lag indicates that running Claude Design (especially during generation) or even the local preview might be resource-intensive, potentially affecting user experience on less powerful machines.
*   **Understanding Generated Code:** While the goal is to reduce coding, the "Hand-off to Claude Code" ultimately produces code. To truly "own" and maintain the website, or to make changes not covered by Claude Design's GUI, understanding the generated React/HTML/CSS/JS is essential. This transitions the solo non-coder into needing at least basic coding skills.
*   **Deployment Workflow:** While Claude Code helps set up the project locally, the final step of deploying to a live server (e.g., configuring CI/CD on Vercel from GitHub) still requires some technical understanding that is outside the scope of a pure "non-coder" workflow.

**In summary:** Claude Design significantly lowers the barrier for *design ideation and prototyping* for non-coders, enabling them to create visually consistent and rich designs. However, the "Hand-off to Claude Code" still requires a level of comfort with developer tools and concepts (CLI, Git, local servers), and *true coding skill* would be necessary to debug issues, perform deep customizations, or fully leverage the advanced animation capabilities implied by the examples, especially for production-ready, premium animated websites. For a solo non-coder, it's a powerful *design assistant*, but not yet a complete *no-code deployment solution* for complex, custom projects.