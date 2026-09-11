---
name: theoneloop-accept
description: Prepare and record human acceptance of requirements for a technically verified TheOneLoop sprint, or turn feedback into tracked rework. Does not replace human judgment or perform merges or deployments.
---

# Sprint acceptance

This installed skill is self-contained. Resolve Markdown links relative to the file containing them. Use bundled resources rather than looking for a source checkout or sibling skills. Write project state to the target project's `.theoneloop/`, not to the installation directory.

Read the [protocol](references/protocol.md), [document format](references/documents.md), sprint, stories, integrated verification reports, and release blockers.

## Prepare validation

1. Verify that all stories are technically completed and reviewed and the integrated version has passed required checks. If these conditions are missing, identify remaining work; do not ask the human to accept a sprint that is not technically ready.
2. Present the delivered increment, candidate version, plan revision, instructions for trying it, verification results, and relevant limitations. Link evidence without requiring the human to conduct a code review.
3. Show release blockers and their resolution conditions. The human may assess requirements, but the sprint remains open until those constraints are resolved.
4. Request human feedback on requirements only if it has not already been given for this version. Do not interpret silence, a positive technical review, or an open PR as acceptance.

## Record the decision

- **Positive feedback:** record the author when known, date, version, and plan revision. If all release blockers are resolved and evidence remains valid, set `accepted`. Otherwise, retain the positive feedback but leave the sprint `ready_for_acceptance` with open blockers.
- **Negative feedback:** keep the sprint open and return it to `in_progress`. Record feedback, map it to stories and criteria, and start rework. If feedback is ambiguous, clarify the expected outcome before making changes that depend on the answer.
- **Changed requirements:** preserve previous requirements and agree on impact through [theoneloop-plan](references/workflows/theoneloop-plan.md). Update the plan revision after the human decision. Do not automatically move feedback to a future sprint.

After rework, relevant review and verification and new human feedback on the updated candidate are required. If only an external constraint is resolved without changing code or requirements, previous human feedback remains usable where still applicable; do not ask for the same approval again without a reason.

## Outcome

Explicitly state whether the sprint is closed and releasable or still open, and why. Update the acceptance log in the sprint document. Do not merge or deploy. Findings may inform subsequent planning, which remains a draft until discussed with the human.
