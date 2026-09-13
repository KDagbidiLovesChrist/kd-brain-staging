# Video Study · Agent Loops (Owen, Claude Code + Codex)

**Source:** https://www.youtube.com/watch?v=RVEaDvh6f5A · Watched 2026-06-17 via `/watch`. Confidence 5/5.

## Objective lesson (one line)
An "agent loop" = run an agent on a trigger that **reads state → does work → writes state → repeats**,
with a visible **control plane** and hard **guardrails** so it's safe and trustworthy.

## The pattern (Owen's exact framing)
`Schedule/Event trigger → READ state (control plane) → DO work → WRITE state → sleep/repeat`
- **Control plane = GitHub Issues / Linear** (the shared place agents read work from + report back to).
- Example: a **Manager loop** triages the backlog (labels: agent-ready, risk-low, type-feature); a
  **Worker loop** polls issues → writes code → runs tests → spawns a code-review sub-agent → opens a PR
  with evidence (test output).
- Files: `backlog-manager.yml` (GitHub Action, cron/workflow_dispatch), `SKILL.md`, worker prompt file.
- Setup: GitHub Action using `anthropic/claude-code-action@v1` + `ANTHROPIC_API_KEY`/`GITHUB_TOKEN`;
  run with `mode: dry-run` first, then `apply`.

## Production guardrails (the important part · for KD's future autonomous work)
1. **Control plane / visibility**, never run agents unmonitored; a place to see what they did.
2. **Guardrails / least privilege**, agents get destructive power only if essential (manager = labels only).
3. **Clean environment**, abort if dirty branch / uncommitted changes.
4. **Sequential over parallel early**, avoids conflicts.
5. **Evidence + reporting**, agent must show proof (tests/screenshots) in the ticket.
6. **Rate/cost limits**, cap issues per run (e.g. 3) to contain tokens + blast radius.
7. **Skill-based**, call lightweight skills, don't embed huge prompts in the workflow.
8. **Secondary review**, linters/static analysis/second AI reviewer before merge.
9. **Human feedback loop** at the PR stage. 10. **Eval metrics** (rework rate, first-pass success).

## What it means for KD / what to DO
- ✅ Confirms (again) our SessionStart→Stop loop is the right read/write pattern.
- 🔜 When we make anything autonomous (Upwork watcher, client automations, `/loop`, `/goal`): apply the
  guardrails above, **dry-run→apply, cost caps, evidence, least privilege.** This is also Cole's
  "security = hooks not prompts" from the other video.
- Not for KD now: full GitHub-Actions agent armies (engineering-heavy). Bank the guardrails for later.
