---
name: theoneloop-implement
description: Execute all or selected stories from an approved TheOneLoop sprint, coordinating implementation, separate review, corrections, and verification. Manage branches and PRs within the agreed workflow without performing merges.
---

# Execute the technical cycle

This installed skill is self-contained. Resolve Markdown links relative to the file containing them. Use bundled resources rather than looking for a source checkout or sibling skills. Write project state to the target project's `.theoneloop/`, not to the installation directory.

Read the [protocol](references/protocol.md) and [document format](references/documents.md). Read the configuration, readiness assessment, sprint, selected stories, and relevant reports. Do not start from a chat summary alone.

## Prepare execution

1. Reconstruct the authorized selection, approved plan revision, actual state, branch, existing PRs, and evidence. If the selection is missing and cannot be inferred from the request, ask which stories to execute.
2. Verify prerequisites and dependencies on the actual branch. Do not implement a `blocked` story, add dependencies to the selection, or autonomously integrate code from other branches. Identify blockers and continue with other selected, independent stories.
3. Apply the configured workflow: in Git mode, create or resume the story/sprint branch; in direct mode, use the branch prepared by the user. If the direct-workflow branch is missing or differs from the agreed branch, report the blocker before changing code.
4. Do not overwrite unrelated changes or confuse existing work with story changes. Record the base and scope. Use one sprint coordinator at a time and serialize implementations in this first version.

## Execute each ready story

1. Set the state to `implementing`. Implement the agreed outcome, update tests and documentation, and explain any justified absence of impact.
2. Run the implementer's checks for the change. Document results and limitations; do not describe this self-check as an independent review.
3. If a requirement change becomes necessary, follow the plan-change process. Do not change criteria to match the code produced.
4. Set the story to `in_review`. Delegate review to an agent in a separate context when the environment's capabilities and instructions allow it. This is the concrete subtask requested by this skill: read [theoneloop-review](references/workflows/theoneloop-review.md) and assess the story version without implementing it. No additional parallel agents or particular model are required.
5. Prepare a neutral assignment using the [handoff template](templates/handoff.md), including requirements, baseline, code, and diff scope. If an automatic separate context is unavailable, save the document and explain how the human can use it in a new session. Do not replace the reviewer with another reading in the same conversation.
6. Handle findings according to the protocol: fix blocking defects, document resolved findings, and request another review of changed areas. Track rounds and lack of progress; when a limit is reached, retain the blocker and request the necessary decision without resetting counters.
7. After a positive review, execute the [theoneloop-verify](references/workflows/theoneloop-verify.md) phase. Failed verification returns the story to rework and requires relevant reassessment after changes.
8. Record `done` only when all required evidence exists. You may recommend human validation for a complex story and explain why, without automatically stopping other selected stories.

## Complete the selection and prepare integration

- With PRs per story, open or update the technically completed story's PR under the authorized workflow. Describe the problem, resulting behavior, and relevant verification.
- With a PR per sprint, retain the branch and results of partial selections. Once every story is `done`, verify the integrated sprint and only open or update the sprint PR after a positive result.
- In direct mode, do not create PRs or branches. All merges remain the user's responsibility in both modes.
- If an integration required for overall checks is missing, identify exactly which changes must become available; do not declare the sprint ready.
- If you cannot open a required PR, prepare its title and body as text and record delivery as `pending`. A story can be technically `done` while PR creation remains outstanding; distinguish the two outcomes.

## Outcome and resumption

Update documents before ending or handing off to a new session. Report completed stories, stories awaiting review, blockers or rework, versions and reports, branches and PRs that actually exist, and the next required intervention. Do not declare sprint acceptance or deploy.
