# Workflow Study: https://www.youtube.com/watch?v=NvxiSG34mPU
_Analysed: 2026-06-03 21:30_

This tutorial video showcases an AI-powered workflow to create "premium," "luxury," and "modern" websites, primarily featuring dynamic background videos. The core idea is to leverage AI (Claude Code and KIE AI's video generation models) to quickly produce visually engaging looping videos and then integrate them into a website structure that is also designed and coded by AI. This aims to significantly reduce the time and cost associated with traditional web development and content creation.

---

## 2. THE END-TO-END WORKFLOW (numbered steps)

The workflow consists of the following steps:

1.  **Set up Development Environment:**
    *   Download and install **Visual Studio Code (VS Code)**.
    *   Install the **Claude Code VS Code extension**.
    *   Log in to Claude Code with an Anthropic API key or Claude Pro subscription.
    *   Open a new project folder in VS Code (e.g., "Seedance Demo").
    *   Create a `.claude` directory within the project folder.

2.  **Acquire Claude Code Skills:**
    *   Join the presenter's "free school community" (implied external platform).
    *   Download the `seedance-loop-prompt` skill folder and drag it into the `.claude` directory. This skill helps craft detailed video prompts.
    *   Install the `frontend-design` plugin globally within Claude Code (via `/plugins` command), which guides Claude Code's web design choices.
    *   (Optional) Drag a `settings.local.json` file (from the free school community) into the `.claude` directory to enable automatic permissions for Claude Code.

3.  **Generate Initial Image (for video background):**
    *   Access the **KIE AI** platform (kie.ai).
    *   Navigate to the "Models Market" and select an "Image Generation" model, specifically "Nano Banana 2".
    *   Provide a text prompt describing the desired background image (e.g., "I need an image of a blueprint. It should look like it is on sketch paper. It should be a skyscraper that is about 75% of the way sketched out").
    *   Set the aspect ratio to 16:9.
    *   Run the generation and download the resulting image (e.g., `blueprint.jpg`).

4.  **Generate Looping Background Video from Image:**
    *   On the **KIE AI** platform, navigate to "Models Market" and select a "Video Generation" model, specifically "Seedance 2.0".
    *   Upload the image generated in Step 3 to both the "first\_frame\_url" and "last\_frame\_url" inputs. This ensures a seamless loop.
    *   Input a detailed prompt for the video (crafted with the help of the `seedance-loop-prompt` Claude Code skill, ensuring explicit instructions for animation, text overlays, and transitions). Example prompt: "Blueprint of a modern skyscraper in blue ink on cream paper... new pencil lines sketch themselves onto the blueprint... camera pushes slowly into the drawing as flat blue lines transform into real steel beams and concrete... text 'Turn your ideas into reality' slides in... Seamless 10-second loop."
    *   Set the video duration (e.g., 10 seconds, matching the prompt's instruction).
    *   Ensure "generate\_audio" is toggled OFF.
    *   Run the generation and download the output video (e.g., `Building Video (2).mp4`).

5.  **Design and Code the Website using Claude Code:**
    *   Drag the generated video (e.g., `Building Video (2).mp4`) into the main project folder in VS Code.
    *   In Claude Code (terminal or extension), prompt it to build the website. Reference the video (`@Building Video (2).mp4`).
    *   Provide high-level instructions for the website:
        *   Hero section: Full-bleed looping video, no separate hero text (as text is in the video).
        *   Overall feel: Trusted, professional, modern.
        *   Sections: Full site (About, Featured Projects, Services, Testimonials, Contact).
        *   Color palette: Light & Minimal.
        *   Branding: No branding yet (Claude Code will create a fictional name).
        *   Impression: Prestigious & established.
        *   Blueprint image: Ignore it for direct site design (it was only for video prompt context).
    *   Claude Code will interactively ask clarifying questions based on the `frontend-design` skill. Answer these questions (e.g., "Create a firm name for me," "Commercial/High-Rise" for architecture type).
    *   Review Claude Code's proposed plan (optional but recommended).
    *   Approve the plan to instruct Claude Code to generate the `index.html` file and other necessary code.

6.  **Deploy the Website:**
    *   Create a new **GitHub repository** (private is recommended during development).
    *   Push the local project folder (containing `index.html`, `Building Video (2).mp4`, etc.) to the GitHub repository.
    *   Go to **Vercel** (vercel.com) and log in, ideally with your GitHub account for easy integration.
    *   Add a new project in Vercel and import the newly created GitHub repository.
    *   Click "Deploy."
    *   Vercel will build and deploy the website, providing a live URL. Any future `git push` to the linked GitHub repository will automatically trigger a re-deployment on Vercel.

---

## 3. EVERY TOOL USED + ITS ROLE

*   **Visual Studio Code (VS Code):**
    *   **Role:** The integrated development environment (IDE) where the user interacts with Claude Code, manages project files, and views generated code.
    *   **Cost:** Free.
*   **Claude Code (VS Code Extension):**
    *   **Role:** An AI agent powered by Anthropic's Claude that assists with code generation, project planning, answering questions, and applying skills. It interprets natural language prompts and generates web development code.
    *   **Cost:** Requires a Claude Pro subscription ($20/month) or an Anthropic API key (pay-as-you-go).
*   **Higginsfield / Seedance 2.0 (via KIE AI):**
    *   **Role:** A multimodal AI model for video generation. It takes images and text prompts to create animated video sequences, crucial for the looping background videos. The seamless looping is achieved by using the same image for the first and last frames.
    *   **Cost:** Accessed via KIE AI's pay-as-you-go credit system. Pricing (720p, with video input) is 25 credits/second ($0.125/s).
*   **KIE AI:**
    *   **Role:** An API platform that serves as an intermediary to access various AI models, including image and video generation models like Nano Banana 2 and Seedance 2.0. It provides a playground interface and API keys for developers.
    *   **Cost:** Pay-as-you-go credit system. Nano Banana 2 costs 18 credits for a 4K image ($0.081).
*   **Nano Banana 2 (via KIE AI):**
    *   **Role:** A Google Gemini 1.5 Flash model for text-to-image generation. Used to create the initial still image that then serves as the basis for the Seedance 2.0 video.
    *   **Cost:** Accessed via KIE AI's pay-as-you-go credit system.
*   **GitHub:**
    *   **Role:** A web-based platform for version control and collaboration. It stores the generated website code and allows for tracking changes. It serves as the source for Vercel deployments.
    *   **Cost:** Free for personal use (including private repositories).
*   **Vercel:**
    *   **Role:** A cloud platform for static sites and serverless functions. It automatically builds and deploys the website from GitHub, making it live and accessible online via a global content delivery network (CDN).
    *   **Cost:** Free for personal/hobby projects.
*   **FFmpeg:**
    *   **Role:** Mentioned by the speaker when explaining a different scroll-animation technique (like the Herk Advisory Group example) to describe extracting video frames. **It is not directly used in the demonstrated website building workflow but is relevant for understanding advanced scroll-linked video techniques.**
    *   **Cost:** Free (open-source software).
*   **GSAP (GreenSock Animation Platform) & CSS `keyframes` + Intersection Observer:**
    *   **Role:** Mentioned as techniques for implementing scroll-triggered fade-in reveals, smooth scroll behavior, navigation transitions, and parallax effects. Claude Code's `frontend-design` skill is implied to leverage these or similar methods.
    *   **Cost:** GSAP has free and paid licenses. CSS `keyframes` and Intersection Observer are free web standards.

---

## 4. WHAT THE FINAL WEBSITES ACTUALLY LOOK LIKE

The "3D/animation" on the final websites, in the primary example built during the tutorial (Aldworth & Partners), is a **pre-rendered AI video** that plays as a full-bleed, continuously looping background in the hero section. This creates a dynamic and immersive visual effect. The video itself transitions from a blueprint sketch to a finished building in a city, with text overlays ("Turn your ideas into reality") seamlessly integrated into the video's timeline.

The quality of the AI-generated video is high (e.g., 720p or 1080p, depending on generation settings), making it look professional and smooth. The overall aesthetic of the generated website, chosen by Claude Code based on the "Light & Minimal" and "Prestigious & Established" prompts, is clean, elegant, and modern, utilizing classic serif fonts, ample whitespace, and subtle fade-in animations for subsequent sections.

For other examples shown in the video's introduction (like the Herk Advisory Group or Apple AirPods Max), the animation technique involves **scrubbing a pre-rendered AI video frame-by-frame based on scroll position**. This creates a powerful, interactive 3D-like experience where scrolling down advances the video's playback, allowing for exploded views, dynamic text reveals, or complex scene transitions precisely tied to user interaction. This particular scroll-linked scrubbing technique is more advanced than the continuous loop demonstrated in the main tutorial, but the speaker confirms Claude Code is capable of it.

The websites look premium due to:
*   **High-quality AI-generated visuals:** The videos are compelling and unique.
*   **Seamless integration:** The video flows well with the overall design.
*   **Modern aesthetic:** Clean layouts, elegant typography, subtle animations, and appropriate color palettes (as guided by the user's prompts).
*   **Dynamic engagement:** The moving backgrounds immediately capture attention and create an immersive feel.

---

## 5. THE SCROLL-ANIMATION TECHNIQUE (be specific)

In the primary example built in the tutorial (the Aldworth & Partners architecture firm website), the hero section's "animation" is a **seamlessly looping HTML5 video element**. Claude Code embeds the `Building Video (2).mp4` file as a `<video>` tag with `autoplay`, `muted`, and `loop` attributes, and styling (e.g., `object-fit: cover`) to make it fill the entire viewport. This video simply plays continuously in the background, independent of scroll, providing a constant dynamic visual.

However, the speaker also refers to more advanced scroll-animation techniques for other examples (like the Herk Advisory Group and Apple AirPods Max sites). For these, the technique described is:
1.  **Frame Extraction:** The original AI-generated video is processed (e.g., via FFmpeg, though not explicitly shown in the tutorial's building phase) to extract individual frames (image sequences).
2.  **Scroll-Linked Playback:** Client-side JavaScript libraries (like **GSAP ScrollTrigger**, mentioned by the speaker, likely combined with Intersection Observer) are used to tie the playback of these video frames directly to the user's scroll position. As the user scrolls down, the JavaScript code advances the displayed frame, giving the illusion of a real-time, interactive 3D animation. Scrolling up reverses the playback.
3.  **Content Association:** Text overlays and other elements are synchronized with specific scroll positions (and thus specific video frames) to create dynamic reveals and transitions.
4.  **Preloading:** For smooth performance, these image sequences or video segments would need to be strategically preloaded or buffered to avoid stuttering during scrubbing.

The `frontend-design` skill in Claude Code is stated to handle these complex animations, implying it generates the necessary HTML, CSS (e.g., `@keyframes`, transitions), and JavaScript (e.g., using GSAP ScrollTrigger or custom scroll event listeners to manipulate video `currentTime` or `src` of image elements).

---

## 6. COSTS + WHAT YOU NEED

**Total Tool/API Cost to Produce One Site (as stated or estimated):**

*   **Claude Pro Subscription:** $20/month (fixed cost, recommended for extensive use over API key).
*   **KIE AI Credits (for image and 10-second 720p video):**
    *   Nano Banana 2 (image): 18 credits (approx. $0.081)
    *   Seedance 2.0 (10s 720p video): 10 seconds * 25 credits/s = 250 credits (approx. $1.25)
    *   **Total KIE AI Cost per site:** ~ $1.33
*   **GitHub:** Free.
*   **Vercel:** Free.

**Overall Cost for the first month (including Claude Pro and one site):** ~$21.33. Subsequent sites in the same month would only incur the KIE AI credit cost (~$1.33 each).

**Which accounts/keys are required:**

*   **Anthropic Account:** (for Claude Code) - requires Claude Pro subscription or API key.
*   **KIE AI Account:** (for image and video generation) - requires account and sufficient credits.
*   **GitHub Account:** (for code hosting and Vercel integration).
*   **Vercel Account:** (for deployment) - typically logs in via GitHub.
*   **VS Code:** Software installed locally.

---

## 7. THE BUSINESS / PRICING CLAIM

**The Business / Pricing Claim:**
The presenter frames the workflow as enabling the creation of "super luxury, super, super professional and very modern" sites, which typically command high prices. He directly references a comparison where traditional production costs for similar creative assets could be "hundreds of thousands of dollars and months of production," contrasting it with a supposed cost of "$99 and 30 minutes with Seedance 2.0." This positions the AI workflow as a massive cost and time-saver, implying that a one-person studio can now deliver high-value, premium websites that clients would traditionally pay "15k" for, at a fraction of the traditional production expense.

**Is that realistic, and for whom?**

*   **Realism of "Hundreds of Thousands" vs. "$99" for Creative Assets:** The claim about drastically reducing the cost and time for *creative asset generation* (specifically the animated videos) is plausible. High-end video production is indeed very expensive and time-consuming. AI tools like Seedance 2.0 can generate impressive visual content for relatively low per-second costs.

*   **Realism of "$15k" for the *Entire* Website:** This claim, while aspirational, is **less realistic for a solo non-coder** to achieve consistently, especially based solely on the automation demonstrated.
    *   **For the AI-generated elements:** Yes, the cost of generating the videos themselves is minimal.
    *   **For the AI-generated website code:** Claude Code provides a solid starting point (`index.html`).
    *   **Missing Human Expertise:** A $15k website typically involves far more than just generating a good-looking front-end. It includes:
        *   **Deep Strategy & UX:** Understanding client business goals, target audience, user journeys, content strategy, and information architecture. This requires human expertise, not just AI prompting.
        *   **Customization & Refinement:** Even with good AI output, clients often demand specific design tweaks, branding consistency, and unique features that would require a skilled front-end developer to implement or a highly proficient prompt engineer to iterate with Claude Code. The presenter himself plays around with prompts to get the right elements, implying iterative human input.
        *   **Backend Integration:** Many $15k+ websites require databases, e-commerce functionality, payment gateways, custom APIs, etc., which are beyond the scope of this frontend-focused workflow.
        *   **Ongoing Maintenance & SEO:** Optimizing for search engines, ensuring accessibility, and continuous updates are critical for a "professional" site but not fully automated here.
        *   **Client Management:** Managing expectations, feedback, and project timelines.

*   **For Whom:**
    *   **Experienced Designers/Developers:** This workflow is highly realistic and valuable for experienced designers and developers. They can leverage the AI for rapid prototyping, content generation, and boilerplate coding, freeing up time for higher-value strategic work, custom features, and client communication. They could genuinely use this to deliver premium sites faster and potentially increase their profit margins.
    *   **Solo Non-Coder:** A non-coder might be able to generate a *basic* site using this method. However, without design sensibility or coding skills, they would likely struggle to:
        *   Craft the precise prompts needed for truly "luxury" video and design (beyond generic).
        *   Iterate on Claude Code's output to match specific client feedback or achieve a truly unique aesthetic.
        *   Handle any technical issues, customize interactive elements, or integrate complex functionalities.
        *   Effectively communicate the value of the AI-generated site to command a $15k price tag, as the value proposition of such a site heavily relies on sophisticated design and functionality.

In summary, the "$15k" framing highlights the *potential value* of delivering such a visually rich site, but realizing that value realistically requires significant human skill in design, development, and client strategy, even with powerful AI assistance. The "AI automation" mainly addresses the raw content and basic code generation, not the full spectrum of high-end web development services.

---

## 8. HONEST FEASIBILITY FOR A SOLO NON-CODER USING CLAUDE CODE

**What is genuinely easy vs. hard here?**

**Genuinely Easy:**

*   **Setup:** Installing VS Code and the Claude Code extension is straightforward.
*   **Basic AI Content Generation:** Using KIE AI's playground to generate an image via Nano Banana 2 and a simple looping video via Seedance 2.0 is user-friendly. The interface is intuitive for uploading and setting basic parameters.
*   **Basic Website Scaffolding:** Claude Code can indeed generate a fundamental `index.html` file based on a simple video and high-level design preferences (e.g., "Light & Minimal"). The interactive Q&A format helps guide even non-technical users through initial decisions.
*   **Deployment:** Vercel's integration with GitHub for basic deployment is highly automated and typically requires minimal technical input after initial setup.

**Hard / Needs Real Skill / Could Break:**

*   **Prompt Engineering for "Premium" Videos:** While basic generation is easy, achieving the *specific, high-quality, and creative* looping video effects shown in the McLaren or even the architecture firm example requires advanced prompt engineering skills. This involves understanding how Seedance 2.0 interprets prompts, incorporating precise details on camera movement, lighting, staging, and text choreography, and iterative refinement. A non-expert might get generic results or struggle to achieve their vision.
*   **Refining AI-Generated Design and Code:**
    *   **Design Taste:** Claude Code (even with the `frontend-design` plugin) relies on the user's input for aesthetic direction. A non-designer might struggle to provide specific, actionable feedback to the AI to achieve a truly "luxury" and "unique" look, or to recognize what adjustments are needed. The presenter makes quick, confident design choices based on experience.
    *   **Code Customization:** The generated output is a raw HTML file. Any significant changes, debugging, or custom feature implementation (e.g., complex interactive elements, integrating specific third-party components) would require real front-end coding skills (HTML, CSS, JavaScript). Claude Code can *edit* code, but directing it to make complex changes efficiently often requires understanding the underlying code structure.
*   **Advanced Scroll Animations (e.g., Herk Advisory / Apple Watch):** The tutorial *shows* these impressive scroll-linked video scrubbing effects but *does not build them in the step-by-step demo*. Implementing these is significantly more complex, requiring frame extraction, careful synchronization with scroll events (likely using JavaScript libraries like GSAP ScrollTrigger), performance optimization (preloading, compression), and robust cross-browser compatibility. A solo non-coder would struggle immensely to build or debug such features if Claude Code's `frontend-design` skill doesn't provide them perfectly out-of-the-box (and even then, refinement would be hard).
*   **Tool / Skill Access:**
    *   **Proprietary Skills and Resources:** The `seedance-loop-prompt` skill and `settings.local.json` are stated to be from the presenter's "free school community." This implies an external dependency and potential gatekeeping or the need to join a specific community.
    *   **KIE AI Limitations:** KIE AI models, like any AI, can be temporarily offline ("This service has been temporarily taken offline" message seen in video). This could interrupt a workflow. There are also character limits on prompts, requiring careful crafting to fit complex instructions.
*   **General IT/DevOps Skills:** While Vercel simplifies deployment, basic understanding of Git (commits, pushes, repositories) and navigating potential issues (e.g., build failures, custom domain setup) would still be necessary. The presenter quickly types `git init`, `git add`, `git commit`, which are fundamental Git commands a non-coder would need to learn.

**What would block someone from doing this today?**

1.  **Cost of AI Tools:** The ongoing subscription for Claude Pro ($20/month) and KIE AI credits ($1.33+ per site) are recurring costs. While seemingly small, they are a barrier if someone expects a truly free solution.
2.  **Lack of Prompt Engineering Expertise:** The ability to consistently generate "premium" AI video content and web designs requires significant skill in crafting precise and iterative prompts. Non-experts will likely produce suboptimal or generic results.
3.  **Limited Web Development Skills:** For anything beyond basic boilerplate, a non-coder would be blocked from customizing the generated HTML/CSS/JS, adding specific features, or debugging issues effectively. The AI is a powerful assistant, but it doesn't eliminate the need for *any* technical understanding for professional outcomes.
4.  **Access to Specific Resources:** The need to join an external "free school community" for essential Claude Code skills and settings could be an initial hurdle.
5.  **Performance and Optimization:** Ensuring the scroll animations are smooth, responsive across devices, and performant (especially with larger video files) requires expertise in web optimization, which is not trivial.