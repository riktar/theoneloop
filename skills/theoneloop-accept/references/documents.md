# Documents and references

## Source of truth

Use a single `.theoneloop/` directory in the target project:

```text
.theoneloop/
  config.md
  readiness.md
  issues/ISSUE-001.md
  stories/STORY-001.md
  sprints/SPRINT-001.md
  evidence/
    REVIEW-STORY-001-01.md
    VERIFY-STORY-001-01.md
    VERIFY-SPRINT-001-01.md
  handoffs/HANDOFF-STORY-001-01.md
```

Create documents when needed. Do not generate empty stories, evidence, or sprints to fill the structure. The package contains templates; `.theoneloop/` contains data for the project using it.

Use UTF-8 Markdown files with YAML frontmatter. Use English keys and state values, and descriptive text in the project's language. Do not depend on an installed parser: agents apply the format by reading the documents.

Template placeholders are instructions for completion, not valid values for approved documents. Replace them, remove irrelevant optional sections, and use `null` or empty lists for unavailable information. Do not use `null` as a positive outcome.

## Identifiers

- Project-wide unique IDs: `ISSUE-001`, `STORY-001`, `SPRINT-001`.
- Stable criteria within a story: `AC-01`, `AC-02`. Use `STORY-001/AC-01` for external references.
- Evidence IDs containing the subject and a sequence number: `REVIEW-STORY-001-01`, `VERIFY-SPRINT-001-01`.
- Preserve existing IDs imported from the user. Do not renumber stories that already have references.
- Preserve external references in `issue_refs` and the analysis document; do not require a particular issue tracker or Git provider.

The story document is authoritative for its requirements and technical completion. The sprint document is authoritative for composition, objective, approved revision, integration, release blockers, and acceptance. Reports preserve evidence. Summary status must be consistent with that evidence, not replace it.

## Common metadata

`schema_version: 1` identifies the format. `plan_revision` is a revision of approved requirements, not a Git revision. `status` follows the protocol. `blocked_by` contains concrete descriptions of impediments, with references where available. `resume_status` preserves a suspended story's phase.

Distinguish blocker types in the text:

- **execution:** prevents the affected technical work;
- **integration:** required code is missing from the working branch;
- **release:** does not necessarily prevent technical completion but prevents sprint closure.

Record release blockers in the sprint document, with resolution conditions and evidence. Do not manually duplicate the same blocker as an independent fact in multiple documents; use references.

## Versions and evidence

A version reference must identify the verified code. Use a commit when available. For a branch with uncommitted changes, record the base, files, and diff actually examined; treat the result as provisional until a stable, identifiable reference exists for the final result. Do not commit solely to construct evidence unless this is within the authorized workflow.

For `done`, PR readiness, and acceptance, require a stable, identifiable version: a commit or equivalent durable snapshot prepared according to the agreed workflow. If unavailable, retain provisional results and identify the required user action. A branch name alone is not an immutable version.

Reports include the subject, plan revision, baseline, examined version, environment, results, and limitations. Allowed outcomes for individual checks are `pass`, `fail`, `not_run`, `blocked`, and `not_applicable`. Always explain `not_applicable`; do not use it to evade an approved criterion.

Every mandatory criterion requires evidence of a positive outcome. This may be an automated check or an observable test specified in the plan; a required but unavailable check remains blocking. A planned manual check may be performed by the human and recorded as their evidence without turning it into early story acceptance.

Do not include secrets, tokens, or unnecessary personal data in evidence. Provide references to useful logs and concise results. A mock test demonstrates the simulated contract: do not claim that an unexercised real integration has been verified. Agree during planning on the evidence required for the actual requirement.

## Decision history

Maintain a log in sprint and story documents with the date, author or session when available, decision, rationale, and references. Do not invent reviewer or human identities. Record acceptance only after an explicit response, including the code version and plan revision it applies to.

For requirement changes, preserve the previous wording or a reference to the version containing it, describe the change, and record the human decision. New requests arising from rejected acceptance are not automatically deferred to another sprint.
