---
schema_version: 1
id: "<VERIFY-STORY-NNN-NN or VERIFY-SPRINT-NNN-NN>"
scope: null
subject: null
plan_revision: null
baseline_ref: null
code_ref: null
verified_at: null
verified_by: null
result: pending
review_refs: []
previous_verification: null
---

# Outcome verification

`scope`: `story` or `sprint`. `result`: `pending`, `pass`, `fail`, or `blocked`.

## Version and preparation

- Subject and plan revision:
- Baseline and verified version:
- Environment, configuration, and test data:
- For a story, relevant positive review:
- For a sprint, evidence that all stories are complete and integrated:

## Results

| Criterion / check | Procedure actually performed | Expected result | Observed result | Outcome | Evidence |
|---|---|---|---|---|---|

Check outcomes: `pass`, `fail`, `not_run`, `blocked`, `not_applicable`. Explain exclusions; do not use `not_applicable` to skip a mandatory requirement.

## Regressions and coverage

- Agreed checks performed:
- Baseline comparison:
- Pre-existing problems and their impact:
- Unexercised areas and limitations:
- Clearly distinguished simulated, real, and manual tests:

## Defects and blockers

| ID | Criterion / area | Reproduction or impediment | Impact | Affected story or diagnosis still needed |
|---|---|---|---|---|

## Outcome and transition

- Rationale for the overall outcome:
- Subject state after verification:
- Evidence to renew after corrections:
- Next step:

A positive sprint result prepares human acceptance. It does not close the sprint or automatically resolve release constraints.
