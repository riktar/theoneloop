# TheOneLoop

<p align="center">
  <img src="docs/assets/theoneloop.png" alt="TheOneLoop: a white infinity ring with flowing runes" width="360">
</p>

**One loop. Human direction. Agent execution.**

Turn an issue into a reviewed, releasable software increment. Six text-only skills give your coding agent a repeatable process, with you approving the plan and accepting the result.

## Install

Run in your project, then choose your agents:

```sh
npx skills add riktar/theoneloop --skill '*'
```

For Claude Code, Codex, OpenCode, and Pi explicitly:

```sh
npx skills add riktar/theoneloop --skill '*' --agent claude-code codex opencode pi --copy
```

Requires Node.js/npm for installation. [More installation options](docs/installation.md).


## How it works

**Issue → Plan together → Approve sprint → Implement, review, verify → Human acceptance**

- **You define the outcome.** The agent helps turn it into stories with acceptance criteria, tests, and documentation work. A sprint contains a complete feature or fix, including all necessary backend and frontend work.
- **The agent runs the technical cycle.** Choose one story, several, or the full approved sprint. Each goes through implementation, separate code review, corrections, and requirement verification. Blocked stories wait for their prerequisites.
- **You accept the increment.** All stories must be complete and the integrated build and agreed regression checks must pass first. Your feedback reopens affected work; you control merges and releases.

Plans, decisions, and evidence live in your project's `.theoneloop/` folder, so a fresh session can resume the work.

## Your first sprint

Ask your agent in sequence. Use the story and sprint IDs generated for your project.

**1. Set up the workflow**

> Use theoneloop-init to check this project and agree on the workflow.

**2. Plan an increment, then approve it**

> Use theoneloop-plan for this issue: customers need to recover access to their account.

**3. Execute the approved work**

> Use theoneloop-implement to complete all stories in SPRINT-001, including review and verification.

The implementation skill includes `theoneloop-review` and story verification. If a separate reviewer cannot run automatically, it provides a handoff for another session.

**4. Integrate and accept**

Perform any required merges, then ask:

> Use theoneloop-verify to check the integrated SPRINT-001, then use theoneloop-accept to guide my acceptance review if verification passes.

## Go deeper

- [Workflow, six skills, Git modes, and project state](docs/workflow.md)
- [Installation and updates](docs/installation.md)
- [Story template](skills/theoneloop-plan/templates/story.md) and [sprint template](skills/theoneloop-plan/templates/sprint.md)
- [Validation status and publishing](docs/publishing.md#validation-record) · [Package maintenance](docs/maintaining.md)
