# /blind-spot · Find what you missed, before King does

> Born 2026-08-30 from the PaintPots build for Samson. King had to point out three
> separate misses in a row ("did you reorganise and add the png files", "the jumbotron
> needs to be header and footer the same", "show thumbnail aswell in showreel is that
> not obvious"). Each one was findable by me, without being told. This skill is the
> loop that finds them first.
>
> Complements, does not replace: `/qa-master` (adversarial gate, run it INSIDE stage 4
> here) and `/website` (the build skill). Scale depth to stakes, Rule #17.

## When this runs
- Before showing King ANY deliverable he will judge (Rule #26: show real proof).
- Automatically after a build, not on request. If King has to ask "did you check X",
  this skill failed.
- Any handover to a third party (client, Samson, a lecturer, a buyer).

---

## THE CORE PRINCIPLE

**A deliverable is not what the code says. It is what the person sees when they open it.**

Everything below exists because those two things kept disagreeing.

Never say "should work". Open it. Look at it. Rule #21.

---

## STAGE 1 · Inventory what you were GIVEN

Before judging the output, list the inputs. You cannot spot an unused asset
if you never counted the assets.

```
1. Every file the client/King handed over (count them)
2. The instructions, VERBATIM from source, not from memory or a summary
   - the email / the README / the meeting transcript
   - pull the actual words: mcp__granola__get_meeting_transcript, the zip, the thread
3. Anything said in passing that reads like a requirement
```

**Why verbatim matters:** on PaintPots, the summary said "jumbotron on the footer".
The transcript said *"I want the Jumbotron, the image I use for the shop. The show reel,
the gallery, the home, the contacts. I want it to be the same. Has the 4."* Five pages
plus the footer, not one footer. The summary lost 5 of 6 requirements.

---

## STAGE 2 · The unused-asset audit (mechanical, always run it)

If someone gave you 8 files and you used 5, the 3 spares are three missed requirements.
People do not send files for no reason.

```bash
cd <deliverable folder>
for f in *.png *.jpg *.svg *.mp4; do
  n=$(grep -o -F "$f" index.html | wc -l)
  if [ "$n" -eq 0 ]; then echo "  UNUSED -> $f"; else echo "  used x$n -> $f"; fi
done
```

Target: **zero unused.** On PaintPots this found three, including Samson's own
hand-drawn logo sitting in the folder while the header showed plain text.

Generalise beyond images: unused fonts, an unreferenced stylesheet, a data file
nobody reads, a video nobody links, a section of the brief nobody answered.

---

## STAGE 3 · Look at it with your own eyes

Reading the code is not seeing the page. Screenshot it and actually read the picture.

```powershell
# Cache-bust: file:// URLs cache HARD. A normal reload can show you yesterday's build
# and you will confidently report a fix that is not visible. This bit King twice today.
Start-Process msedge -ArgumentList "-inprivate","file:///<abs path>"
Start-Sleep -Seconds 8
Add-Type -AssemblyName System.Windows.Forms; Add-Type -AssemblyName System.Drawing
$s=[System.Windows.Forms.Screen]::PrimaryScreen
$b=New-Object System.Drawing.Bitmap($s.Bounds.Width,$s.Bounds.Height)
[System.Drawing.Graphics]::FromImage($b).CopyFromScreen($s.Bounds.Location,[System.Drawing.Point]::Empty,$s.Bounds.Size)
$b.Save("<scratchpad>\shot.png")
```

Then **Read the png** and describe what is actually there. Every page, every state.

Ask of the screenshot, not the code:
- Can I read every piece of text? (contrast)
- Is any image cropped, stretched, missing, or a placeholder?
- Does anything overflow its container?
- Is there an emoji or lorem or a grey box where real content belongs?

---

## STAGE 4 · Trace to root cause, never patch the symptom

When something looks wrong, find WHY before you touch it.

Worked example from PaintPots, the title was near-invisible:
- Symptom: "PaintPots" barely readable on the hero.
- Wrong fix: bump the font-weight, add a shadow.
- Root cause: `.page-hero` set `color: white`, `.hero` never did, so the h1
  inherited `#333` from `body` onto a dark background. One missing declaration,
  present since the first build, invisible until the background got darker.

Second example, same build:
- Symptom: jumbotron only on the footer.
- Wrong fix: copy the footer rule onto each page's markup.
- Root cause: `.cosmic-bg`, the shared class all 5 heroes use, had **no image
  reference at all**, only a gradient. Fixing the class fixed all five at once.

Run `/qa-master` here at STANDARD or FULL depth for anything client-facing.

---

## STAGE 5 · The obviousness pass

Ask literally: **"What would a person expect here that is not here?"**

Not "does it meet the letter of the brief". What does the thing NEED to be the thing.

- A showreel needs **thumbnails**. A play triangle on a grey box is not a showreel.
  (King: *"show thumbnail aswell in showreel is that not obvious and logic"*.) Correct.
- A video card needs to **go somewhere** when clicked.
- A brand site needs the **brand's own logo**, not the brand's name in the body font.
- A shop needs prices and a button that responds.
- A contact form needs to say something when submitted.

This stage is where domain sense lives. Run it as the target's user, not as its builder.

---

## STAGE 6 · Re-verify after EVERY fix

A fix is a claim. Claims get proven, in this session, by something that executed.

1. Make the change
2. Cache-busted fresh load
3. New screenshot
4. Read it, confirm the specific thing changed AND nothing else broke

Fixing the logo size on PaintPots made it overflow the header. Caught only because
of a re-screenshot. Never batch fixes and screenshot once at the end (Rule #26).

---

## WEB DELIVERABLE · the recurring defect classes

Checked every time, these are the ones that keep recurring:

| Class | The trap | The check |
|---|---|---|
| Colour inheritance | Child block never sets `color`, inherits body dark onto a dark bg | Read every heading in the screenshot |
| Background cropping | `background-size: cover` silently crops a landscape image in a short wide band | Compare rendered band against the source file |
| Layer order | Image at `z-index: 0` under an overlay at `z-index: 0`, image never shows | Image below overlay below text, distinct z values |
| Cache | `file://` serves a stale build, you report a fix that is not there | Always `-inprivate` or a fresh window |
| Unused assets | Files shipped in the folder, referenced nowhere | Stage 2 audit |
| Placeholders | Emoji, lorem, "TODO", a gradient standing in for art | Grep for emoji + eyeball every card |
| Overflow | Enlarged logo or long text breaks its container | Screenshot after every size change |
| Dead interaction | A card that looks clickable and is not | Click it |
| Offline assumption | Remote images silently blank with no network | Fallback layer behind, state the trade-off |

---

## OUTPUT · what King gets

Never "done". Give him the table:

```
BLIND SPOTS FOUND (n)
| # | What I missed | Root cause | Status |
Plus: what I checked and it was already fine
Plus: any trade-off I made and why (e.g. remote thumbnails need internet)
```

Then the real thing on screen (Rule #26), then wait for his yes.

**If the count is zero, say what you checked.** A bare "no issues" is not a report,
it is a claim with no evidence behind it.

---

## The standing rule this enforces

King should never be the one to notice. Every time he says "is that not obvious",
that specific check gets added to Stage 5 above so it is caught by machine next time.

Related: `/qa-master` · `/qa` · `/website` · `/ship` ·
`memory\feedback_staged_qa_loop_standard.md` (Rule #26) ·
`memory\feedback_consensus_everything_rule.md` (Rule #17)
