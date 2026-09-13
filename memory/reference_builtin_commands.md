---
name: reference-builtin-commands
description: "Every Claude Code built-in slash command, keyboard shortcut, and permission mode explained in plain English. King David's cheat sheet for controlling Claude Code natively."
metadata: 
  node_type: memory
  type: reference
  originSessionId: 4b621969-d6bd-419c-9280-c6a4e0333ae8
---

# Claude Code Built-in Commands · Complete Reference

These are Claude Code's OWN commands, built into the tool itself. Different from King
David's custom /skills (like /save, /scrape, /newsletter). These are the controls for
the Claude Code engine itself.

---

## THE THREE MODES (Most Important)

Before commands, understand the three modes. They control how much Claude does on its own.

### Plan Mode
**What it does:** Claude ONLY thinks and plans. It cannot edit files, run scripts, or
make changes. It just reasons and presents a plan.
**When to use:** At the start of any significant task. Forces you to review before Claude acts.
**How to activate:** Click the mode selector at the bottom of Claude Code → Plan Mode
**Analogy:** Claude is an architect drawing blueprints. It designs but doesn't touch the bricks.

### Ask Mode (default)
**What it does:** Claude asks permission before every file edit or command it runs.
You approve or deny each action.
**When to use:** When working on something sensitive or when you want full control over each step.
**How to activate:** Default mode. Or select "Ask before edits" in the mode selector.
**Analogy:** Claude is a contractor who checks with you before drilling any hole.

### Bypass/Auto Mode
**What it does:** Claude executes everything automatically without asking permission.
It reads files, writes files, runs scripts, all on its own.
**When to use:** After you've reviewed the plan and trust Claude to execute. Long builds.
**How to activate:** Select "Bypass permissions" in the mode selector (or enable in settings.json)
**Analogy:** Claude is a trusted employee who you've briefed fully, you go do other work,
they execute, you check the result at the end.
**Warning:** Only use this when you've reviewed the plan and trust the task. Claude will
make changes without asking.

---

## SLASH COMMANDS (Built-in)

### /clear
**What it does:** Wipes the entire conversation clean. Fresh start.
**When to use:** Between unrelated tasks. You've finished building X, now starting Y.
**What stays:** CLAUDE.md (re-read automatically on next message). Saved files. Memory.
**What goes:** Everything discussed this session.
**Command:** Type `/clear` in the chat input

### /compact
**What it does:** Summarises the current conversation into a shorter version, then
continues. Like compressing a file without losing the content.
**When to use:** Mid-session when context is getting long (orange on the context ladder)
but you're still working on the same task.
**What stays:** The summary of what was discussed + current task context
**What goes:** The exact wording of earlier messages (meaning is kept, not word-for-word)
**Command:** Type `/compact` in the chat input
**Pro tip:** You can say `/compact, focus on [specific topic]` to tell it what matters most

### /model
**What it does:** Switches which Claude model is powering your session.
**Models available:**
- `claude-haiku-4-5`, Fastest and cheapest. Good for simple tasks (formatting, summaries)
- `claude-sonnet-4-6`, Balanced. Good for most daily work. (Default)
- `claude-opus-4-7`, Most powerful. Best for hard thinking, complex builds, strategy
**When to use:**
- Switch to Haiku for quick formatting or simple rewrites (saves tokens + speed)
- Switch to Opus when you need the deepest thinking (complex architecture, hard problems)
- Stay on Sonnet for normal daily work
**Command:** Type `/model` to see options, then select

### /status
**What it does:** Shows the current session state, model in use, context usage percentage,
session ID, and configuration.
**When to use:** When you want to check how full the context is, or which model is active.
**Command:** Type `/status`

### /cost
**What it does:** Shows the token spend for this session, how many tokens used and the
approximate cost.
**When to use:** If you want to track spending or see if a task was expensive.
**Command:** Type `/cost`

### /config
**What it does:** Opens the Claude Code settings. View and change configuration options
like theme, auto-update channel, effort level.
**When to use:** When you want to change a setting without editing settings.json manually.
**Command:** Type `/config`

### /permissions
**What it does:** Shows the current permission state, what tools are allowed without
prompting, what requires approval.
**When to use:** To check what Claude is currently allowed to do automatically.
**Command:** Type `/permissions`

### /memory
**What it does:** Manages Claude's memory system. Can add, view, or remove memory entries.
**When to use:** If you want to manually add something to Claude's long-term memory.
**Note:** In this setup, memory is managed through the memory\ folder system and /save skill.
Use /save for most memory tasks.
**Command:** Type `/memory`

### /help
**What it does:** Shows available commands and basic help.
**Command:** Type `/help` or press `?`

