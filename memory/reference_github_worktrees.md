---
name: reference-github-worktrees
description: "What git is, how to set it up on Windows, how to push King David's projects to GitHub, and how worktrees enable safe parallel development. Connects to trigger.dev deployment."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# GitHub & Git Worktrees · Step-by-Step Guide

## What Is Git? (Plain English)

**Git is a time machine for your code.**

Every time you save a version of your project with git (called a "commit"), it's like
taking a photo. If something breaks later, you can go back to any photo. You never lose
working code. You always have a safe fallback.

**GitHub** is where you store those photos in the cloud. It's like Google Photos, but
for code. Your projects are backed up, shareable, and deployable from there.

---

## What Are Worktrees?

**Worktrees are parallel working copies of the same project.**

Imagine you have the newsletter project working perfectly. You want to try a new feature, but you don't want to break what's already working while you experiment.

With a worktree, you create a parallel copy (a different "branch") of the project.
You experiment in the copy. If it works, you merge it into the main version.
If it breaks, you delete the copy. The main version is never touched.

**Analogy:** It's like having a photocopy of a document to scribble ideas on. The original
stays clean. You test on the copy. If you like it, you update the original.

---

## WHY THIS MATTERS FOR KING DAVID

1. **Safe experimentation:** Try upgrading the scraper without risking the working version
2. **Version history:** See exactly what changed, when, and why
3. **Deployment pipeline:** GitHub → trigger.dev → automated newsletter runs 24/7
4. **Backup:** Projects are safe even if laptop dies
5. **Client delivery:** Share a GitHub repo instead of emailing ZIP files

---

## STEP 1: INSTALL GIT ON WINDOWS

Open PowerShell and run:
```powershell
winget install Git.Git
```

Wait for it to install. Then close and reopen PowerShell to reload.

Verify it worked:
```powershell
git --version
# Should show: git version 2.x.x
```

---

## STEP 2: SET UP YOUR IDENTITY

Git records who made each change. Set your name and email once:
```powershell
git config --global user.name "King David Agbidi"
git config --global user.email "Kingdavidagb@icloud.com"
```

---

## STEP 3: CREATE A GITHUB ACCOUNT

1. Go to github.com
2. Click "Sign up"
3. Use email: Kingdavidagb@icloud.com (or your preferred email)
4. Choose username: something professional like `kingdavidagbidi` or `kda-automation`
5. Verify email
6. Done, your GitHub profile is at: `github.com/[your-username]`

---

## STEP 4: CREATE YOUR FIRST REPOSITORY

A repository (repo) = one project on GitHub.

**Option A, From GitHub website:**
1. Go to github.com → click "+" → "New repository"
2. Name it: `newsletter-automation` (no spaces, use hyphens)
3. Set to Private (keeps client work confidential)
4. Do NOT initialise with README (you'll push existing files)
5. Click "Create repository"
6. GitHub shows you the commands to push, copy them

**Option B, From GitHub MCP (when set up):**
Ask Claude: "Create a GitHub repo called newsletter-automation, private"
Claude handles it directly.

---

## STEP 5: PUSH THE NEWSLETTER PROJECT TO GITHUB

```powershell
# Navigate to the project
cd "C:\Users\Dell\Documents\Newsletter Demos"

# Initialise git
git init

# Create a .gitignore FIRST (to protect API keys)
# (This should already exist · verify it includes .env)

# Stage all files
git add .

# Create first commit
git commit -m "Initial commit, newsletter automation pipeline"

# Link to GitHub repo (replace with your actual URL)
git remote add origin https://github.com/[your-username]/newsletter-automation.git

# Push to GitHub
git push -u origin main
```

Your newsletter project is now on GitHub. Repeat for the Scrapers project.

---

## STEP 6: HOW TO USE WORKTREES (Safe Experimentation)

### Create a worktree (for experimenting)
```powershell
cd "C:\Users\Dell\Documents\Newsletter Demos"

# Create a new branch in a separate folder
git worktree add "../Newsletter Demos EXPERIMENT" experiment-branch
```

Now you have two folders:
- `Newsletter Demos\`, the main working version (safe)
- `Newsletter Demos EXPERIMENT\`, your experimental copy

### Work in the experiment, leave the main safe
```powershell
cd "C:\Users\Dell\Documents\Newsletter Demos EXPERIMENT"
# Make changes, test, break things · main version is untouched
```

### If the experiment works · merge it in
```powershell
cd "C:\Users\Dell\Documents\Newsletter Demos"
git merge experiment-branch
```

### If the experiment fails · delete the worktree
```powershell
git worktree remove "../Newsletter Demos EXPERIMENT"
git branch -d experiment-branch
```

The main version was never touched. Safe.

---

## STEP 7: CONNECT GITHUB TO TRIGGER.DEV (24/7 Deployment)

Once the newsletter project is on GitHub:
1. Create trigger.dev account at trigger.dev (free tier)
2. Connect your GitHub account
3. Select the `newsletter-automation` repo
4. Add environment variables (your API keys from .env)
5. Set schedule: "Every Monday at 8am"
6. Deploy, trigger.dev reads your tools\ and runs them on schedule

From this point, the newsletter sends itself. You don't touch a thing.

---

## STATUS TRACKER

```
[ ] Step 1: Git installed (winget install Git.Git)
[ ] Step 2: Identity configured (name + email)
[ ] Step 3: GitHub account created
[ ] Step 4: Newsletter repo created on GitHub
[ ] Step 5: Newsletter project pushed to GitHub
[ ] Step 5b: Scrapers project pushed to GitHub
[ ] Step 6: Worktrees understood, used for safe experimentation
[ ] Step 7: trigger.dev connected → newsletter runs automatically
```

---

## DAILY GIT WORKFLOW (Once Set Up)

```powershell
# After making changes to a project:
git add .
git commit -m "What you changed and why"
git push

# To see history of changes:
git log --oneline

# To go back to a previous version:
git checkout [commit-hash]

# To create a safe experiment:
git worktree add "../[project] EXPERIMENT" experiment-name
```

---

## QUICK REFERENCE

```
GIT = Time machine for code (local)
GITHUB = Cloud storage for git (online)
WORKTREE = Safe copy for experimentation

KEY COMMANDS:
  git init            → Start tracking a project
  git add .           → Stage all changes
  git commit -m "msg" → Save a version
  git push            → Upload to GitHub
  git log --oneline   → See history
  git worktree add    → Create safe experiment copy

WORKFLOW:
  Make changes → git add . → git commit → git push
  Experiment → git worktree → test → merge or delete
  Deploy → GitHub → trigger.dev → runs 24/7
```
