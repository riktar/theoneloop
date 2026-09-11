# Install TheOneLoop

[Back to the quick start](../README.md)

Run installation commands in the project where you want to use the skills. The external installer requires Node.js and npm; the skill packages themselves contain only Markdown.

## Install and update

Install the full set and choose agents interactively:

```text
npx skills add riktar/theoneloop --skill '*'
```

Select the four intended clients explicitly using copy mode:

```text
npx skills add riktar/theoneloop --skill '*' --agent claude-code codex opencode pi --copy
```

Install an individual skill:

```text
npx skills add riktar/theoneloop --skill theoneloop-implement
```

Use `--global` for user-level installation. Without it, installation is project-local. Use `--copy` when copies are preferred to links. Node/npm are requirements of the external installer, not dependencies shipped with TheOneLoop. [CLI options](https://github.com/vercel-labs/skills#options).

Update installed skills using the CLI:

```text
npx skills update
```

## Install from a local checkout

Replace the source path with your checkout, and run this from the target project:

```sh
npx skills add /absolute/path/to/theoneloop --skill '*'
```

## Start using the skills

Use your agent's skill selector or name a skill in your request. Begin with `theoneloop-init`, then follow the [first sprint walkthrough](../README.md#your-first-sprint).

For package test results and their scope, see the [validation record](publishing.md#validation-record).
