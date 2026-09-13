# /capstone · Capstone Submission Skill
# PURPOSE: Prepare and submit proof-of-work for any course capstone or challenge completion

---

## TRIGGER
`/capstone`, called when completing a course challenge that requires proof submission

---

## WHAT THIS SKILL DOES
1. Generates a proof document showing folder structure + skills built
2. Takes screenshots of the system in action
3. Navigates to the submission form and pre-fills all fields
4. Marks the challenge complete in memory

---

## AIS CHALLENGE CAPSTONE (completed 2026-05-16)

**Submission URL:**
https://docs.google.com/forms/d/1LIz5IOul85f76wileSMdTNOysamFJ5Gzrf_dTcoPIUM/viewform

**What was submitted:**
- Proof document: C:\Users\Dell\.claude\capstone_proof.txt
- Screenshot: C:\Users\Dell\.claude\day7-capstone.png (92% progress bar visible)
- Community posts: Days 3, 7 all live at skool.com/ai-automation-society

**What still needs King David:**
- 1-2 minute screen recording (Win + G → record → open Claude Code → type /scrape → stop)
- Upload video to the Google Form above
- Submit

---

## REUSABLE PROOF GENERATION

Run this PowerShell to generate a fresh proof document for any submission:

```powershell
$skills = Get-ChildItem "C:\Users\Dell\.claude\commands\" -Filter "*.md" | Select-Object Name
$proof = "SKILLS BUILT:`n" + ($skills | ForEach-Object { "  /" + $_.Name.Replace(".md","") }) -join "`n"
$proof | Out-File "C:\Users\Dell\.claude\capstone_proof.txt" -Encoding utf8
```

---

## GOOGLE FORM NAVIGATION (Playwright)

```javascript
// Navigate to form
await page.goto('FORM_URL_HERE');

// Fill name field
await page.locator('[aria-label*="name"], [aria-label*="Name"]').fill('Kingdavid Agbidi');

// Fill description field  
await page.locator('textarea').first().fill('DESCRIPTION_HERE');

// Submit
await page.locator('[role="button"]:has-text("Submit")').click();
```

---

## SKILL REFERENCE (what to show in any demo video)

Best skills to demo (visual, fast, impressive):
1. `/scrape`, runs Firecrawl, outputs a CSV of leads in ~30 seconds
2. `/newsletter`, researches a topic, writes full HTML email
3. `/skool-post`, automated browser posting (uses Playwright live)

For a 2-minute video:
- Open Claude Code terminal
- Type /scrape (or /newsletter)
- Let it run, narrate what it's doing
- Show the output file / result
- Done

---

## NOTES
- The /skool-post playbook is itself the Day 6 capstone proof (self-improving skill)
- AIS Challenge Graduates module: once verified, King David is added permanently
- This skill can be reused for any future course, challenge, or client proof-of-work


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
