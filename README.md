# cbl-challenge-coach

A Claude Code Skill that coaches a solo learner through Challenge-Based Learning (Engage → Investigate → Act) to turn a vague problem instinct into a validated, evidence-tested challenge statement and evidence-traced solution concepts.

It's built to resist the two failure modes that make most "idea coaching" tools useless: converging on a solution before the problem is validated, and asking questions forever without ever moving forward.

## Grounded in

- Dikilitaş, K., Marshall, T., & Shahverdi, M. (2025). *A Practical Guide to Understanding and Implementing Challenge-Based Learning.* Palgrave Macmillan. Open Access. https://doi.org/10.1007/978-3-031-67011-4
- Nichols, M., & Cator, K. (2008). *Challenge Based Learning: Take Action and Make a Difference.* Apple Inc.
- Nichols, M., et al. (2016). *Challenge Based Learning User Guide.* Digital Promise / challengebasedlearning.org
- Perna, S., Recke, M.P., & Nichols, M.H. (2023). *Challenge Based Learning: A Comprehensive Survey of the Literature.* The Challenge Institute.

## Install

**Per-project:** copy `.claude/skills/cbl-challenge-coach/` into your project's `.claude/skills/` directory.

**Global (all projects):**
```bash
ln -s "$(pwd)/.claude/skills/cbl-challenge-coach" ~/.claude/skills/cbl-challenge-coach
```

No other setup, dependencies, or MCP servers required — it only uses tools already available in Claude Code (Read/Write/Edit and optionally WebSearch/WebFetch for labeled secondary research in Investigate).

## Use

Open Claude Code in any project directory (a fresh empty folder works fine — one per challenge) and just describe a problem or business idea you're turning over. The Skill triggers automatically; no slash command needed.

State persists in a `challenge.md` file it creates in the project root — that's what survives across sessions, not conversation memory. Starting a new challenge just means starting in a new directory.

## How it works

- **Engage** — Big Idea → many essential questions → one essential question → an actionable Challenge statement. Actively catches vague, oversized, and solution-disguised challenges rather than accepting them as-is.
- **Investigate** — guiding questions, evidence gathering (Claude may do light, clearly-labeled secondary research; you own primary research), explicit confirmation-bias checks.
- **Act** — generates multiple solution concepts, each traced back to specific Investigate-phase evidence, converging on one direction to test next. Stops there — no implementation planning, prototyping, or MVP-building.

Phase transitions happen by checkpoint confirmation: Claude states when it thinks a phase's exit criteria are met and asks before advancing, but never advances silently and never blocks you if you want to proceed anyway.

See `.claude/skills/cbl-challenge-coach/references/` for the full mentor behavior, and `evals/scenarios.md` for the manual test scenarios used to validate it.
