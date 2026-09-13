# /skool-post · Skool Community Post Playbook
# Learned from live execution on 2026-05-16 (Day 3 AIS Challenge)
# PURPOSE: Post to AIS Skool community without fumbling. Every selector verified live.

---

## TRIGGER
`/skool-post`, called with a title and post body

---

## WHAT THIS SKILL DOES
Posts a challenge share (or any post) to the AIS Skool community at:
https://www.skool.com/ai-automation-society

No re-learning. No guessing. Goes straight to posting.

---

## LEARNED SELECTORS (verified 2026-05-16)

| Action | Selector / Method |
|--------|------------------|
| Navigate to community | `https://www.skool.com/ai-automation-society` |
| Open post editor | JS: find div with text "Write something", call `.click()` |
| Fill title | `[placeholder="Title"]` |
| Fill body | `.tiptap.ProseMirror.skool-editor` · use `.fill()` |
| Open category dropdown | `text=Select a category` |
| Reveal POST button | `window.scrollBy(0, 400)` · scrolls it into view |
| Click POST | `text=POST` or button with text POST |

---

## STEP-BY-STEP EXECUTION

### Step 1 · Navigate
```
Navigate to: https://www.skool.com/ai-automation-society
```
Playwright session stays logged in via cookies. No login needed.

### Step 2 · Open the editor
```javascript
// Find "Write something" div and click it
const all = document.querySelectorAll('*');
for (const el of all) {
  if (el.textContent.trim() === 'Write something' && el.children.length === 0) {
    el.click();
    break;
  }
}
```

### Step 3 · Fill title
```
Click: [placeholder="Title"]
Type: {POST_TITLE}
```

### Step 4 · Fill body
```
Click: .tiptap.ProseMirror.skool-editor
Type: {POST_BODY}
```

### Step 5 · Select category
```
Click: text=Select a category
Choose: Wins  (for challenge shares)
```
NOTE (learned 2026-05-16): Clicking "Select a category" automatically reveals
the POST button. No scroll needed. The dropdown opening exposes the full
editor footer. Previous step had window.scrollBy(0, 400), that was wrong.
Removed. This is the self-improvement in action.

### Step 6 · Post
```javascript
// "POST" text selector hits multiple elements, use JS to find the exact submit button
const btn = Array.from(document.querySelectorAll('button')).find(b => b.textContent.trim() === 'Post');
btn.click();
```
SUCCESS SIGNAL: URL changes to /ai-automation-society/{post-slug}
Take screenshot of the live post to confirm.

---

## MARKING LESSONS COMPLETE (learned 2026-05-16)
```javascript
// Works on any lesson page, one selector, always works
document.querySelector('[class*="ModuleCompletionButton"]').click();
```
SUCCESS SIGNAL: progress % increases (e.g. 47% → 49%)
Run this after navigating to any lesson to mark it done.

---

## KNOWN CATEGORIES (AIS community)
- General Discussion
- Wins
- Support Needed
- YouTube Resources

---

## POST TEMPLATE · AIS CHALLENGE SHARE

```
Day [X] of the 7 Day AIS Challenge, [hook line].

[2-3 sentences on what was built]

What I built:
[skill/tool name], [what it does in one line]
[repeat for each]

One optimization I made:
[specific change or insight]

[Framework/principle that explains it]

#AISChallenge
```

---

## HOW THIS SKILL IMPROVES ITSELF

After every successful post, add to the LEARNED SELECTORS table above:
- Any new selectors discovered
- Any steps that changed
- Any errors encountered and how they were fixed

This file gets smarter every run. Day 3 fumbled. Day 6 flies.

---

## DAY 6 CONNECTION
This playbook is the perfect Day 6 build demonstration.
Day 6 is: "Build a Self-Improving Scheduled Automation"
This skill IS that. It:
1. Runs on a trigger
2. Learns from each execution
3. Writes improvements back into itself
4. Gets faster every time

Demo for Day 6: call /skool-post with Day 6 content → runs clean first try → show the class the playbook file → explain how Day 3 taught Day 6.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
