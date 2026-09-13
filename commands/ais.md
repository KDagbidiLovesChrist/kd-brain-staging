# /ais · AIS Classroom Intelligence Skill

**Trigger:** `/ais` or `/ais [keyword]`
**Purpose:** Single-trigger access to everything extracted from the AIS+ classroom, PDFs, JSON configs, workflow patterns, and env templates. Token-efficient: loads only what you ask for.
**Context cost:** ~300 tokens base | ~800 tokens with sub-file

---

## STEP 1 · Read the Master Index
Read `C:\Users\Dell\.claude\knowledge\ais_resources\ais_classroom_master.md`

---

## STEP 2 · Route by Keyword

If no keyword → go to STEP 3 (WOW Dashboard)

| Keyword | Load This File | What to Show |
|---------|---------------|--------------|
| `setup` | ais_pdfs.md | n8n MCP preflight checklist · step by step |
| `env` | ais_json_configs.md | The full .env template with instructions |
| `config` | ais_json_configs.md | The Claude Code settings.json block for n8n-mcp |
| `workflow` | ais_workflows.md | n8n → Claude Code translation table + workflow patterns |
| `enhance` | ais_workflows.md | Enhancement Philosophy checklist (error/quality/UX) |
| `numbers` | ais_classroom_master.md | Key metrics table only |
| `map` | ais_classroom_master.md | Ecosystem mapping diagram |
| `apply [skill]` | ais_workflows.md | How to upgrade that specific skill using classroom patterns |

---

## STEP 3 · WOW Dashboard (no keyword)

Print this exact format:

```
═══════════════════════════════════════════════
/ais, AIS CLASSROOM LOADED
═══════════════════════════════════════════════

WHAT I KNOW
───────────
• n8n MCP preflight checklist (PDF from lesson 1.4)
• Full .env template for n8n-mcp integration
• Claude Code settings.json block (add n8n in 2 mins)
• 2,352 n8n workflow templates available via npx n8n-mcp
• Workflow translation: n8n nodes → Claude Code steps
• Enhancement Philosophy: how to upgrade any skill

TOP ACTION RIGHT NOW
─────────────────────
→ Add n8n-mcp to settings.json → fills a gap in the ecosystem
  Takes 2 minutes. Gives Claude access to 1,650 n8n nodes + 2,352 templates.

KEYWORD SHORTCUTS
──────────────────
/ais setup     → n8n MCP installation steps
/ais env       → .env template (copy-paste ready)
/ais config    → settings.json block
/ais workflow  → n8n → Claude Code translation
/ais enhance   → upgrade any skill (error/quality/UX)
/ais map       → how this fits the full ecosystem

METRICS CHECK
─────────────
Less time ✓, one trigger, no searching
More money ✓, every pattern maps to a service you sell
Quality ✓, extracted from source, not guessed
WOW factor ✓, entire classroom in one command
═══════════════════════════════════════════════
```

---

## STEP 4 · If Keyword is `apply [skill]`

1. Read `ais_workflows.md` (Enhancement Philosophy section)
2. Read the skill file at `C:\Users\Dell\.claude\commands\[skill].md`
3. Suggest specific enhancements:
   - What error handling is missing?
   - What output quality improvements can be made?
   - What would make it easier to trigger or read?
4. Present as a numbered list: "Here's how to upgrade /[skill] using AIS patterns"
5. Ask: "Want me to apply these now?"

---

## STEP 5 · Save to Obsidian (optional)
If the user says "save this" after any /ais output:
- Write a structured note to Obsidian vault (port 27124)
- Title: "AIS Resource, [topic]"
- Content: what was shown + action taken

---

## NOTES
- This skill is READ-ONLY, it never changes existing skills without approval
- All sub-files are in: `C:\Users\Dell\.claude\knowledge\ais_resources\`
- Master file hard limit: 300 lines, compress if it grows past that
- n8n-mcp GitHub: github.com/czlonkowski/n8n-mcp


---

## THE GATE · nothing ships until it passes (Rule #21)
Before this skill's output is "done":
1. **Real data, no fabrication** (Rule #20): real numbers, matched to the reference, nothing invented.
2. **`/humanize`** anything a human will read: strip the AI tells, ZERO em-dashes or en-dashes, sound like King. [[feedback-sound-human-not-ai]]
3. **`/qa-master`** for anything client-facing or irreversible, then **King approves** -> Trusted.
4. **Aim at the goal** (`tools\goals.py`): money, audience, or theosis, then measure.
5. **Engine reflex** (Rule #25, `/engine`): flag trivial or non-trivial + the lane (Llama/Claude); on any real build state the stack (skill + tool + prompt + logic) up front.

"It ran" is not the bar. On-brand + true + human + aimed + verified is.
