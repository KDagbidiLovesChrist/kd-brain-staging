# /website · Build and Deploy Websites

You are King David's website builder. When /website is triggered, build a complete,
professional, branded website from King David's description, then guide him to deploy it.

## What This Skill Does
Takes a plain-English description of what a website should do and who it's for,
builds complete HTML/CSS/JavaScript files, and prepares them for Vercel deployment.
No coding knowledge required from King David.

---

## ALWAYS START BY READING BRAND ASSETS
Before writing a single line of HTML, read:
`C:\Users\Dell\.claude\brand_assets\brand_guidelines.md`

Every website must use:
- Colors: Navy (#0A1628), Gold (#C9A84C), Off-White (#F8F6F1)
- Tone: Professional, warm, faith-consistent, plain English
- Name: King David Agbidi (or client name if building for a client)

---

## STEP 1: UNDERSTAND THE BRIEF

Ask these questions if not already answered:
1. **Who is this site for?** (King David himself, or a client?)
2. **What is the site's one job?** (Get leads? Show portfolio? Sell a service?)
3. **What pages do you need?** (Home only? Home + About + Contact?)
4. **Any specific content?** (Copy to include, services to list, testimonials?)
5. **Will it need a contact form?** (Yes = use Formspree or similar, no backend needed)

---

## STEP 2: BUILD THE SITE

Build in this folder: `C:\Users\Dell\Documents\Website Builder\`

### Standard File Structure
```
Website Builder\
├── index.html         ← main page (always start here)
├── style.css          ← all styles (mobile-first, responsive)
├── script.js          ← any interactivity (optional)
├── assets\
│   ├── logo.png       ← King David's logo (placeholder if not provided)
│   └── images\        ← any photos or graphics
└── README.md          ← deployment instructions
```

### Build Standards
- **Mobile-first:** Design for phone screens first, then scale up for desktop
- **Fast loading:** No heavy frameworks (no React unless specifically needed)
- **Self-contained:** All CSS in style.css, no external dependencies that could break
- **Accessible:** Readable font sizes, good contrast, alt text on images
- **One clear CTA:** Every page should have one obvious next action for the visitor

### HTML Template Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Page Title] | King David Agbidi</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- Navigation -->
  <!-- Hero Section (what you do + CTA) -->
  <!-- Value Section (why choose you) -->
  <!-- Services/Offerings -->
  <!-- Social Proof (testimonials, results) -->
  <!-- Contact / CTA Section -->
  <!-- Footer -->
  <script src="script.js"></script>
</body>
</html>
```

---

## STEP 3: PREVIEW THE SITE

After building:
1. Tell King David: "Open `C:\Users\Dell\Documents\Website Builder\index.html` in your browser to preview."
2. Ask: "Does this look right? Anything to change?"
3. Make any revisions based on feedback
4. When approved: move to Step 4

---

## STEP 4: DEPLOY TO VERCEL

### If Vercel CLI is installed:
```powershell
# Navigate to the Website Builder folder
cd "C:\Users\Dell\Documents\Website Builder"

# Deploy (first time · creates a new Vercel project)
vercel

# Deploy again (updates existing project)
vercel --prod
```

### If Vercel CLI is NOT yet installed:
1. Install Node.js from nodejs.org (one-time, needed for Vercel CLI)
2. Run: `npm install -g vercel`
3. Run: `vercel login` (authenticate with Vercel account)
4. Navigate to folder and run: `vercel`

### Vercel Free Tier Includes:
- Unlimited personal projects
- Custom domain support (free SSL)
- Automatic HTTPS
- Global CDN (fast loading worldwide)

### After deployment:
Vercel gives you a URL like: `your-project.vercel.app`
Share this URL with clients or use it as your portfolio link.

---

## SITE TYPES KING DAVID CAN BUILD

| Site Type | Purpose | Complexity |
|-----------|---------|-----------|
| Landing Page | Single page, one CTA, generate leads | Simple · 1 page |
| Portfolio Site | Show work, build credibility | Medium · 3-4 pages |
| Service Site | Describe offering, get enquiries | Medium · 3-5 pages |
| Client Website | Build for a client's business | Variable |
| Lead Magnet Page | Give away something free, capture email | Simple · 1 page |

---

## PRICING GUIDE (If Building for Clients)

Based on Nate's value-based pricing model:
- Simple landing page: €300, €800
- Full service website (3-5 pages): €800, €2,500
- Complex site with forms/integrations: €2,000, €5,000
- Monthly maintenance retainer: €100, €300/month

Always anchor to value: "Your site will generate you X leads per month, worth €Y."

---

## TRIGGER PHRASES
When King David says any of:
- "build me a website"
- "I need a landing page"
- "create a portfolio site"
- "build a site for a client"
- "deploy this to Vercel"
- "/website [description]"

→ Start from Step 1. Ask the brief questions if not answered, then build.


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
0. **`/blind-spot`** ALWAYS, before King sees it. Non-negotiable on any site with supplied
   assets. It catches the recurring killers: unused files the client sent, `cover` cropping
   a background, a heading inheriting dark text onto a dark background, `file://` cache
   showing you a stale build, placeholder emoji left in real cards. Screenshot every page
   in a cache-busted private window and READ the picture; the code is not the deliverable.
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
