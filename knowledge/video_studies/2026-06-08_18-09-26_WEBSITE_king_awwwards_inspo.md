# Website Study: ref4.mp4
_Analysed: 2026-06-08 18:09_

Here's a precise, time-coded breakdown of the website's look and feel for recreation:

## 1. ONE-LINE VIBE
Minimalist, elegant interior design showcase with a captivating, scroll-driven room transformation animation.

## 2. THE HERO (first screen)
The centerpiece is a large, high-fidelity, photorealistic 3D render of an empty, minimalist interior space. It's an open-plan room with large windows to the right, a mirror and plant on the left, a pendant light, and a framed art piece on the back wall. The main text "Spaces that breathe." is prominently displayed on the left. The scene is static until the user scrolls.

## 3. SCROLL BEHAVIOUR (most important)
The core interaction is a scroll-driven animation that progressively furnishes and transforms the empty room. This is a classic "scrub-on-scroll" technique, likely using an image sequence or video.

*   **0:01 - 0:02:** As the user begins to scroll down, the initial empty room (0:01) starts to subtly change. A larger plant appears on the right side of the room. A flat-screen TV begins to emerge on the left wall. The camera appears to zoom in slightly and pan a tiny bit to the right.
*   **0:02 - 0:03:** Continued scrolling sees more elements appear. A low, minimalist sofa/seating area begins to form on the right side of the room. Small, round side tables with decor also appear in front of the sofa.
*   **0:03 - 0:08 (includes brief UI overlay):** The scroll continues to drive the animation. The sofa expands and fills out the space. More decorative elements, such as books or additional small sculptures, appear on the side tables. The overall transformation completes, turning the empty shell into a fully furnished, sophisticated living space with a cohesive design. The camera movement throughout this sequence is smooth, subtle, and appears pre-determined (slight zoom and pan).
*   **0:08 - 0:16:** The animation plays back and forth as the user scrolls, demonstrating the direct relationship between scroll input and the scene's progression. Scrolling up "un-furnishes" the room, and scrolling down "furnishes" it.

The motion is directly tied to scroll, feeling exactly like scrubbing a video or an image sequence frame-by-frame. There are no other visible scroll behaviors like parallax or horizontal scroll in this segment.

## 4. IS IT REAL-TIME 3D OR A SCRUBBED VIDEO/IMAGE-SEQUENCE?
Based on the highly realistic rendering quality, the consistent lighting, the complex yet perfectly smooth progressive object reveals, and the lack of any interactive camera controls (like dragging to rotate the scene), this is almost certainly a **pre-rendered image sequence (or video) scrubbed on scroll**. The "frame-by-frame" control with scroll is a strong indicator of this technique, commonly used on premium product pages (e.g., Apple). Real-time WebGL/Three.js would typically show a slightly less photo-realistic quality unless extremely optimized, and often allows for more direct user interaction with the 3D scene.

## 5. MOTION FEEL
The scroll-driven animation feels **snappy and direct**, almost 1:1 with the scroll input. There's minimal visible easing, making it feel very responsive, much like scrubbing through frames of a video. It's smooth and precise, allowing the user to control the speed of the room's transformation.

## 6. LAYOUT & SECTIONS
The video primarily showcases the **Hero Section**.
*   **Top Navigation (Sticky):** "STUDIO - INTERIOR - WORK - STUDIO - PROCESS - JOURNAL"
*   **Hero Content (Overlaid & Sticky):**
    *   **Sub-Headline:** "INTERIOR DESIGN STUDIO" (small, left-aligned)
    *   **Headline:** "Spaces that breathe." (large, left-aligned)
    *   **Call-to-Action Buttons:** "DESIGN YOUR SPACE" and "SEE OUR WORK" (minimalist, rectangular, white text on dark background/outline)
    *   **Scroll Indicator:** "SCROLL TO EXPLORE" (small, bottom-left)
*   The background is a full-screen, high-fidelity render of an interior space that transforms on scroll. There are no other visible sections beyond the hero in this clip.

## 7. COLOUR + TYPOGRAPHY
*   **Palette:** Predominantly **warm neutrals and earthy tones**.
    *   Background/Walls: Off-white/light beige (e.g., `#F0EDE8`, `#EAE7E1`).
    *   Floor: Light greige/concrete tone (e.g., `#D6D3CD`, `#C8C5C0`).
    *   Furniture/Accents: Varying shades of off-white, light grey, and natural wood, with touches of muted green from plants (e.g., `#FAF9F6`, `#D3D6D9`, `#B8A89A`).
    *   Text/UI: Dark grey to black for contrast (e.g., `#1A1A1A`, `#333333`).
*   **Typography:** A clean, modern **geometric sans-serif** typeface.
    *   Headlines ("Spaces that breathe.") are large, with a light or regular weight.
    *   Sub-headlines, navigation, and button text use a smaller size of the same sans-serif, also in light or regular weight. The overall feel is minimalist and sophisticated.

