# Verification separate from implementation

Read the [protocol](../protocol.md), [document format](../documents.md), configuration, readiness assessment, and documents for the subject being verified. Use the [verification template](../../templates/verification.md).

## Story verification

1. Confirm that a positive review applies to the current version. If code has changed, assess impact and require an updated review of affected areas before completing the story.
2. Read approved criteria and the verification plan directly. Do not infer expected behavior solely from code or tests written by the implementer.
3. Execute planned checks in the separate verification phase. Previous reports may support the assessment but are not evidence for different behavior or versions.
4. Record each criterion's result, observation, and evidence. Distinguish mock tests, real integration, automated checks, and manual checks. Do not claim coverage for an unavailable check.
5. Confirm affected tests and documentation. Do not rewrite criteria to pass verification or fix code during this phase; return work to `rework` when needed.
6. Set the story to `done` when all technical requirements are satisfied and relevant evidence is available. If a required check is missing, document the blocker; if a check fails, describe the reproducible defect and start rework.

## Integrated sprint verification

1. Verify that all included stories are technically `done` and their code is present in the actual integrated version. If a merge is missing, report the blocker to the user.
2. Identify a stable candidate version and the approved plan revision. Run the full software build, agreed regression checks, and checks of the complete feature or fix.
3. Check relevant interactions between stories and, where required by the project, migrations, configuration, startup, and overall documentation updates.
4. Compare results with the baseline and explain limitations. A pre-existing failure is not automatically a regression but cannot be ignored if it prevents agreed release criteria from being satisfied.
5. On success, set the sprint to `ready_for_acceptance` and prepare evidence and reproducible instructions for human validation. External release constraints remain open and visible.
6. On failure, leave the sprint `in_progress`, identify stories to reopen, and record defects or blockers. Do not arbitrarily assign an undiagnosed integration error to a story.

The technical report does not authorize sprint closure, merges, or deployment. After changes to the candidate version, reassess impact and renew relevant verification before acceptance.
