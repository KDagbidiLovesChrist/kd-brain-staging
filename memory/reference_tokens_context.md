---
name: reference-tokens-context
description: "Plain-English guide to tokens, context windows, and context management in Claude Code. Covers /compact vs /clear, the context ladder, and how to avoid wasting tokens."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Tokens & Context · Plain English Guide

## What Is a Token?

A token is a small piece of text, roughly one word or part of a word. When Claude reads
or writes anything, it uses tokens. Think of tokens like fuel in a car. Every word Claude
reads from your files, every word you type, every word Claude responds with, that's fuel
being used.

**Why it matters:** There's a limit to how much fuel the session can hold (the context
window). And on paid plans, tokens cost money. The smarter you manage them, the better
Claude performs and the less you spend.

**Rough guide:** 1 token ≈ 0.75 words. A 500-line file ≈ ~4,000, 6,000 tokens.

---

## What Is the Context Window?

The context window is how much Claude can hold in its "working memory" at one time.
Imagine a whiteboard. Claude can only see what's written on the whiteboard right now.

- Everything you type goes on the whiteboard
- Everything Claude responds with goes on the whiteboard
- Every file Claude reads goes on the whiteboard
- When the whiteboard is full, older content gets pushed off

**The problem:** When context fills up, Claude starts "forgetting" what was discussed
earlier in the session. Its answers get less accurate. It may repeat itself or miss context.

**The solution:** Manage the whiteboard deliberately, compact or clear when needed.

---

## The Context Ladder

Use this to know what action to take based on how full the session is:

```
[SHORT], Under 30% full
   Status: Green. Work freely. No action needed.
   Signs: Fast responses, Claude remembers everything from early in session.

[MEDIUM], 30, 60% full
   Status: Yellow. Keep an eye on it.
   Action: Finish the current task, then consider /compact before the next big task.
   Signs: Slightly slower, but still accurate.

[LONG], 60, 85% full
   Status: Orange. Act before it becomes a problem.
   Action: Run /compact now. It summarises the conversation so far without losing progress.
   Signs: Claude occasionally misses context from early in the session.

[CRITICAL], 85%+ full
   Status: Red. Do not start new tasks.
   Action: Run /save → then /clear → open new session → run /recover
   Signs: Claude is repeating itself, losing thread, or giving generic answers.
```

---

## /compact vs /clear · What's the Difference?

### /compact
- **What it does:** Summarises the conversation so far into a shorter version, then continues
- **Analogy:** Erasing messy notes on the whiteboard and replacing them with a clean summary
- **When to use:** Mid-session when context is getting long but you're still working on the same task
- **What you keep:** The progress, decisions, and current task context
- **What you lose:** The exact wording of earlier messages (but not the meaning)
- **Best for:** Long build sessions, keeping momentum without starting over

### /clear
- **What it does:** Wipes the entire conversation. Claude starts fresh.
- **Analogy:** Wiping the whiteboard completely clean
- **When to use:** You've finished a task and want a clean slate for a new unrelated task
- **What you keep:** The CLAUDE.md file (Claude re-reads it automatically) + any saved memory files
- **What you lose:** Everything discussed in this session
- **Best for:** Starting a new topic after completing one task

### New Session
- **What it does:** Closes Claude Code entirely and reopens it
- **When to use:** When context is critical AND you've run /save so nothing is lost
- **Recovery:** Run /recover in the new session to get the full briefing back
- **Best for:** Major resets, new day, new project, or after a crash

---

## Context Window Size (Current Models)

| Model | Context Window | Best For |
|-------|---------------|---------|
| Claude Haiku | 200K tokens | Fast, cheap tasks · summaries, formatting |
| Claude Sonnet | 200K tokens | Balanced · most daily work |
| Claude Opus | 200K tokens | Hard thinking · complex builds, deep analysis |

200K tokens sounds huge, but a long session with many file reads fills up faster than you'd think. The 500-line file rule exists precisely to protect context quality.

---

## How to Check Context Usage

In Claude Code's status line at the bottom of the screen, context usage is shown.
You can also run `/status` to see the current session state including context percentage.

When the status line shows context getting full, act. Don't wait until Claude starts
giving poor answers.

---

## Token Cost Awareness

King David is on a paid Claude subscription. Tokens cost money. Here's how to be efficient:

**High-cost actions (use deliberately):**
- Reading large files (every line costs tokens)
- Long back-and-forth conversations (each message adds up)
- Running Claude on very long documents

**Low-cost habits that save money:**
- Keep .md files under 500 lines (the hard rule, enforced by /context)
- Use /compact before starting fresh sections instead of letting context bloat
- Use /clear between unrelated tasks instead of continuing one long session
- Ask Claude to summarise findings before moving on, rather than referencing the raw output

**Best practice:** Think of context like RAM on a computer. Keep it clean and you'll get
better performance. Let it bloat and everything slows down.

---

## The 500-Line Rule

Every file in this setup has a hard limit of 500 lines. This is not arbitrary.

**Why:** Claude reads files in full. A 400-line file = 100% focused attention.
A 1,200-line file = diluted, slower, less accurate. Claude starts missing things.

**What to do when a file approaches 500 lines:**
1. Run /context, it flags files over the limit
2. Identify which sections are historical (old notes, outdated entries)
3. Summarise the historical sections into a compact block
4. Keep the current/active content in full

**Who enforces this:** The /context skill scans all files automatically. Run it at the
start of every session to catch problems before they affect quality.