## 8. THE SIGNATURE PREMIUM MOVE
1.  **High-Fidelity Scroll-Driven Room Transformation:** The seamless and incredibly realistic furnishing of an empty room, frame-by-frame, tied directly to scroll input. This is the main "wow" factor.
2.  **Subtle, Cinematic Camera Movement:** The slight zoom and pan during the furnishing process add a cinematic quality, enhancing the immersion and visual storytelling.
3.  **Minimalist & Elegant Aesthetic:** The entire presentation, from the clean typography to the serene color palette and uncluttered UI, elevates the high-quality animation, making the site feel sophisticated and expensive.

## 9. RECREATE RECIPE (for the 'AI clip scrubbed on scroll' workflow)
To recreate this look and feel, we'll leverage AI-generated cinematic clips, process them into frames, and scrub them on scroll.

**1. AI-Generated Cinematic Hero Clip (approx. 15-20 seconds):**
    *   **Scene:** Start with an empty, minimalist, brightly lit interior room, similar to the one in the video (light beige walls, concrete floor, large windows on one side, a mirror on another, a sleek pendant light).
    *   **Progression:** Over the clip's duration, various elements should *smoothly appear and arrange themselves* to furnish the room into a cohesive, inviting living space.
        *   **Phase 1 (Empty):** Establish the empty room and subtle camera perspective.
        *   **Phase 2 (Basic Furniture):** A low-profile, modular sofa, a large flat-screen TV on the wall, and one or two minimalist side tables appear.
        *   **Phase 3 (Decor & Accents):** Plants (e.g., olive tree, snake plant), books, small sculptures, or other subtle decor items populate the tables and floor. Perhaps a plush rug under the sofa.
    *   **Camera Motion:** During the entire sequence, implement a very subtle, slow **zoom-in and a slight pan to the right** (or a fixed gentle arc) to enhance the sense of depth and reveal details as the room fills.
    *   **Quality:** Aim for photorealistic rendering, consistent lighting (soft, natural light), and high resolution.

**2. Frame Extraction:**
    *   Use `ffmpeg` or similar tools to extract **90-120 frames** from the AI-generated clip. This range provides excellent smoothness for the scrub. Ensure frames are extracted as `image%04d.jpg` or `png`.

**3. Preload & Scroll-Scrub Implementation:**
    *   **Preloading:** Implement a robust preloader that fetches all image frames before the hero section becomes interactive, displaying a loading spinner or simple logo.
    *   **Canvas Integration:** Use a `<canvas>` element to display the image frames. This canvas should be full-screen within the hero section, `position: fixed` or `position: sticky` for the duration of the animation.
    *   **Scroll Mapping:** Map the 90-120 frames to a scroll distance of **approximately 2500-3500 pixels**. This provides enough "scrubbing" range for a pleasant interaction. Each frame should advance when the user scrolls X pixels (e.g., 25-30 pixels per frame). Use JavaScript (e.g., GreenSock's ScrollTrigger, or vanilla Intersection Observer + scroll event listener) to control which frame is drawn on the canvas based on the user's scroll position.

**4. Section Build Order:**
    *   **Hero Section (Sticky Container):**
        *   A main `div` with `position: relative` and `height: 100vh`.
        *   Inside, the `<canvas>` element for the animation, `position: absolute; top: 0; left: 0; width: 100%; height: 100%; object-fit: cover;`.
        *   Overlaid UI elements (navigation, headlines, CTA buttons) positioned `absolute` or `fixed` above the canvas, ensuring they are always visible.
        *   A "dummy" scroll-trigger `div` (with no visible content) immediately after the hero, with a `height` equal to the 2500-3500px scroll mapping, forcing the page to scroll and trigger the canvas animation.
    *   **Subsequent Sections:** (Not shown in video, but follow after the scroll trigger).

**5. Palette + Typography:**
    *   **Palette:**
        *   Walls/Background: `#F0EDE8`
        *   Floor/Concrete: `#D6D3CD`
        *   Main Text (dark): `#1A1A1A`
        *   Accent/Button Background (dark): `#333333`
        *   Accent/Button Text (light): `#FAF9F6`
    *   **Typography:**
        *   **Font Family:** A modern geometric sans-serif, e.g., 'Inter', 'DM Sans', 'Montserrat', or 'Manrope'.
        *   **Headlines (`Spaces that breathe.`):** `font-weight: 300` or `400`, large `font-size` (e.g., `4rem` to `6rem` depending on viewport), `line-height: 1.1`.
        *   **Sub-headlines (`INTERIOR DESIGN STUDIO`):** `font-weight: 400`, smaller `font-size` (e.g., `1rem`), `text-transform: uppercase`, `letter-spacing: 0.1em`.
        *   **Navigation/Buttons:** `font-weight: 400`, `font-size: 1.1rem`.
    *   **Smooth Scroll:** Consider a smooth scroll library (like Lenis or Locomotive Scroll) for a more weighted and premium feel, although the video implies a more direct scroll. If adding smooth scroll, ensure it doesn't interfere with the frame-scrubbing responsiveness.