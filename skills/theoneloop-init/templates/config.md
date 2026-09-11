---
schema_version: 1
project: "<project name>"
language: en
workflow: null
branch_unit: null
base_branch: null
integration_branch: null
pr_target: null
story_branch_pattern: "story/{id}"
sprint_branch_pattern: "sprint/{id}"
review_mode: null
max_rework_rounds: 3
max_no_progress_rounds: 2
configured_at: null
configured_by: null
---

# TheOneLoop configuration

Complete with the human. `workflow`: `git` or `direct`. In Git mode, choose `branch_unit`: `story` or `sprint`; in direct mode, leave `branch_unit: null`. Define the actual Git bases and record any variations in the sprint. Set `language` to the target project's preferred language; the English template does not require English project documents.

`review_mode`: `delegated` when a separate context is available and permitted, otherwise `manual_handoff`. Limits of 3 and 2 are initial proposals to agree on. No setting allows automatic merges.

## Project and conventions

- Product, users, and repository structure:
- Repository instructions to follow:
- Authoritative documentation:
- Existing naming and ID conventions:

## Commands and environment

Record project commands as text; this document is not executable. Specify where to run them and what they verify. Do not store credentials.

| Activity | Command or procedure | Directory / environment | Baseline outcome and reference |
|---|---|---|---|
| Preparation / installation | | | |
| Full build | | | |
| Automated tests | | | |
| Relevant static checks | | | |
| Startup and smoke test | | | |
| Regression checks | | | |

## Fundamental project criteria

- Mandatory conditions for starting implementation:
- Mandatory checks for a releasable increment:
- Known baseline limitations:
- Required evidence and test methods for external integrations:
- Method for identifying the verified version durably:

## Environment capabilities

- Repository and command access:
- Available separate-review mode:
- PR creation available through:
- Handoff when a capability is unavailable:
- Agreed Git workflow, including commit operations:

## Agreed decisions

| Date | Decision | Author / source | Rationale |
|---|---|---|---|
