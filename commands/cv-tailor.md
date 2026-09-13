# /cv-tailor · Tailored CV + Cover Letter for One Engineering Job

Produces a tailored CV and cover letter for King David's brother (Aircraft Engineering with Pilot Studies graduate, applying for any engineering role, aviation #1). Output reads human, not AI. King David reviews and sends manually. No auto-apply.

**Project:** `C:\Users\Dell\.claude\cv-tailor\`
**Project brain:** `C:\Users\Dell\.claude\cv-tailor\CLAUDE.md`

---

## Steps to Execute

1. **Read the project CLAUDE.md first.**
   `C:\Users\Dell\.claude\cv-tailor\CLAUDE.md`, confirms scope, persona, anti-AI rules.

2. **Confirm `.env` is set.**
   `ANTHROPIC_API_KEY` must be filled in `C:\Users\Dell\.claude\cv-tailor\.env`.
   If empty, copy from `C:\Users\Dell\.claude\newsletter-demos\.env`. Stop and tell King David if no key exists anywhere.

3. **Confirm dependencies installed.**
   `pip install anthropic python-dotenv reportlab` (idempotent, safe to re-run).

4. **Confirm brother's data is filled in.**
   - `applicants\brother\profile.md`, if still mostly `[FILL IN]` placeholders, ask King David to fill it before running.
   - `applicants\brother\master_cv.md`, if still placeholder, ask King David to paste brother's CV.
   - If both are clearly populated → proceed.

5. **Collect inputs from King David:**
   - **Company name** (e.g. "Lufthansa Technik")
   - **Role title** (e.g. "Trainee Aircraft Engineer")
   - **Job description**, paste text OR provide URL (you fetch and render to text)
   - **Bridging context** (only if the role is NOT aviation), King David tells you which of brother's skills/modules/projects to lead with

6. **Run the master pipeline:**
   ```
   cd "C:\Users\Dell\.claude\cv-tailor"
   python tools\run_tailor.py --company "<company>" --role "<role>" --job-file .tmp\job.txt [--bridging "<note>"]
   ```
   Save the pasted job text to `.tmp\job.txt` first, then run.

7. **What the runner does (do not interfere):**
   - Stages pack folder: `applicants\brother\applications\[YYYY-MM-DD]_[company]_[role]\`
   - Agent 1 (Job Analyst) → `analysis.md`
   - Agents 2 + 3 in PARALLEL → `tailored_cv.md` + `cover_letter.md`
   - Agent 4 (Humanizer QA) → scores both on 4-axis rubric, rewrites anything < 8/10, writes `notes.md`
   - PDF Exporter → `tailored_cv.pdf` + `cover_letter.pdf`

8. **Report back to King David:**
   - Pack folder path
   - Final scores from `notes.md` (both should be 8+, flag if forced pass)
   - List of files produced
   - One-line summary of any flagged issues
   - Remind him: he sends the application himself

## When Something Goes Wrong

| Symptom | Fix |
|---------|-----|
| `ANTHROPIC_API_KEY` missing | Copy from Newsletter Demos `.env` or get fresh key from console.anthropic.com |
| `reportlab not found` | `pip install reportlab` |
| Agent 4 keeps forcing pass | Check humanizer rules · likely a banned word in `master_cv.md` itself. Edit master CV and rerun. |
| PDF formatting odd | `cv-tailor\tools\export_pdf.py` is ReportLab-based; tweak styles dict for the issue |
| URL fetch failed | Ask King David to paste job text manually |
| Brother's profile / master CV both empty | Hard stop. Tell King David to fill them. |

## The Hard Rules
1. **Sound human, not AI.** Agent 4 enforces. `cv-tailor\workflow\humanizer_rules.md` is the law.
2. **No auto-apply, no auto-send.** Output is always for King David's review.
3. **Bridging context = top priority.** When King David provides one, it overrides default emphasis.

## Money Angle
Brother is Client Zero. Once the pipeline produces packs King David is willing to send for his brother → the same system works for paying clients. Add `applicants\client_name\` and a per-client `profile.md` + `master_cv.md`. Price: €20, 50 per CV pack, or €100/month for unlimited applications.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
