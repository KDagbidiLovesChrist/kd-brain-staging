# Website Study: ref1.mp4
_Analysed: 2026-06-08 18:07_

Here's a precise breakdown of the website's look and feel, designed for recreation:

## 1. ONE-LINE VIBE
Premium cinematic architectural showcase with seamless scroll-driven visual narratives and elegant typography.

## 2. THE HERO (first screen)
The centerpiece is a full-screen, high-resolution visual narrative of a luxury tropical villa. It starts with an inviting interior view looking out through wide-open glass doors to an infinity pool and lush palm trees.
*   **Content:**
    *   **Visual:** A beautifully rendered (or filmed) interior shot of a modern living space with minimalist furnishings, leading the eye directly to the bright outdoor pool area and tropical landscape.
    *   **Text:** A large, elegant serif text overlay "Welcome." appears centrally.
    *   **Navigation:** A clean, minimalist top navigation bar with text links: "VELLORA - ESTATES", "HOMES", "STUDIOS", "JOURNAL" (and likely a "CONTACT" or "TOUR" link on the far right, partially obscured).
    *   **Indicator:** A subtle "SCROLL" text is visible at the bottom center.
*   **Motion:** The "Welcome." text subtly fades in. The camera itself performs a very slow, deliberate dolly movement, inching forward slightly, subtly drawing the viewer into the scene.

## 3. SCROLL BEHAVIOUR (most important)
The core interaction is a scroll-scrubbed, continuous camera animation through the luxury property. The entire visual section appears to be sticky/pinned while the user scrolls, effectively scrubbing through the pre-rendered animation.

*   **0:01 - 0:02:** Initial hero (interior view). Scrolling down initiates a continuous camera dolly forward from the interior. "Welcome." text fades out.
*   **0:02 - 0:04:** The camera continues its forward motion, passing *through* the open glass doors, showcasing the infinity pool and the immediate outdoor lounging area. The perspective transitions from inside to fully outside, looking across the pool.
*   **0:04 - 0:05:** As scrolling continues, the camera smoothly pulls further back and slightly up, revealing the full exterior facade of the modern villa, including the surrounding landscaping and garage. This is a dramatic reveal.
*   **0:06 - 0:09:** Scrolling *up* reverses the entire animation perfectly: the camera dollies back towards the house, then through the pool area, and finally back into the interior view, at which point the "Welcome." text fades back in. This confirms the frame-by-frame scrub technique.
*   **0:09 - 0:11:** Scrolling down again, the sequence plays out: interior -> pool view (with "Here you won't count the days." text overlay appearing) -> full exterior view (with "For the few who notice." text overlay appearing).
*   **Summary:** It's a continuous, smooth camera path pre-rendered into an image sequence or video. As the user scrolls, they scrub through this sequence. Text overlays are timed to appear and disappear at specific scroll points/frames, acting as chapter titles or key messages for each part of the visual journey. The motion feels like scrubbing a video frame-by-frame, perfectly synchronized with scroll input.

## 4. IS IT REAL-TIME 3D OR A SCRUBBED VIDEO/IMAGE-SEQUENCE?
My best judgment is that this is a **pre-rendered video/image-sequence scrubbed on scroll** (the "Apple product page" technique).
*   **Clues:**
    *   **Photorealism:** The incredible detail, complex lighting, and realistic foliage/water reflections are characteristic of high-quality architectural renderings, which are difficult to achieve in real-time WebGL with consistent performance across devices.
    *   **Fixed Camera Path:** The camera movement is exceptionally smooth and follows a highly choreographed, continuous path. While possible in WebGL, it often points to a pre-rendered animation.
    *   **Lack of Interactivity:** There are no discernible real-time 3D interactions like object manipulation, dynamic lighting changes, or different camera angles other than the scroll-driven scrub.
    *   **Performance vs. Detail:** Pre-rendering allows for maximum visual fidelity without burdening the client's GPU with real-time rendering of such a complex scene.

## 5. MOTION FEEL
The scroll is incredibly **smooth, weighted, and buttery**. It feels continuous and fluid, making the scrubbing experience highly cinematic. There's no choppiness or abrupt transitions. The overall pace is slow and deliberate, enhancing the luxury and grandeur of the architecture. The text reveals also exhibit a subtle, controlled fade-in/fade-out, likely with an easing function.

## 6. LAYOUT & SECTIONS
The video primarily showcases the hero section, which functions as a multi-stage visual narrative.
*   **Hero Section (Primary Visual Storytelling):** This is a full-viewport, sticky/pinned container that drives the scroll-scrub animation.
    *   **Scene 1: Interior Welcome (approx. 0-20% scroll depth):** Shows the interior, text "Welcome.".
    *   **Scene 2: Pool & Outdoor Living (approx. 20-60% scroll depth):** Camera moves through to the pool, text "Here you won't count the days." appears.
    *   **Scene 3: Exterior Reveal (approx. 60-100% scroll depth):** Camera pulls back to reveal the full house exterior, text "For the few who notice." appears.
