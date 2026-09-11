# TheOneLoop protocol

This is the authoritative source of rules shared by the six skills. Read it before working; also consult [documents.md](documents.md) for documents and evidence. User and host-environment instructions take precedence. If an explicit request changes a convention, document the decision; do not present a modified requirement or skipped check as satisfied.

## Responsibilities and boundaries

- The human coordinating the work has authority over product decisions. Do not add approvals for other roles solely because of their job titles.
- The human and AI analyze issues, define requirements, and plan together. The model proposes sprint composition; the human approves the plan for the sprint to execute.
- Each sprint contains a complete increment that can be released as a whole. Do not spread backend and frontend work required for the same increment across different sprints, leaving incomplete functionality.
- Future sprints remain drafts. Detail and approve them when they become the next work to undertake.
- The human selects all stories or a subset. The agent does not automatically add stories to the selection to resolve dependencies.
- The agent may choose technical details within agreed requirements and constraints. Changes to behavior, scope, or criteria require a recorded human decision; pause only affected work.
- Each story includes code, tests, and affected documentation, with an explicit explanation when test or documentation changes are unnecessary.
- All merges are the user's responsibility, including in Git mode. Do not perform equivalent operations to autonomously transfer work between branches.
- Human validation of a story is optional and does not automatically block the selection. Final sprint acceptance is mandatory.
- Closure means an accepted, releasable increment, not an already performed or authorized deployment.

## Prerequisites

Initialization assesses repository structure, environment, installation, the full build, tests, startup, regression checks, documentation, and agent capabilities. Run available checks within the authorized scope and record baseline results, including pre-existing failures and coverage limitations.

A proposed command that has not run is not a verified baseline. Missing tests or a successful build alone do not demonstrate the absence of regressions. Agree on meaningful project checks; do not introduce a universal coverage percentage or attribute absolute guarantees to the suite.

For a new or unready project, produce a preparation plan agreed with the human. Analysis and preparation may continue; implementation of stories that depend on missing prerequisites remains blocked. Do not silently waive initialization requirements.

Recheck relevant prerequisites when starting or resuming a sprint and when the environment, dependencies, or commands change. A previous positive result does not remain valid indefinitely.

## Story states

| State | Meaning | Exit condition |
|---|---|---|
| `draft` | Requirements are being developed. | The story is sufficiently defined and the plan is approved. |
| `ready` | Requirements are ready for execution, subject to checking blockers on the actual branch. | User selection and satisfied prerequisites. |
| `blocked` | A concrete impediment prevents the activity. | Evidence that all applicable blockers have been resolved. |
| `implementing` | Code, tests, and documentation are in progress. | Implementation is available and implementer checks are complete without blocking issues. |
| `in_review` | Waiting for or undergoing separate review. | Positive review or findings requiring correction. |
| `in_verification` | Separate verification against criteria for the reviewed version. | All required criteria are verified or defects need correction. |
| `rework` | Corrections are needed following review, verification, or human feedback. | Work resumes with defined corrective activities. |
| `done` | Technical completion is documented. | Remains valid until changes or new findings invalidate the evidence. |

Normal transition: `draft → ready → implementing → in_review → in_verification → done`.

After defects in review or verification: `rework → implementing → in_review → in_verification`. A blocker may suspend any unfinished phase; record `resume_status` and the reason without declaring the work complete. A `done` story affected by feedback or invalidated evidence returns to `rework`, or `blocked` if it cannot be executed.

Before implementation, verify that required dependencies are technically complete and their changes are present in the working branch. If A is complete but absent from B, B remains `blocked`: tell the user which integration is missing. If A is already present in the shared sprint branch, do not require an unnecessary merge.

Dependency status and code availability are separate checks. Do not infer code availability from a branch name or an open PR alone. If availability cannot be established, retain the blocker. Recheck dependent stories when a dependency is reopened.

## Technical completion

A story may become `done` only when:

1. All approved criteria have been verified against the relevant version.
2. Required code, tests, and documentation are updated, or the absence of impact is explained.
3. Review in a separate context is positive and no blocking findings remain open.
4. Subsequent corrections have been reviewed and verified again in affected areas.
5. The version, results, and evidence limitations are recorded.

An implementer's summary, a checkbox, or a listed command is insufficient. Review also assesses test adequacy, plausible regressions, and alignment with requirements; verification checks observable behavior. Do not automatically turn refactoring suggestions or scope expansions into mandatory defects.

## Review independence

The reviewer works in a context separate from the one that implemented the work. Loading another skill in the same conversation does not meet this requirement.

When the environment permits and authorizes delegation, `theoneloop-implement` instructions require a separate reviewer. Provide approved requirements, code, diff scope, baseline, and check commands. Avoid passing the implementer's entire conversation or a suggested conclusion; provide necessary information without promising isolation the tool does not offer.

