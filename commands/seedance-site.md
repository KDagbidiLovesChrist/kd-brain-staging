# /seedance-site · Seedance Animated Website Skill

> READ FIRST: `C:\Users\Dell\.claude\CLAUDE.md` (master brain, WAT, operating rules).
> READ ALSO: `C:\Users\Dell\.claude\memory\skill_seedance_animated_websites.md` (full pipeline + hard-won lessons).
> READ ALSO: `C:\Users\Dell\.claude\plugins\marketplaces\claude-plugins-official\plugins\frontend-design\skills\frontend-design\SKILL.md` (the design rulebook, no AI slop).

**Trigger:** King types `/seedance-site` OR says "build a premium animated website", "build a
3D-style site", "Seedance site for [brand]", "scroll-scrub site", "cinematic animated website",
"build the [brand name] site from the video".

**What it produces:** A flagship-tier website where the hero is an AI cinematic video scrubbed
frame-by-frame as the user scrolls, the Apple product-page technique. Looks like a $10, 15k
"3D" site. Actually just images flipping fast. No real-time WebGL, no lag, buttery on any phone.
Priced at the top of the menu: **€4,000+ build + €129, 249/mo maintenance**. This is King's highest
ticket web offer.

**Cost to produce:** ~$1.33 the old way (KIE: $0.08 image + $1.25 video). **Cheaper now via the cost
router** (2026-06-26): cheapest image + MuAPI Seedance Pro 1080p video ≈ **$0.62, 0.68/site** (~half).
Use `tools\gen_router.py` so each generation auto-picks the cheapest tool. Everything else is free.

---

## WAT chain

- **W (Workflow):** This SOP (the numbered steps below).
- **A (Agent):** Claude, reads the frontend-design skill, designs the brand world, writes all code.
- **T (Tools):**
  - `C:\Users\Dell\.claude\tools\gen_router.py`, **cost router: quotes MuAPI vs KIE and runs the cheapest. USE THIS FIRST.**
  - `C:\Users\Dell\.claude\tools\muapi_generate.py`, MuAPI wrapper (Seedance/Kling/Veo/Flux/Nano Banana, one key).
  - `C:\Users\Dell\.claude\tools\kie_generate.py`, KIE API wrapper (image + video generation). Fallback / still used for images at 2k.
  - `C:\Users\Dell\.claude\tools\batch_seedance.py`, batch multiple brands at once (3 concurrent).
  - `ffmpeg`, extracts frames from the video clip.
  - `C:\Users\Dell\Documents\Website Builder\templates\seedance-site\index.template.html` (LAPTOP-ONLY: lives outside the synced brain), the parameterised veyra-b engine.
  - `vercel` CLI, deploys and aliases the finished site.
- **S (Skill):** `/seedance-site`, one trigger runs the whole pipeline.

**API keys:** `KIE_AI_API_KEY` and `MUAPI_API_KEY` live in `C:\Users\Dell\.env.master`. Already loaded.

---

## Cost-aware generation (NEW 2026-06-26 · pick the cheapest tool automatically)

King's rule: **when choosing a tool, choose by cost.** The router does this for you. It quotes
**Google Gemini/Veo**, **MuAPI** (live `estimate-cost` endpoint) and **kie.ai** (price table), then runs
the cheapest that meets the quality tier, with the others as fallback.

```powershell
# See the costs BEFORE spending (free · no generation happens):
python .claude\tools\gen_router.py quote video --res 1080p --dur 5 --i2v          # ranks all video tools
python .claude\tools\gen_router.py quote image --res 2k                            # ranks all image tools

# Generate via the cheapest tool automatically:
python .claude\tools\gen_router.py image "<prompt>" hero.png --aspect 16:9 --res 2k
python .claude\tools\gen_router.py video "<motion prompt>" hero.mp4 --first-frame <url> --dur 5 --res 1080p
```

Tiers: `--tier budget` = Seedance Pro (cheap, great for social) · `--tier premium` = Seedance 2.0
(top quality, realistic humans) · `--tier any` (default) = cheapest across all.

**What it picks today (verified 2026-06-26):**
- **Video → Gemini Veo 3.1 Lite** = cheapest ($0.30 720p · $0.48 1080p per ~6s; Veo durations snap to 4/6/8s).
  Then MuAPI Seedance Pro ($0.36 720p · $0.62 1080p/5s), then Veo Fast, then premium (Seedance 2.0 $1.25 / Veo Quality / kie.ai $2.55).
