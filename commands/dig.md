# /dig · King's voice-friendly shortcut for /research

**Trigger:** King types `/dig [question]` OR says "dig into X", "dig on X", "dig into this".
**What it is:** a plain alias. "Dig" is the short word King says out loud, it runs the exact same research engine.

## Action
Run the full `/research` skill exactly as written in `commands/research.md` on King's question:
- Pick the gear first (Rule #17): quick for a lookup, the STORM 5-lens deep layer for anything King will act on.
- Same 5 lenses (practitioner, academic, skeptic, economist, historian), contradiction map, source verdicts (confirmed / corrected / demoted), goal weighting, and the gate.

All the logic lives in `commands/research.md`. Nothing is duplicated here, this file just gives King a shorter word.