*   **Navigation:** A fixed or sticky header with the brand name "VELLORA - ESTATES" (left) and menu items "HOMES", "STUDIOS", "JOURNAL" (right).
*   **Scroll Indicator:** A subtle "SCROLL" text at the bottom of the initial hero view.
*   *(Implied subsequent sections):* While not shown, typical luxury real estate sites would follow with sections like: About the Property, Features/Amenities, Gallery, Floor Plans, Contact/Schedule a Tour, and Footer.

## 7. COLOUR + TYPOGRAPHY
*   **Palette:**
    *   **Dominant:** A sophisticated blend of warm, natural neutrals (light beige, cream, natural stone tones, deep wood browns) for the architecture and interiors.
    *   **Accents:** Vibrant natural greens from tropical foliage and a striking turquoise/blue from the pool and sky provide visual contrast.
    *   **Text:** Primarily white or very light grey for high contrast against the rich visuals.
    *   **Approx HEX (Educated Guess):**
        *   Stone/Wall: `#EAE4DA`, `#D1C7B8`
        *   Wood: `#5C4A3F`, `#3B2C24`
        *   Pool/Sky: `#5BBAD5`, `#3D9DD6`
        *   Foliage: `#4D6D47`, `#2C4F2A`
        *   Text: `#FFFFFF`
        *   Navigation text/accents: Dark grey `#222222` or `#1A1A1A`.
*   **Typography:**
    *   **Hero Text Overlays ("Welcome.", "Here you won't count the days.", "For the few who notice."):** An elegant serif typeface (e.g., Playfair Display, Lora, Ibarra Real Nova), light to regular weight, generous letter-spacing, and large, impactful sizing. It exudes classic luxury.
    *   **Navigation / Smaller UI Text:** A clean, modern geometric sans-serif (e.g., Montserrat, Inter, Poppins), regular weight, standard to slightly open letter-spacing, and appropriate sizing for readability. This provides a contemporary counterpoint to the serif.
    *   **Overall:** A deliberate and harmonious blend of classic serif for expressive headlines and clean sans-serif for functional elements, contributing to the site's premium feel.

## 8. THE SIGNATURE PREMIUM MOVE
1.  **The Scroll-Scrubbed Cinematic Visual Narrative:** The continuous, high-fidelity camera journey from inside to outside the luxurious villa, directly controlled by the user's scroll, is the ultimate premium feature. It creates an immersive, explorable storytelling experience that is incredibly engaging and visually stunning.
2.  **Immaculate Architectural Photorealism:** The quality of the visuals (whether rendered or filmed) is exceptional, showcasing the property with magazine-level perfection in lighting, textures, and composition. This dedication to visual excellence screams high-end.
3.  **Elegant & Contextual Text Overlays:** The use of a refined serif font for key messages, perfectly timed to appear and disappear in sync with the visual journey, adds an editorial, curated layer to the experience. It feels deliberate and enhances the narrative without being intrusive.

## 9. RECREATE RECIPE (for the 'AI clip scrubbed on scroll' workflow)

This plan outlines how to rebuild this look using an AI-generated cinematic hero clip.

1.  **AI-Generated Cinematic Hero Clip (15-20 seconds, 30fps):**
    *   **Prompt Idea:** "A smooth, cinematic drone shot that starts inside a luxurious, minimalist tropical villa living room with large glass doors opening to an infinity pool, slowly dollies forward through the doors over the pool, then gracefully pulls back to reveal the entire modern architectural exterior of the villa against a clear blue sky, surrounded by lush palm trees. Hyperrealistic, detailed, sunny, 8K, architectural visualization, serene, slow motion, professional cinematography."
    *   **Clip Length & Frames:** Aim for a 15-20 second clip. At 30fps, this yields 450-600 frames, providing ample scroll distance for a smooth scrub.

2.  **FFmpeg Frame Extraction:**
    *   Extract every frame from the generated MP4 clip into a numbered image sequence (e.g., `frame_001.jpg`, `frame_002.jpg`, ..., `frame_600.jpg`).
    *   Command: `ffmpeg -i input_ai_clip.mp4 -vf fps=30 frame_%03d.jpg`