- **Image → MuAPI Nano Banana 2** ($0.06 1k); Gemini ($0.067) and kie.ai ($0.08) close behind. (kie.ai is cheapest at 2k = $0.08.)
- MuAPI Seedance i2v is **live-tested working** (real $0.36 clip generated + QA'd). Veo path built; first live Veo run will confirm it.

> ⚠️ **Spend + billing:** MuAPI is pay-as-you-go (no free API credits), key in `.env.master`, top-ups via `/money`.
> **Veo runs on the Gemini key and needs the Gemini API PAID tier enabled** (Veo is not on the free tier), confirm
> billing before relying on it. kie.ai stays as the working fallback. MuAPI + Veo response/SDK fields are
> auto-detected; MuAPI is confirmed, Veo confirms on its first paid run (see notes in the tool files).

Steps 1, 2 below show both the router command (preferred) and the direct KIE command (fallback).

---

## SOP · numbered steps (King is non-technical · explain as you go)

### Step 0 · Brief and brand world
Before touching any tool, ask King (or read the brief):
- Brand name, industry, target audience.
- Mood/feeling (dark luxury? clean tech? organic wellness? bold fintech?).
- Any reference sites or colours they have in mind.
- The CTA destination (booking link, WhatsApp, email form).

Then READ the frontend-design skill SKILL.md. Commit to a BOLD aesthetic direction that is
completely unique to this brand. Each brand gets its OWN world, palette, fonts, copy, concept.
NEVER reskin veyra-b with a colour-swap and call it done. [[feedback-each-3d-world-truly-unique]]

Good starting question: "What is the ONE thing someone should feel when they land on this site?"

### Step 1 · Generate the hero still with Nano Banana (~$0.08)
Nano Banana is a cinematic-quality image model on KIE. It produces the frame that Seedance will
animate. Think of it as "designing the opening shot of a film".

**What to run (PowerShell, from C:\Users\Dell):**
```powershell
# Preferred · router picks the cheapest image tool (kie.ai or MuAPI):
python .claude\tools\gen_router.py image "<your cinematic prompt>" hero.png --aspect 16:9 --res 2k
# Fallback · direct KIE:
python .claude\tools\kie_generate.py image "<your cinematic prompt>" hero.png 16:9
```

**KIE model used internally:** `google/nano-banana`
IMPORTANT: `google/nano-banana-2` does NOT exist on KIE, it returns 422. Always use v1.

**Good prompt structure:**
"[Brand aesthetic] [hero object or scene], [lighting], [camera angle], cinematic, ultra-detailed,
8K, [mood adjectives], [colour palette]"

Example for a jewellery brand:
"Black diamond solitaire ring on dark obsidian surface, dramatic directional light from upper-left
, extreme macro, 4:3 crop, deep shadow, razor-sharp facets, cinematic, ultra-detailed, 8K,
luxury editorial, onyx and gold palette"

Save the output URL from the script (you will need it as `first_frame_url` in Step 2).

### Step 2 · Animate the still with Seedance 2.0 (~$1.25)
Seedance 2.0 takes the still and animates it into a ~6-second cinematic clip. The trick: pass
the still as `first_frame_url` so the video starts exactly on your designed frame.

**What to run:**
```powershell
# Preferred · router picks the cheapest video tool/tier (MuAPI Seedance Pro is usually cheapest):
python .claude\tools\gen_router.py video "<motion prompt>" hero.mp4 --first-frame <first_frame_url> --dur 5 --res 1080p
# Fallback · direct KIE Seedance 2.0:
python .claude\tools\kie_generate.py video "<motion prompt>" hero.mp4 <first_frame_url> 6 720p 16:9
```

**KIE model used internally:** `bytedance/seedance-2`
Set `generate_audio: false` (no audio needed, the site has no sound).
Duration: 6 seconds. Resolution: 720p (enough for frame-scrub at 1280px wide).

**Good motion prompt structure:**
"[Subject] [what moves], [camera move], [speed], [mood], cinematic, slow motion"

Example:
"The diamond ring catches light, facets slowly rotating, a single beam sweeps across the stone, camera drifts in slowly, dreamlike, luxurious, no cuts, continuous motion"

The script polls KIE until the video is ready (~30, 90 seconds), then downloads `hero.mp4`.

### Step 3 · Extract frames with ffmpeg
ffmpeg splits the video into individual JPEG frames. Each frame becomes one "state" of the scroll.

**What to run:**
```powershell
ffmpeg -i hero.mp4 -vf "fps=30,scale=1280:-1" -q:v 3 frames/f_%03d.jpg
```

- `fps=30` → 30 frames per second → 6s clip = ~180 frames.
- `scale=1280:-1` → 1280px wide, height auto-calculated (keeps aspect ratio).
- `-q:v 3` → high quality JPEG (1=best, 31=worst; 3 is a good balance of quality/size).
- Output: `frames/f_001.jpg`, `frames/f_002.jpg`, ... `frames/f_180.jpg`.

After running, count the frames:
```powershell
(Get-ChildItem frames -Filter "*.jpg").Count
```
Note this number, it becomes `{{FRAME_COUNT}}` in the template.

### Step 4 · Build the site from the template
Open `C:\Users\Dell\Documents\Website Builder\templates\seedance-site\index.template.html` (LAPTOP-ONLY: lives outside the synced brain).
Copy it to a new folder: `Website Builder\proofs\<brand-slug>\index.html`.

Replace every `{{PLACEHOLDER}}` with brand-specific values. Full list in the README at:
`C:\Users\Dell\Documents\Website Builder\templates\seedance-site\README.md` (LAPTOP-ONLY: lives outside the synced brain)

The critical replacements are:
- `{{FRAME_COUNT}}`, the number from Step 3.
- `{{FRAME_PATH}}`, `frames/f_` (default, leave as-is if you used the ffmpeg command above).
- All `{{PALETTE_*}}` values, pick colours that suit THIS brand.
- `{{FONT_IMPORT_URL}}`, `{{FONT_DISPLAY}}`, `{{FONT_BODY}}`, distinctive fonts (NOT Inter/Arial).
- All section copy: hero headline, philosophy text, product cards, CTA.

**Design rule from the frontend-design skill:**
Pick an extreme aesthetic and commit to it fully. Refined luxury? Raw industrial? Bold editorial?
Do not hedge. The difference between a €500 site and a €4,000 site is intentionality.

**Readability rule (HARD CONSTRAINT):**
Text must always be readable over the video frames. The CSS gradient scrims are your safety net.
Never remove the vignette, top-fade, or bottom-fade overlays. For dark text on light backgrounds,
add an explicit scrim div with `background: rgba(0,0,0,0.5)` minimum.

### Step 5 · Copy hero assets into the site folder
```
proofs/<brand-slug>/
  index.html           ← filled template
  frames/              ← the f_001.jpg ... f_NNN.jpg files from Step 3
  img/                 ← editorial, featured, craft, piece images
```

For the `img/` section images (editorial, featured, craft, piece1/2/3):
- Use Nano Banana again to generate brand-appropriate images at ~$0.08 each.
- Or use stock photos from Unsplash (free, no attribution required for commercial use).
- Each should match the brand palette and mood, no generic white-background stock shots.

### Step 6 · QA (non-negotiable before deploy)

**A. Mobile loader test (the most important check):**
Open Chrome DevTools → Network tab → throttle to "Slow 3G".
Hard-reload the page. The preloader should reveal the page within 3.5 seconds maximum.
It should NEVER stay stuck at "0%" indefinitely. If it does, the 3.5s setTimeout fallback
is broken, check the JS loader in the template.

**B. Scroll-scrub test:**
Scroll slowly through the hero. Frames should advance smoothly. If jumpy:
- Check TOTAL_FRAMES matches the actual frame count.
- Check the frame path `frames/f_001.jpg` exists (no off-by-one).

**C. Text readability:**
On mobile at the narrowest viewport (375px), all overlay text must be readable.
Minimum: white text on a 50% black scrim. Use the browser's accessibility checker.

**D. Console errors:**
Open DevTools → Console tab. Zero errors acceptable. 404s on frame files are fatal.

**E. Cross-browser:**
Test in Chrome, Safari (iOS if possible), Firefox. Canvas + rAF are well-supported but Safari
occasionally has timing quirks, the 3.5s timeout covers this.

### Step 7 · Deploy to Vercel and alias to a clean public URL
```powershell
# Deploy from the site folder
vercel deploy --prod --yes --cwd "Documents\Website Builder\proofs\<brand-slug>"
```

The deploy command outputs a URL like `<brand-slug>-abc123.vercel.app`.
That URL is team-scoped and will 401 on external links. You must alias it:

```powershell
vercel alias set <deployment-url> <brand-name>.vercel.app
```

Example: `vercel alias set veyra-abc123.vercel.app veyra-web.vercel.app`

Verify the alias is live and public:
```powershell
(Invoke-WebRequest -Uri "https://<brand-name>.vercel.app" -Method Head).StatusCode
```
Should return 200.

Send King the live URL via phone so he can check it on mobile before pitching the client.

---

## Pricing and positioning

| Tier | What's included | Price |
|---|---|---|
| Seedance Flagship | AI hero video + 7-section scroll-scrub site + Vercel hosting | €4,000 build |
| Monthly retainer | Hosting, updates, new section per quarter | €129-249/mo |
| Add-ons | Booking form, CRM integration, analytics | Quote separately |

**How to pitch it:**
"This is the Apple product-page technique, the same thing you see when you scroll through the
iPhone page and the phone slowly rotates. Except your brand is the hero. It looks like a $15k
custom agency build. It takes us two days."

Free sample first: always build the demo, show King before sending, King sends to the prospect.
Never pitch without a live URL they can scroll on their phone.

---

## Batch mode (building 10 sites from pre-made videos)

King has 10 hero videos already generated in `Documents\Website Builder\seedance\<slug>\hero.mp4`.
To extract frames for all 10 at once and start building:

```powershell
# Run this from Documents\Website Builder\
$brands = @("veyra","flux","nova","meridian","veloce","kin","lume","roast","atlas","orbit")
foreach ($b in $brands) {
  $out = "proofs\$b\frames"
  New-Item -ItemType Directory -Force -Path $out | Out-Null
  ffmpeg -i "seedance\$b\hero.mp4" -vf "fps=30,scale=1280:-1" -q:v 3 "$out\f_%03d.jpg" -y
}
```

Or use `batch_seedance.py` to generate new image+video pairs:
`python C:\Users\Dell\.claude\tools\batch_seedance.py`
(reads a concept list from within the script, 3 concurrent, logs to `seedance\batch_log.json`)

---

## Hard-won lessons (READ BEFORE BUILDING)

1. **Mobile loader is the #1 failure mode.** Without the "reveal on first frame + 3.5s timeout"
   combo, the page hangs forever on slow mobile connections. King personally hit this ("stuck at
   000/145"). The template has it baked in, do not remove it.

2. **Each brand truly needs its OWN aesthetic.** King rejected a batch where 2 sites used the
   same engine with different colours. They felt like reskins. The rule: different fonts, different
   colour temperature, different 3D concept, different copy voice. [[feedback-each-3d-world-truly-unique]]

3. **KIE model names are exact.** `google/nano-banana` works. `google/nano-banana-2` → 422 error.
   `bytedance/seedance-2` works. `bytedance/seedance-2-fast` = cheaper but lower quality.

4. **Vercel aliases are mandatory.** The team-scoped deploy URL (e.g. `project-abc123.vercel.app`)
   returns 401 when opened in a non-team browser. Always alias to a clean public name.

5. **Text readability over video.** Dark video = white text looks great. But if Seedance generates
   a light or blown-out frame, text can disappear. Solution: always keep the vignette + gradient
   overlays. Test specifically on the lightest frame in the sequence.

6. **Delete `.vercel` before deploying a new folder.** If you copy from another site folder,
   the hidden `.vercel` config points to the OLD project. Delete it first or `vercel deploy`
   will overwrite the wrong project.

---

## Tool paths (verified 2026-06-04)

| Tool | Verified path |
|---|---|
| `kie_generate.py` | `C:\Users\Dell\.claude\tools\kie_generate.py` |
| `batch_seedance.py` | `C:\Users\Dell\.claude\tools\batch_seedance.py` |
| Template | `C:\Users\Dell\Documents\Website Builder\templates\seedance-site\index.template.html` (LAPTOP-ONLY: lives outside the synced brain) |
| Template README | `C:\Users\Dell\Documents\Website Builder\templates\seedance-site\README.md` (LAPTOP-ONLY: lives outside the synced brain) |
| Seedance videos | `C:\Users\Dell\Documents\Website Builder\seedance\<slug>\hero.mp4` |
| KIE API key | `KIE_AI_API_KEY` in `C:\Users\Dell\.claude\.env.master` |
