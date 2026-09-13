# Three folders say "skill". Here is which is which.

*Written 2026-08-23 during the restructure. Nothing was moved, this file exists because the
three names are genuinely easy to confuse and that confusion was costing time.*

| Folder | What it holds | Count today | How you use it |
|---|---|---|---|
| `commands/` | King's own `/command` skills, the **Logic** layer (from *Logos*). Hand written markdown, one file per command. | 57 `.md` files | Type `/aide`, `/money`, `/qa` etc. in Claude Code |
| `skills/` | Third-party / plugin skills already **installed** into this brain. One folder per skill. | 57 folders | Invoked by name via the Skill tool |
| `skill-forge/` | The **workshop**, not a skill store. Where candidate skills get scouted, scored and decided on before any of them reach `skills/`. | Its own project (MANIFEST, commands, tools, sessions, vendor, workflow) | Read `skill-forge/MANIFEST.md`, or run `/find-skills` |

## The one-line version

- `commands/` = **mine**, written here.
- `skills/` = **theirs**, installed here.
- `skill-forge/` = **the shortlist**, not installed yet.

`skill-forge/MANIFEST.md` is a catalogue with a status per candidate
(🗂️ Catalogued · 🔬 Evaluated · ✅ Installed · ⏭️ Skipped · 🔴 Hold). A skill marked ✅ there
is one that has since landed in `skills/`. So `skill-forge` is the pipeline and `skills` is
the destination, they are not two competing copies of the same thing.

## Also nearby, and also not a skill folder

- `agents/` (5 files) holds **subagent** definitions (accountant, memory-keeper, qa-verifier,
  scout, writer). Different concept: an agent is who does the work, a skill is how it is done.
- `plugins/` holds the plugin **marketplace cache and install data**, machine-managed. The
  human-readable result of what is installed is `skills/`.

## Related indexes

- `knowledge/SKILLS_INDEX.md` lists every command skill and installed plugin skill together.
- `skill-forge/MANIFEST.md` lists candidates and their verdicts.
