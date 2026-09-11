---
schema_version: 1
id: "<SPRINT-NNN>"
title: "<increment>"
status: draft
plan_revision: 1
approved_revision: null
story_refs: []
depends_on: []
blocked_by: []
workflow: null
branch_unit: null
base_ref: null
working_branch: null
integration_branch: null
candidate_ref: null
pr_target: null
pr_url: null
pr_status: not_applicable
integration_verification_refs: []
human_requirements_result: pending
accepted_ref: null
accepted_plan_revision: null
accepted_at: null
---

# <ID> — <Title>

## Increment objective

Describe the complete feature, fix, or capability that will be available at the end. All required parts, including backend and frontend, must belong to the same increment.

## Scope and boundaries

- Included outcome:
- Exclusions:
- Agreed constraints:

## Stories and dependencies

The story document is the source of truth for requirements and technical state; do not duplicate all its criteria in the sprint.

| Story | Contribution to the increment | Dependencies | Document |
|---|---|---|---|

## Plan approval

- Presented revision:
- Explicit human decision:
- Date and author when known:
- Recorded conditions or blockers:

Future sprints remain `draft`; do not record implicit approval.

## Workflow

- Mode inherited from configuration and agreed variations:
- Base, working branch, integrated branch, and PR target:
- Method for identifying the candidate version durably:
- All merges are managed by the user.

With a PR per sprint, do not open a PR after only a partial selection. Wait for all stories to be technically complete and integrated verification to pass. With PRs per story, link story PRs here without treating them as automatically integrated.

## Runs and selections

| Date / session | Stories selected by the user | Branch | Outcome | Remaining work / next step |
|---|---|---|---|---|

## Integrated verification plan

| ID | Scope | Procedure / command | Expected result | Prerequisites |
|---|---|---|---|---|
| INT-01 | Full software build | | | |
| INT-02 | Regressions | | | |
| INT-03 | Complete feature / fix | | | |

Add only checks relevant to the project, such as interactions between stories, migrations, and startup. Agree on these checks before execution.

## Integrated evidence

- Candidate version:
- Integrated verification report:
- Results and limitations:
- Reopened stories, if any:

## Release blockers

| ID | Constraint | Resolution condition | State | Evidence / decision |
|---|---|---|---|---|

A sprint may be technically ready for validation with external constraints still open, but it cannot become `accepted`. A failed technical criterion is not an external constraint.

## Presentation to the human

- Delivered increment:
- Version to try:
- Preparation and test instructions:
- Requirements to validate:
- Relevant limitations and remaining blockers:

## Acceptance log

| Date | Author / source | Candidate version | Plan revision | Requirements outcome | Feedback | Release blockers |
|---|---|---|---|---|---|---|

`human_requirements_result`: `pending`, `pass`, or `changes_requested`. A `pass` with open release blockers does not close the sprint. Only after all conditions are positive, populate `accepted_ref`, `accepted_plan_revision`, and `accepted_at`, and set `status: accepted`.

## Rework and plan changes

| Date | Feedback / proposal | Affected stories | Human decision | Previous and new revision | Evidence to renew |
|---|---|---|---|---|---|

Rejection keeps the sprint open. Do not automatically move work to future sprints or retain positive acceptance for code or requirements that have changed.
