---
name: theoneloop-review
description: Independently review a TheOneLoop story's code and reassess corrections, recording findings and an outcome tied to the examined version. Use in a context separate from implementation; does not replace functional verification or human acceptance.
---

# Story review

This installed skill is self-contained. Resolve Markdown links relative to the file containing them. Use bundled resources rather than looking for a source checkout or sibling skills. Write project state to the target project's `.theoneloop/`, not to the installation directory.

Read the [protocol](references/protocol.md), [document format](references/documents.md), story, sprint, configuration, and available handoff.

## Preconditions

- This must not be the session that implemented the work. If it is, prepare a handoff to a separate context and leave the story `in_review`; do not issue an independent approval.
- Identify the plan revision, baseline, code version, and relevant diff. If a reliable scope is missing, request that information and keep the review pending.
- Read requirements and code directly. The implementer's report is not proof of correctness and must not determine the conclusion.

## Assessment

1. Compare code against approved criteria, scope, and constraints. Examine surrounding code needed to understand integration and side effects.
2. Look for behavioral defects, plausible regressions, unhandled error cases, relevant security problems, inadequate tests, and inconsistent documentation.
3. Distinguish blocking defects from nonblocking suggestions and new product requests. For each finding, identify its location, concrete problem, consequence, and a verifiable resolution condition. Do not present stylistic preferences as defects without explaining their impact.
4. You may run useful checks within the authorized environment. Record checks actually performed and do not change product code during assessment.
5. Write a report using the [review template](templates/review.md). Assign `pass`, `changes_requested`, or `blocked` according to evidence. Do not use `pass` for an incomplete review.
6. With `changes_requested`, set the story to `rework` and return findings to the implementer. With `pass`, record the report and set it to `in_verification`. For a concrete impediment, record `blocked` and `resume_status: in_review`; simply waiting for a new session remains `in_review`. Review alone does not mark the story `done`.

## Reassessment

Link the previous report, identify the new version, and examine the correction and its effects. Verify that each blocking finding is actually resolved. A change can introduce new problems; do not merely check that suggested code exists. Preserve report history and respect the sprint's rework limits.

Return the outcome, open or resolved findings, and assessment limitations. Do not open or merge PRs or record human acceptance.