---

## KEYBOARD SHORTCUTS

| Shortcut | What It Does |
|----------|-------------|
| `Escape` | Cancel the current running action (stops Claude mid-task) |
| `Ctrl + C` | Interrupt · same as Escape but more forceful |
| `↑ Arrow` | Scroll back through previous messages you sent |
| `Ctrl + K` | Clear the input box |
| `Enter` | Send message |
| `Shift + Enter` | New line without sending (for multi-line messages) |

---

## PERMISSIONS SYSTEM

### How Permissions Work
Claude Code has a list of tools it can use: read files, write files, run Python, run
PowerShell, call MCPs (Firecrawl, Playwright), etc.

Each tool can be:
- **Pre-approved** (in allowedTools in settings.json) → Claude uses it without asking
- **Ask-mode** → Claude asks permission each time
- **Blocked** → Claude cannot use it at all

### King David's Current Permission Setup (settings.json)
Pre-approved tools (no prompts):
- Reading files anywhere in the system
- Running Python scripts
- Running specific PowerShell commands
- Firecrawl MCP (scraping, search)
- Playwright MCP (browser automation)

### Adding New Permissions
To add a tool to the allowed list without prompting:
1. Open `C:\Users\Dell\.claude\settings.json`
2. Find the `"allowedTools"` section
3. Add the tool name as a new entry
4. Save, takes effect immediately

Or use the `/update-config` skill to add permissions safely with Claude's help.

### The Three Permission Modes
- **Plan Mode** → No permissions needed (Claude only plans, never acts)
- **Ask Mode** → Claude asks before each action (safe, slow)
- **Bypass Mode** → All pre-approved tools fire without prompting (fast, requires trust)

**Rule of thumb:** Plan first. Review. Then switch to Bypass for the execution.

---

## @FILE TAGGING

One of the most powerful features, not a slash command, but critical to know.

**What it does:** When you type `@` followed by a filename, Claude directly reads that
specific file as part of your message. Like attaching a document to an email.

**How to use:** Type `@` and start typing the filename, autocomplete appears.
Example: `@brand_guidelines.md` or `@newsletter_sop.md`

**When to use:**
- Including a specific workflow for Claude to follow
- Referencing brand assets when asking Claude to write something
- Pointing Claude at a specific tool file when debugging
- Adding context from one project while working in another

**Pro tip from Nate's video:** Before asking Claude to build a newsletter, tag
`@brand_guidelines.md` so it reads your brand before generating a single word.

---

## ULTRATHINK

Not a slash command, a prompt modifier. One of the most powerful tricks.

**What it does:** When you add "ultrathink" anywhere in your message, Claude activates
extended reasoning, it thinks much harder, considers more angles, catches more edge cases.

**When to use:**
- Complex architectural decisions ("ultrathink, should I build this as one script or three?")
- Hard debugging ("ultrathink, why is this scraper failing on that site?")
- Strategy questions ("ultrathink, what's the best way to price this for a client?")
- Anything where being wrong is expensive

**Cost:** Uses more tokens. Worth it for hard problems.
**Example:** "ultrathink, help me design the architecture for the agent team"

---

## FAST MODE

**What it does:** Switches to faster output generation. Uses Claude Opus but with
quicker responses (not downgrading to a smaller model).
**When to use:** When you need speed more than maximum depth.
**How to activate:** Type `/fast` to toggle on/off

---

## CUSTOM STATUS LINE

**What it is:** The information bar at the bottom of Claude Code. You can customise
what it shows.
**Default shows:** Model name, context usage percentage
**Can show:** Custom text, session info, current project name, whatever is useful
**How to configure:** Use the /statusline-setup skill or edit settings.json directly

---

## QUICK REFERENCE CARD

```
MODE SELECTOR:
  Plan Mode    → Claude thinks only, never acts
  Ask Mode     → Claude asks before each action (safe)
  Bypass Mode  → Claude acts automatically (fast)

SLASH COMMANDS:
  /clear       → Wipe conversation, fresh start
  /compact     → Summarise + continue (free context)
  /model       → Switch Claude model (Haiku/Sonnet/Opus)
  /status      → Check context %, model, session info
  /cost        → See token spend this session
  /config      → View/change settings
  /permissions → See what's allowed
  /help        → Show available commands

KEYBOARD:
  Escape       → Cancel running action
  Ctrl+C       → Force interrupt
  ↑ Arrow      → Previous messages
  Enter        → Send
  Shift+Enter  → New line

POWER TRICKS:
  @filename    → Tag a file into your message
  ultrathink   → Activate deep reasoning mode
  /fast        → Faster output mode
```
