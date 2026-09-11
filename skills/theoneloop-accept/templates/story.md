---
schema_version: 1
id: "<STORY-NNN>"
title: "<title>"
sprint: null
plan_revision: 1
status: draft
resume_status: null
priority: null
estimate: null
depends_on: []
issue_refs: []
blocked_by: []
branch: null
base_ref: null
implementation_ref: null
pr_url: null
pr_status: not_applicable
review_refs: []
verification_refs: []
rework_rounds: 0
no_progress_rounds: 0
---

# <ID> — <Title>

In the Git workflow, `pr_status` may be `pending` or `opened`; in direct mode, it is `not_applicable`. With a PR per sprint, the sprint document is authoritative for the branch and PR: reference it here rather than maintaining a second independent state.

## Context

Describe existing behavior, the need, and links to issues and preceding stories. Identify relevant sources of truth and product constraints.

**As a** <user or role>,
**I want** <capability or behavior>,
**so that** <outcome or benefit>.

For technical activities that do not benefit from this format, use a direct statement of the objective.

## Acceptance criteria

Group criteria by area. Assign stable IDs and describe observable outcomes, errors, and relevant limits. Checkboxes indicate documented positive verification, not merely the presence of code.

### <Functional area>

- [ ] **AC-01** — <expected behavior and observable conditions>
- [ ] **AC-02** — <relevant error handling or edge case>

### <Another area, if needed>

- [ ] **AC-03** — <expected behavior>

## Verification plan

Define how each criterion can be verified before execution. One scenario may cover several criteria if the mapping is explicit. Do not record future outcomes as already positive.

| Criterion | Scenario and preparation | Method / procedure | Expected result | Environment / prerequisites |
|---|---|---|---|---|
| AC-01 | | | | |
| AC-02 | | | | |
| AC-03 | | | | |

## Technical notes

- Agreed technical constraints and rationale:
- Affected integrations, data, migrations, or contracts:
- Proposed choices still open, distinguished from requirements:

## Automated tests

- Tests to add or change and behavior to protect:
- Relevant regression cases:
- Verifiable rationale when no test changes are needed:

## Affected documentation

| Document / area | Required update | Rationale |
|---|---|---|

If there is no impact, explain why explicitly.

## Dependencies and blockers

| Dependency / blocker | Type | Resolution condition | Evidence in the working branch | State |
|---|---|---|---|---|

A technically completed dependency that is absent from the working branch keeps the story blocked. Release-only constraints are recorded in the sprint and referenced here.

## Out of scope

- <explicit exclusion>

## Implementation

Complete during and after work without anticipating outcomes.

- Starting version and resulting version:
- Changes to code, tests, and documentation:
- Implementer checks actually performed:
- Limitations, remaining work, and references:

## Agent review

Link separate reports. Do not replace a report with a statement that the review passed.

| Report | Examined version | Outcome | Blocking findings still open |
|---|---|---|---|

## Verification

| Criterion | Outcome | Report / evidence | Verified version |
|---|---|---|---|

## Rework

| Round | Source / feedback | Corrective activities | Reassessment outcome | Report |
|---|---|---|---|---|

## Optional human validation

Complete only when validation has occurred or been recommended. Record the reason for the recommendation, version, and actual human feedback. This is not required for technical `done` status and does not replace sprint acceptance.

## Decisions and requirement changes

| Date | Revision | Decision / change | Human source | Previous requirement / reference | Impact on evidence |
|---|---|---|---|---|---|
