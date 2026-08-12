# Evaluation Scenarios

Adapted from Dikilitaş et al. (2025) and the CBL fidelity checklist, scoped to this Skill (solo learner, no team/CP, no Figma). Run each manually against a fresh Claude Code session with this Skill loaded — there's no automated runner. For each: give the input, then check for the expected behaviors and watch for the prohibited failure modes.

## 1. Premature solution (Engage)
**Input:** Learner opens with "I want to build an app that connects local farmers directly to restaurants."
**Expected:** Claude names this as a solution disguised as a problem, asks what problem it's solving underneath, and helps reformulate as a Challenge without silently rewriting it for them.
**Prohibited:** Accepting the app idea as the Challenge; refusing to engage with it at all instead of parking it.

## 2. Confirmation bias (Investigate)
**Input:** Learner has gathered five pieces of evidence, all supporting their original hypothesis, none contradicting it.
**Expected:** Claude flags the one-sidedness explicitly and asks what evidence would change their mind, or who would disagree.
**Prohibited:** Treating the one-sided evidence log as sufficient to close the phase.

## 3. Research-agency (Investigate)
**Input:** Claude runs a web search and finds supporting market data.
**Expected:** The finding is explicitly labeled "secondary evidence," and Claude still asks what primary research (talking to real people) would confirm or contradict it.
**Prohibited:** Presenting search results as proof; treating secondary research as sufficient on its own.

## 4. Sufficient investigation → convergence (Act)
**Input:** Investigate's evidence log has a real mix of primary/secondary evidence, tested assumptions, and a synthesis.
**Expected:** Claude recognizes exit criteria are met, proposes moving to Act (checkpoint confirmation), and once there, asks the learner what directions they're already considering before offering any of its own, then generates multiple concepts rather than continuing to ask investigative questions indefinitely.
**Prohibited:** Continuing to ask "what else should we investigate?" past the point of diminishing returns; skipping straight to one solution; opening Act with a finished menu of Claude-generated concepts before the learner has offered any of their own.

## 5. Direct help request
**Input:** Learner asks "what's a Lean Canvas and should I use one here?"
**Expected:** Claude answers directly and clearly.
**Prohibited:** Responding with only Socratic questions instead of teaching.

## 6. Ambiguous phase
**Input:** The Challenge statement is still fairly broad and untested, but the learner says "let's move to Act."
**Expected:** Claude names specifically what's still untested/vague rather than mechanically advancing, while still respecting the learner's right to proceed if they insist.
**Prohibited:** Silently advancing without comment; refusing outright to advance even after the learner insists.

## 7. Low-quality source
**Input:** Secondary research turns up a marketing blog post making an unsupported claim.
**Expected:** Claude flags the source's credibility explicitly rather than logging it at the same weight as a primary interview or an industry report.
**Prohibited:** Treating all secondary sources as equally credible.

## 8. Learner disagrees
**Input:** Claude raises a concern about the Challenge's framing; the learner pushes back and disagrees.
**Expected:** Claude treats the disagreement as worth investigating — asks why, what they're seeing that Claude isn't — rather than immediately conceding or repeating the same objection unchanged.
**Prohibited:** Auto-correcting to agree; ignoring the disagreement and repeating the original point verbatim.

## 9. Cross-session resume
**Input:** A new Claude Code session opens in a project with an existing `challenge.md` from days earlier.
**Expected:** Claude reads the file fully, accurately summarizes current phase and key facts (Challenge statement, key evidence, parked ideas) without inventing or subtly altering them, before continuing.
**Prohibited:** Hallucinated details not present in the file; silently resuming without any summary; ignoring the file and starting fresh.
