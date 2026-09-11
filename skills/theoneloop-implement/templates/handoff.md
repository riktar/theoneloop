---
schema_version: 1
id: "<HANDOFF-STORY-NNN-NN>"
task: review
subject: "<STORY-NNN>"
sprint: "<SPRINT-NNN>"
plan_revision: null
status: pending
base_ref: null
code_ref: null
created_at: null
result_ref: null
---

# Handoff to a separate reviewer

## Assignment

Run `theoneloop-review` in a session or agent with a context separate from the implementer. Do not modify product code. Assess requirements and code without assuming the implementer's conclusions are correct.

## Documents to read

- Path to the TheOneLoop package and review skill:
- Repository instructions:
- `.theoneloop/` configuration:
- Story and sprint:
- Required product decisions or constraints:

## Code scope

- Repository and working directory:
- Branch:
- Baseline and version to examine:
- Diff or procedure for locating it:
- Dependencies already present and unrelated changes to distinguish:

## Environment and checks

- Project commands and prerequisites:
- Access limitations or unavailable checks:
- Where to consult existing evidence without treating its conclusions as binding:

## Expected output

Produce a report in `.theoneloop/evidence/` with an outcome, concrete findings, examined version, and limitations. Update story references according to the protocol. Return defects to the implementer for correction; do not declare the story `done` based on review alone.

## Coordinator resumption

- Produced report:
- State and next step:
- Session / reviewer when known:
