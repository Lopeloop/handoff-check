# handoff-check

A small agent skill for the gap between “done” and what the repository actually shows.

An agent hands over a session: tests green, fixes complete, ready to continue. This skill asks the next agent to check those claims against code, reviews, saved evidence, and Git state before building on them.

It keeps **implemented, tested, accepted, committed, and published** separate. Particularly useful when several coding agents share a repository or work spans multiple sessions.

## Try it

Download or clone this repository. Ask your coding agent:

> Read `skills/check-handoff/SKILL.md`. Use it to check the handoff below against my repository. Keep the audit read-only and tell me where to resume.

Then provide the handoff and your repository location. The skill requires file inspection; Git is useful for version-state claims. It does not require an API key, a server, or a particular model. If your agent supports installing folder-based skills, use the `skills/check-handoff` folder with its documented installation workflow.

## Example

Handoff: “All tests pass. The change is accepted and pushed.”

Observed evidence: saved test output, an unresolved review, modified code, and no observation of the publication destination.

Result: tests have historical evidence; acceptance is contradicted by the unresolved review; current changes are not fully committed; publication is not checked. The next step is to resolve the review, not assume the handoff is authoritative.

See [worked cases](examples.md) for common traps.

## Scope and limitations

This is an instruction skill, not an automated verifier. It helps an agent gather and interpret evidence; the agent can still make mistakes. It does not replace code review, prove semantic correctness, or provide a security boundary against malicious input.

It is also not an experiment runner: no scheduling, execution, scoring, or reproducibility machinery. It can inspect a runner's handoff just as it can inspect any other coding project's handoff.

Validation: skill structure checked with the skill-creator validator; worked cases manually reviewed. No independent model evaluation or measured accuracy claim.

Published by [Lopeloop](https://github.com/Lopeloop). MIT licensed.
