---
name: excalidraw-visuals
description: Use when someone asks for a hand-drawn visual, PNG image, rendered diagram, visual explanation, or says "excalidraw image" or "excalidraw visual". This generates PNG images, not editable files.
---

# /excalidraw-visuals · Excalidraw-Style Image Generator

Generates hand-drawn style PNG images using kie.ai (Nano Banana model, ~$0.02, 0.09/image).

## Prerequisites

1. `KIE_AI_API_KEY`, sign up at kie.ai, add to `.env` in the current project folder
   (add `KIE_AI_API_KEY=your-key-here` to any project's `.env`, or to `.env.master`)
2. Node.js installed (already installed, `node --version` to verify)

## Script and Style Guide Paths (Global)

| What | Path |
|------|------|
| Script | `C:\Users\Dell\.claude\tools\excalidraw-visuals\generate-visual.js` |
| Style guide | `C:\Users\Dell\.claude\tools\excalidraw-visuals\style-guide.md` |
| Style reference image | `C:\Users\Dell\.claude\brand_assets\excalidraw-style-reference.png` |
| Output folder | `[current project]\projects\excalidraw-visuals\` (auto-created) |

## Style Prefix (LOCKED · prepend to every prompt, never modify)

```
Excalidraw-style hand-drawn diagram on a clean white background. All text uses neat, consistent architect-style handwriting -- legible, slightly rounded letters with medium stroke weight. Letter sizes are uniform within each label. Titles are bold and larger. Body labels are smaller but equally neat. This is NOT sloppy handwriting -- it looks like a designer wrote it carefully with a thick marker.

Shapes are rounded rectangles with a 2-3px dark gray (#495057) hand-drawn outline and soft pastel fills. Lines and arrows are slightly wobbly and hand-drawn, not ruler-straight. Arrowheads are simple triangles. Nothing is pixel-perfect -- everything has a natural, sketched feel with visible stroke texture.

Color palette: soft blue (#a5d8ff), warm yellow (#ffec99), soft green (#b2f2bb), coral (#ffa8a8), light purple (#d0bfff). All text is dark charcoal (#343a40). All lines and arrows are dark gray (#495057). Background is always clean white.

People are simple stick figures with round heads, no facial features. AI agents/robots have a round head with two dot eyes and a small antenna. Documents have a folded corner. Gears represent automation. All icons are simple line drawings, not detailed or cartoonish.

Layout is clean and spacious with generous whitespace. Visual hierarchy is clear -- title is largest, labels are short (max 3 words each). The overall feel is educational, friendly, and slightly more polished than basic Excalidraw -- colored fills, intentional spacing, consistent sizing, and meaningful color coding elevate it.

Do NOT include: realistic photos, gradients, drop shadows, 3D effects, corporate clip art, stock imagery, dark backgrounds, heavy borders.
```

## Workflow

### Step 1 · Gather input
- What concept or process to visualize
- Specific elements, steps, or labels
- Aspect ratio (default: 16:9)

If vague, ask ONE clarifying question about what specific angle or flow to show.

### Step 2 · Choose layout template

| Template | Best For |
|----------|----------|
| Left-to-Right Flow | Processes, sequences, transformations |
| Hub and Spoke | Capabilities, features around a central concept |
| Top-to-Bottom Hierarchy | Levels, layers, progressive depth |
| Side-by-Side Comparison | Before/after, old vs new |
| Numbered Steps List | Frameworks, checklists |
| Cycle / Loop | Feedback loops, iterative processes |

### Step 3 · Plan the text (minimize it)

- **Title:** max 5 words, prefer 3
- **Box labels:** max 3 words each, prefer 1, 2
- **Annotations:** max 4 words each
- **Total word count:** target under 30 words, absolute max 50

### Step 4 · Assign colors by meaning

- **Flows:** Blue (input) → Yellow (process) → Green (output)
- **Comparisons:** Coral (old/bad/slow) vs Green (new/good/fast)
- **Hub and spoke:** Blue center, mixed colors for spokes
- **Hierarchies:** Blue (top) → Yellow (middle) → Green (bottom)

Never leave color choice to the model. Always specify.

### Step 5 · Build the prompt

```
[STYLE PREFIX, paste in full]

STYLE REFERENCE: Match the visual style of the reference image exactly.

Diagram concept: [TITLE, max 5 words]

Layout: [TEMPLATE NAME], [brief spatial description]

Elements (left to right / top to bottom):
1. [Element name], [color] fill, label: "[EXACT TEXT]"
2. ...

Connections:
- Arrow from [1] to [2], label: "[TEXT or none]"
...

Title at top center, bold and large: "[EXACT TITLE TEXT]"
```

### Step 6 · Generate

```bash
node "C:\Users\Dell\.claude\tools\excalidraw-visuals\generate-visual.js" "<FULL_PROMPT>" "projects/excalidraw-visuals/[YYYY-MM-DD]-[slug].png" "16:9" --input "C:\Users\Dell\.claude\brand_assets\excalidraw-style-reference.png"
```

Aspect ratios: `16:9` (default) · `1:1` · `4:5`

### Step 7 · Present result

- Show the file path for preview
- One-line summary of what it shows
- Ask if adjustments are needed (only change diagram-specific part, never touch style prefix)

## Self-Improvement Rule

After any successful run: note what layout/color choices worked. If King David requests a specific style, save that style note to `C:\Users\Dell\.claude\knowledge\patterns.md` under a "Excalidraw Visuals" heading.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
