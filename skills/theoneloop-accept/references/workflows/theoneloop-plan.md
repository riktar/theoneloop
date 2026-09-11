# Analysis and planning

Read the [protocol](../protocol.md), [document format](../documents.md), and the project's configuration and readiness assessment.

## Analyze the issue

- Accept text, a local document, or content available through an integration. Preserve the source and supplied IDs; do not require a particular issue tracker.
- Distinguish the need, proposed solution, constraints, existing behavior, and expected outcome. For a bug, seek a reproduction and the expected correct behavior.
- Read the code and documentation needed to assess impact. If uncertainty prevents verifiable criteria, document an investigation or question; do not invent requirements.
- Use the [issue template](../../templates/issue.md), distinguishing agreed decisions, proposals, and open questions.

## Define stories and sprints

1. Use the [story template](../../templates/story.md), preserving its context, grouped criteria, technical notes, tests, and out-of-scope sections. The As a / I want / so that format is optional for technical activities that do not benefit from it.
2. Define observable criteria with stable IDs and a verification plan for each. Include error cases and nonfunctional requirements relevant to the work without imposing universal checklists.
3. Make dependencies, constraints, tests, and documentation impact explicit. Check that referenced IDs exist and dependencies do not form cycles; resolve cycles during planning before declaring stories executable. Distinguish product requirements, agreed technical constraints, and possible implementation choices.
4. Propose sprints using the [sprint template](../../templates/sprint.md). Each objective must describe the complete increment that will become available. A story does not have to be independently releasable.
5. Consider splitting stories that are too large for a comprehensible review without imposing fixed sizes or counts. Keep all parts needed for a complete feature in the same sprint.
6. Detail only the next sprint. Keep subsequent sprints `draft`, with an objective, known dependencies, and indicative stories; do not invent precision or automatically infer durations from qualitative sizes.
7. Agree on integrated sprint checks and fundamental prerequisites before execution. Record release constraints separately, including external constraints already identified in the requirements.
8. Present the objective, scope, criteria, dependencies, verification plan, and Git choices to the human. After explicit approval, record the revision and decision; set the sprint to `approved` and stories to `ready` or `blocked` according to known impediments.

## Change an approved plan

Record the proposal and its impact on the outcome, criteria, dependencies, and evidence. Pause affected work while the human decision is pending. After the decision, increment `plan_revision`, preserve the previous requirement or its reference, and reopen affected activities. Do not seek approval again for ordinary technical details already within scope.

## Outcome

Provide links to the documents and identify what is approved, what remains a draft, and which decisions or blockers remain. Plan approval does not automatically select every story for execution.
