---
name: theoneloop-init
description: Initialize or recheck TheOneLoop in a project by assessing prerequisites, the baseline, and development workflow configuration. Use before actionable planning or when the environment changes; does not automatically implement features.
---

# Project initialization

This installed skill is self-contained. Resolve Markdown links relative to the file containing them. Use bundled resources rather than looking for a source checkout or sibling skills. Write project state to the target project's `.theoneloop/`, not to the installation directory.

Read the [protocol](references/protocol.md) and [document format](references/documents.md). This skill configures a workflow made entirely of text files. Do not install TheOneLoop scripts, dependencies, or coding-agent configurations.

## Procedure

1. Read repository instructions and any existing `.theoneloop/` documents. Identify the project, stack, structure, documentation, and existing workflow. Do not overwrite the user's configuration or work.
2. Identify and, where executable within the authorized scope, run installation, the full software build, tests, static checks, startup, and regression checks. Use the project's own tools; distinguish verified commands from commands that are only documented or unavailable.
3. Record baseline results, pre-existing failures, limitations, and areas with insufficient evidence. Do not confuse existing test failures with new regressions or automatically accept them as harmless.
4. Identify file access, Git/PR tools, and the ability to delegate a review to a separate context. If delegation is unavailable, configure a manual handoff to a new session. Lack of a PR provider does not block the direct workflow.
5. Agree only on choices that are still missing: Git or direct workflow, story/sprint granularity for branches and PRs, Git bases and targets, fundamental checks, and rework limits. Do not ask again for decisions already recorded in the session or valid configuration.
6. If prerequisites are missing, prepare a remediation plan and agree on it with the human. Identify activities that remain blocked. For a new repository, allow analysis and preparation without declaring a nonexistent build verified.
7. Create or update `.theoneloop/config.md` and `.theoneloop/readiness.md` using the [configuration](templates/config.md) and [readiness](templates/readiness.md) templates. Create other directories only when needed.

## Outcome

Report whether the project is ready, which prerequisites have been verified, and which blockers require preparation. Record human decisions and the next executable step. Initialization alone does not authorize starting product stories.
