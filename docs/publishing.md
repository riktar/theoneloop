# Publishing TheOneLoop on skills.sh

The source is prepared as six self-contained skill directories. See [maintenance instructions](maintaining.md) for the authoritative files and bundled copies.

## Before publication

1. Create a public GitHub repository under the chosen owner.
2. Choose and include an explicit license for reuse and redistribution. A license has not yet been selected. [GitHub licensing documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository).
3. Replace `OWNER/theoneloop` in installation examples with the real repository identifier.
4. Publish the files, perform an installation from that public source, and check the installed resources before announcing a release.

No npm publication, service, plugin manifest, or executable TheOneLoop installer is required. The external `skills` CLI handles discovery and installation. [CLI documentation](https://github.com/vercel-labs/skills).

## Install and update

Install the full set and choose agents interactively:

```text
npx skills add OWNER/theoneloop --skill '*'
```

Select the four intended clients explicitly using copy mode:

```text
npx skills add OWNER/theoneloop --skill '*' --agent claude-code codex opencode pi --copy
```

Install an individual skill:

```text
npx skills add OWNER/theoneloop --skill theoneloop-implement
```

Use `--global` for user-level installation. Without it, installation is project-local. Use `--copy` when copies are preferred to links. Node/npm are requirements of the external installer, not dependencies shipped with TheOneLoop. [CLI options](https://github.com/vercel-labs/skills#options).

Update installed skills using the CLI:

```text
npx skills update
```

## Listing on skills.sh

The skills.sh FAQ describes automatic listing through installation telemetry when users run `npx skills add OWNER/REPO`. No manual leaderboard submission is required. Recorded installations affect visibility and ranking; the documentation does not promise an indexing time. [Official FAQ](https://www.skills.sh/docs/faq).

Local packaging tests use disabled telemetry. They do not publish a repository or establish a skills.sh listing. Public-source installation and listing verification remain pending.

## Validate a local checkout

From an isolated target project, substitute the actual source path:

```text
npx skills@1.5.25 add /absolute/path/to/theoneloop --list
npx skills@1.5.25 add /absolute/path/to/theoneloop --skill '*' --agent claude-code codex opencode pi --copy --yes
```

The pinned version identifies the installer used for local packaging checks. Check installed file contents, local references, and package boundaries as well as installer output. A complete sprint in each coding agent is a separate behavioral test.

## Validation record

Checked on September 11, 2026, on Windows with Node `v22.22.0` and `skills` CLI `1.5.25`.

| Check | Result |
|---|---|
| Discovery | Exactly six `theoneloop-*` entrypoints found. |
| Full-set copy installation | Passed with Claude Code, Codex, OpenCode, and Pi selected. |
| Default installation mode | Canonical skill copies and Claude Code links verified. |
| Individual installation | All six skills installed separately, with required resources included. |
| Installed contents | 204 files across 36 installed skill directories match their packages. |
| References | 346 link checks across repository and installed resources passed; installed local links stay within their skill boundary. |
| Shared copies | References, templates, and bundled phase instructions match their authoritative sources. |
| Naming and cleanup | No previous project name remains in distributed files; the root contains only `README.md`, `docs/`, and `skills/`. |
| File types | All files under `skills/` are Markdown. Marketing assets live outside the skill packages and are not installed. |

The four-client command uses `--copy` to provide explicit client directories, including Pi. Installation checks verify package layout and resource availability, not a complete sprint executed inside each agent.

Public-source installation, global installation, other operating systems, and full sprint execution in each target client remain outside the local packaging test scope.
