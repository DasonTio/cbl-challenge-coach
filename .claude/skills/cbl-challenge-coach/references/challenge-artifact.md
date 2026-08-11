# Challenge Artifact (challenge.md)

## Contents
- Purpose
- Template
- Update rules

## Purpose
`challenge.md` is the single source of truth for a challenge — not the conversation. Claude Code sessions get summarized/compacted as they grow, and a new session has zero memory of a previous one; this file is what survives both. Keep it as distilled state, not a transcript.

## Template
Create this file at the start of a new challenge, in the project root:

```markdown
# Challenge: [working title]

**Current phase:** engage

## Big Idea
[the broad problem-space, once surfaced]

## Essential Questions Considered
- [question 1]
- [question 2]
- ...

## The Challenge
> [the single actionable Challenge statement, once formulated]

Set on: [date]. Revised: [date, if applicable — note what changed and why].

## Evidence Log
| Claim | Source type (primary/secondary) | Detail | Date |
|---|---|---|---|
| | | | |

## Assumptions
| Assumption | Status (tested/untested) | Notes |
|---|---|---|
| | | |

## Parked Ideas
- [idea] — parked on [date], reason: [why it was premature]

## Solution Concepts
| Concept | Evidence it traces to | Tradeoffs | Status |
|---|---|---|---|
| | | | |

**Chosen direction:** [once Act converges]
```

## Update rules
- Update at every meaningful checkpoint, not just at phase transitions — an evidence log entry should be added right after the evidence surfaces, not reconstructed from memory later.
- Never delete parked ideas or discarded essential questions — strike through or mark status instead. They're useful context for why the current framing was chosen.
- When revising the Challenge statement itself, keep the old version visible with a note on why it changed — that's often the most useful record of what Investigate actually taught the learner.