When a separate context cannot be created automatically, save a handoff and request a new session. Leave the story `in_review`. This is a required protocol handoff, not human validation of requirements.

The reviewer does not modify product code during assessment; they document findings. The implementer makes corrections and the reviewer reassesses them. After technical changes, always link the new outcome to the new version. Verification is a separate phase; a third context is not mandatory.

## Correction cycles

Configure `max_rework_rounds` and `max_no_progress_rounds` during initialization. Suggested starting values are 3 and 2, adjustable by the human. A round consists of a correction attempt and its reassessment; do not count individual commands or tests as rounds.

Track rounds in documents without resetting them in every new session. When a limit is reached, record the blocker, attempts, and required human decision. Recognize lack of progress when the same finding recurs without a new, verifiable solution. A human decision may start a new series of attempts; retain its rationale and previous history.

Continue with other selected, independent stories where possible. Do not bypass a blocker by changing a criterion, weakening checks, or implementing an unselected story.

## Workflows and PRs

Configuration specifies `workflow: git | direct`. In Git mode, also specify `branch_unit: story | sprint`, the base, and naming conventions.

- **Git per story:** create or resume the story branch; open the PR when the story is technically `done`. The user integrates the work.
- **Git per sprint:** create or resume the sprint branch. Multiple partial selections use the same branch. Open one PR only after every story is technically `done` and integrated sprint verification is positive. Do not open an early PR for a partial selection.
- **Direct:** work on the branch prepared by the user. Do not automatically create branches or PRs; merges and branch organization remain the user's responsibility.

Invoking the agreed workflow may already authorize branches and PRs: do not ask again for permission already granted. Configuration read outside an execution request does not by itself authorize external operations.

Do not assume an approved PR has been integrated. If the tool cannot open the requested PR, prepare its title, description, and references and record `pr_status: pending`; state the limitation without claiming the PR exists. On resumption, find and update existing artifacts rather than duplicating them.

Existing PRs may be updated with corrections; wait for the corresponding new review and verification before reporting positive outcomes. All merges, including dependency integration, are the user's responsibility. Report conflicts as blockers; help resolve them when requested by the user, without performing the merge.

## Sprint states and acceptance

| State | Meaning |
|---|---|
| `draft` | Proposed increment, still subject to collaborative planning. |
| `approved` | The human has approved the next sprint's objective, stories, and criteria. |
| `in_progress` | Execution, integration, or rework is underway. |
| `ready_for_acceptance` | All stories are technically complete and integrated verification is positive for the candidate version. |
| `accepted` | Human validation is positive for the candidate version and no release blockers remain open. The sprint is closed. |

Use `blocked_by` on the sprint as well to record impediments without losing its phase. The sprint remains open in every state other than `accepted`.

Apply each blocker only to its scope: a release-only constraint does not prevent implementation or technical verification that can already proceed. Execution and integration blockers prevent activities that depend on them.

Integrated verification must demonstrate a successful full software build, results of agreed regression checks, and complete availability of the new feature or fix. Individual story results do not replace this step. Verify the actual integrated version, not a hypothetical combination of branches.

The human may assess requirements once the sprint is technically ready even when an external release blocker remains. Record that assessment, but do not move to `accepted` until blockers are resolved. A go-live-only constraint can therefore leave a story `done` while preventing sprint closure. Do not reclassify a failed technical criterion as an external constraint.

Human rejection leaves the sprint open and starts tracked rework: identify affected stories and criteria, update the plan when necessary, repeat relevant reviews and verification, and present the candidate version again. Do not automatically defer feedback to a future sprint or close the rejected sprint.

Optional human story review does not replace sprint acceptance. Only explicit human feedback can be recorded as validation: the agent does not infer acceptance from silence, passing tests, or an open PR.

## Resumption and plan changes

Each session reconstructs state, selection, branch, blockers, attempts, and evidence from `.theoneloop/` files and the actual work version. If documents and repository state diverge, record and resolve the discrepancy before advancing.

Link each approval to a plan revision and each review, verification, and acceptance to a code version. Requirement or code changes require an impact assessment: reopen affected activities and do not reuse evidence that no longer applies. Preserve historical outcomes rather than overwriting them with the new result.

When a change invalidates verification, uncheck affected criteria and keep the previous report in history. When the candidate version or a previously validated requirement changes, set `human_requirements_result: pending` and clear current acceptance references; preserve the previous decision in the log. For explicit rejection, use `changes_requested` until the new candidate is ready. Do not erase history merely to make metadata appear consistent.

To change approved requirements, document the proposal, rationale, and impact, obtain the human decision, and increment `plan_revision`. Ordinary implementation details within agreed constraints do not require another approval.

The first version does not coordinate concurrent writes to the same branch or documents: assign one active coordinator per sprint and serialize updates. Separate reviews and read-only tasks may be delegated; this does not imply authorization for concurrent implementations.
