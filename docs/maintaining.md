# Maintaining TheOneLoop

TheOneLoop is distributed as six independently installable, text-only skill directories. Each contains all its required references, templates, and phase instructions. There are no source-only resource directories in the repository root.

## Package boundaries

Every local Markdown link inside a skill must resolve within that same skill directory. Installed skills must not depend on a source checkout, a sibling installation, a network download, or a link back to the repository.

Only the six entrypoints are named `SKILL.md` and contain discovery frontmatter. Bundled phase documents in `references/workflows/` are ordinary Markdown without skill metadata, so they do not become additional discoverable skills.

Project state belongs in the target project's `.theoneloop/` directory, separate from installed instructions and templates.

## Authoritative files

Keep one editing source for shared material. The other copies exist so that each installed skill is self-contained; update them in the same change as their source.

| Resource | Authoritative location | Additional copies |
|---|---|---|
| Shared protocol and document format | [theoneloop-init/references/](../skills/theoneloop-init/references/) | `references/` in all other skills |
| Configuration and readiness templates | [theoneloop-init/templates/](../skills/theoneloop-init/templates/) | None |
| Issue, story, and sprint templates | [theoneloop-plan/templates/](../skills/theoneloop-plan/templates/) | `theoneloop-accept/templates/` |
| Handoff template | [theoneloop-implement/templates/handoff.md](../skills/theoneloop-implement/templates/handoff.md) | None |
| Review template | [theoneloop-review/templates/review.md](../skills/theoneloop-review/templates/review.md) | `theoneloop-implement/templates/` |
| Verification template | [theoneloop-verify/templates/verification.md](../skills/theoneloop-verify/templates/verification.md) | `theoneloop-implement/templates/` |
| Phase instructions | Each skill's `SKILL.md` | Bundled workflows described below |

Reference and template copies must be byte-for-byte identical to their authoritative files.

## Bundled phase instructions

| Package | Bundled workflow | Source |
|---|---|---|
| `theoneloop-implement` | `references/workflows/theoneloop-review.md` | [Review skill](../skills/theoneloop-review/SKILL.md) |
| `theoneloop-implement` | `references/workflows/theoneloop-verify.md` | [Verification skill](../skills/theoneloop-verify/SKILL.md) |
| `theoneloop-accept` | `references/workflows/theoneloop-plan.md` | [Planning skill](../skills/theoneloop-plan/SKILL.md) |

Copy the source skill body without its YAML frontmatter or installation-location paragraph. Rewrite its local links for its location in `references/workflows/`: `references/...` becomes `../...`, and `templates/...` becomes `../../templates/...`. Keep phase behavior unchanged.

When adding a resource link, include its full local dependency chain. A successful full-set installation must not hide an incomplete individual package. Bundled review instructions still require a context separate from implementation; bundling does not turn self-review into independent review.

## Validate a change

1. Confirm that CLI discovery finds exactly six skills with names matching their directories.
2. Check metadata and compare shared copies with the authoritative locations above.
3. Check bundled workflow content against the documented transformation.
4. Resolve every local link and verify it stays within its containing skill directory.
5. Install the complete set into an isolated project, checking copy mode and default link mode as relevant to the change.
6. Install affected skills individually and verify their files without relying on other installed skills.
7. Record the CLI version, platform, results, and limitations in the [publishing guide](publishing.md).

Development tools may be used for these checks, but no validation script, executable hook, or runtime dependency is distributed with the skills. Installation validation is separate from exercising an actual sprint with a coding agent.