3.  **Front-End Implementation (Preload, Canvas, Scroll Scrub):**
    *   **HTML Structure:**
        ```html
        <div id="hero-sticky-wrapper" style="position: sticky; top: 0; height: 100vh; overflow: hidden;">
            <canvas id="hero-canvas" style="width: 100%; height: 100%; display: block;"></canvas>
            <nav id="main-nav" style="position: absolute; top: 0; width: 100%; z-index: 10;"></nav>
            <div id="text-overlays" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; display: flex; align-items: center; justify-content: center; z-index: 5;">
                <h1 class="text-overlay welcome-text" style="opacity: 0;">Welcome.</h1>
                <h2 class="text-overlay pool-text" style="opacity: 0;">Here you won't count the days.</h2>
                <h2 class="text-overlay exterior-text" style="opacity: 0;">For the few who notice.</h2>
            </div>
            <div class="scroll-indicator" style="position: absolute; bottom: 20px; left: 50%; transform: translateX(-50%); opacity: 1; z-index: 5;">SCROLL</div>
        </div>
        <div id="scroll-trigger" style="height: [TOTAL_SCROLL_HEIGHT_PX]px;"></div> <!-- This invisible div creates the scrollable space -->
        <!-- Subsequent content sections below -->
        ```
    *   **JavaScript Logic (with a Smooth Scroll Library like Lenis):**
        *   **Image Preloading:** Asynchronously load all 450-600 `frame_XXX.jpg` images into an array of `Image` objects. Implement a loading screen until all images are ready.
        *   **Canvas Drawing:** On each `scroll` event (or `lenis.on('scroll')` event), calculate the `scrollProgress` (0 to 1) of `#scroll-trigger`.
            *   `scrollProgress = (lenis.scroll - document.getElementById('hero-sticky-wrapper').offsetTop) / document.getElementById('scroll-trigger').offsetHeight;`
            *   Map `scrollProgress` to an image index: `frameIndex = Math.floor(scrollProgress * (numberOfFrames - 1));`
            *   Draw `images[frameIndex]` onto `hero-canvas`.
        *   **`TOTAL_SCROLL_HEIGHT_PX`:** Set this to a value that allows for a comfortable scrub, e.g., `numberOfFrames * 10px` (4500-6000px) or `3-4 * window.innerHeight`. Adjust based on desired scroll speed per frame.
        *   **Text Overlay Timing (controlled via scrollProgress):**
            *   `.welcome-text`: `opacity` from `1` (at `0%`) to `0` (at `20%`).
            *   `.pool-text`: `opacity` from `0` (at `25%`) to `1` (at `30%`), then `0` (at `60%`).
            *   `.exterior-text`: `opacity` from `0` (at `65%`) to `1` (at `70%`), then `0` (at `100%`).
            *   Use GSAP or similar for smooth opacity transitions with easing.
        *   **Scroll Indicator:** Fade `SCROLL` out after initial scroll (e.g., `scrollProgress > 0.05`).

4.  **Premium Components & Smooth Scroll:**
    *   **Smooth Scroll Library:** Integrate `lenis` (or similar) for an ultra-smooth, weighted scroll feel that enhances the cinematic scrubbing.
    *   **Navigation:** `fixed` or `sticky` navigation bar. Left: "VELLORA - ESTATES" (serif, slightly larger). Right: "HOMES", "STUDIOS", "JOURNAL" (sans-serif, uppercase, good letter-spacing).
    *   **Loading State:** A minimal, elegant loading animation or percentage counter while images preload.

5.  **Section Build Order (Subsequent Content):**
    *   **Hero Section (Scroll-Scrubbed):** As described above.
    *   **About/Philosophy:** Full-width hero image with an elegant overlay text, followed by rich text content. Use generous padding and whitespace.
    *   **Property Highlights:** A grid of 2-3 key features, each with a high-quality image, a bold serif heading, and a concise sans-serif description.
    *   **Gallery:** A full-width, responsive image slider or grid, showcasing different aspects of the property.
    *   **Interactive Floor Plans:** Clean, simple diagrams with minimal labels, maybe a hover state.
    *   **Call to Action:** A dedicated section with stunning imagery and clear buttons for "Schedule a Tour" or "Contact Us".
    *   **Footer:** Minimalist, with logo, copyright, social links (icon-only), and essential legal links.

6.  **Palette + Type (Specifics for Recipe):**
    *   **Palette:**
        *   Primary Background: `#F8F6F3` (soft off-white).
        *   Secondary Background (for contrast sections): `#333333` (deep charcoal).
        *   Accent Text/Hover: `#A58A63` (muted gold/bronze).
        *   Main Body Text: `#1A1A1A`.
        *   Hero Overlays: `#FFFFFF`.
    *   **Typography:**
        *   **Hero Overlays & Major Headings (e.g., H1, H2):** `Ibarra Real Nova` (serif, Google Fonts), `font-weight: 300`, `letter-spacing: 0.06em`, `text-align: center`. Responsive `font-size: clamp(3em, 8vw, 6em)`.
        *   **Navigation & Body Text:** `Inter` (sans-serif, Google Fonts), `font-weight: 400`, `letter-spacing: 0.02em`. Navigation links `text-transform: uppercase`, `letter-spacing: 0.08em`.
        *   **Subheadings (e.g., H3, H4):** `Inter`, `font-weight: 600`.

This plan provides a precise roadmap to recreate the sophisticated experience of the sample website.