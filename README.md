# cbl-challenge-coach

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-5A45FF)](https://code.claude.com/docs/en/skills)
[![Grounded in CBL research](https://img.shields.io/badge/Grounded%20in-CBL%20research-blue)](#grounded-in)

**A Claude Code Skill that coaches a solo learner through Challenge-Based Learning — Engage, Investigate, Act — turning a vague problem instinct into a validated challenge statement and evidence-traced solution concepts.**

It exists to resist the two failure modes that make most "idea coaching" useless: converging on a solution before the problem is validated, and asking questions forever without ever moving forward.

---

## What it actually does (and doesn't)

| It does | It doesn't |
|---|---|
| Helps you find a problem worth solving, even starting from nothing | Assume you already have an idea |
| Pushes back on vague, oversized, or solution-disguised "challenges" | Accept the first framing you offer |
| Runs light, clearly-labeled secondary research (market signals, existing solutions) | Treat its own research as proof, or a substitute for primary research |
| Generates and compares multiple solution concepts, each traced to specific evidence | Let you — or itself — converge on one favorite before alternatives exist |
| Stops at a validated solution *concept* | Plan implementation, prototype, or build an MVP |
| Persists state in a `challenge.md` file that survives across sessions | Rely on conversation memory for facts that matter later |

Read that table before installing — it's the actual scope of v1, not a feature wishlist.

## Install

**Recommended — plugin marketplace** (this repo is itself a marketplace; no cloning required):
```
/plugin marketplace add DasonTio/cbl-challenge-coach
/plugin install cbl-challenge-coach@cbl-challenge-coach
```

**Manual — clone and link** (better if you want to read the skill before trusting it):
```bash
git clone https://github.com/DasonTio/cbl-challenge-coach.git
ln -s "$(pwd)/cbl-challenge-coach/.claude/skills/cbl-challenge-coach" ~/.claude/skills/cbl-challenge-coach
```
Or copy `.claude/skills/cbl-challenge-coach/` into one project's `.claude/skills/` instead of linking it globally, if you only want it available in a single place.

No dependencies, API keys, or MCP servers required. It only uses tools already available in Claude Code — Read/Write/Edit for its state file, and optionally WebSearch/WebFetch for labeled secondary research during Investigate.

## Use

Open Claude Code in any directory (a fresh empty folder works fine — one per challenge) and just talk. **You don't need a formed idea** — "I don't know what to work on, help me find something" is a valid opener; the Engage phase is built to handle arriving with nothing.

The Skill triggers automatically from context — no command required. To force it regardless of phrasing, invoke it explicitly:
```
/cbl-challenge-coach
```

State lives in a `challenge.md` file the Skill creates in the project root. That's what survives across sessions, not conversation history — starting a new challenge just means starting in a new directory.

## How it works

| Phase | What happens | Exits when |
|---|---|---|
| **Engage** | Big Idea → many essential questions → one essential question → a Challenge statement | The Challenge is specific, actionable, owned by you — and not secretly a solution |
| **Investigate** | Guiding questions, hybrid research (you do primary, Claude does labeled secondary), explicit confirmation-bias checks | The Challenge has survived contact with real evidence, not just your first instinct |
| **Act** | Generates 2–3+ distinct solution concepts, each traced to specific Investigate-phase evidence, converges on one direction | You've chosen a direction worth testing next — implementation is intentionally out of scope |

Phase transitions happen by checkpoint confirmation: Claude states when it thinks a phase is done and asks before advancing — never silently, and never refusing to advance if you insist anyway.

## Validated against

Nine adversarial scenarios, each run against a fresh Claude Code instance with zero memory of this repo's design discussion. Full input/expected-behavior/prohibited-failure-mode spec for each is in [`evals/scenarios.md`](.claude/skills/cbl-challenge-coach/evals/scenarios.md).

| # | Scenario | Result |
|---|---|---|
| 1 | Premature solution disguised as a problem (Engage) | ✅ Pass |
| 2 | One-sided evidence / confirmation bias (Investigate) | ✅ Pass |
| 3 | Secondary research mislabeled as proof (Investigate) | ✅ Pass |
| 4 | Converging to Act with real evidence traceability | ✅ Pass |
| 5 | Direct explanation request, not Socratic deflection | ✅ Pass |
| 6 | Advancing a phase before its exit criteria are met | ✅ Pass |
| 7 | Low-quality / unverifiable source | ✅ Pass |
| 8 | Learner disagrees with the Skill's concern | ✅ Pass |
| 9 | Cross-session state resume without hallucination | ✅ Pass |

These are manual scenarios, not an automated suite — there's currently no built-in runner for Skill evaluations. Re-run them yourself before trusting a change to the reference files.

## Grounded in

- Dikilitaş, K., Marshall, T., & Shahverdi, M. (2025). *A Practical Guide to Understanding and Implementing Challenge-Based Learning.* Palgrave Macmillan. Open Access. https://doi.org/10.1007/978-3-031-67011-4
- Nichols, M., & Cator, K. (2008). *Challenge Based Learning: Take Action and Make a Difference.* Apple Inc.
- Nichols, M., et al. (2016). *Challenge Based Learning User Guide.* Digital Promise / challengebasedlearning.org
- Perna, S., Recke, M.P., & Nichols, M.H. (2023). *Challenge Based Learning: A Comprehensive Survey of the Literature.* The Challenge Institute.

## Repository structure

```
.
├── .claude-plugin/
│   └── marketplace.json          # makes /plugin install work
└── .claude/skills/cbl-challenge-coach/
    ├── SKILL.md                  # overview + phase/checkpoint logic (~40 lines, always loaded)
    ├── references/                # loaded only when Claude needs the detail
    │   ├── engage.md
    │   ├── investigate.md
    │   ├── act.md
    │   ├── mentor-roles.md
    │   └── challenge-artifact.md  # challenge.md schema
    └── evals/
        └── scenarios.md
```

No engine, proxy, CLI, or SDK — the entire product is these instruction files. That's a deliberate scope choice, not an early stage of something bigger.

## License

MIT — see [LICENSE](LICENSE).
