# claude-prompt-patterns

Claude Code plugin with reusable prompting patterns as slash commands.

## Structure

- `commands/<name>.md` — one file per slash command. Frontmatter: `name`, `description`, `arguments`. Body is the prompt; `$ARGUMENTS` is replaced with the user's input.
- `.claude-plugin/plugin.json` — plugin manifest.

## Versioning

- Do not bump the version manually. release-please bumps `.claude-plugin/plugin.json` and the changelog from conventional commits:
  - `fix:` → patch
  - `feat:` → minor
  - `feat!:` or a `BREAKING CHANGE:` footer → major

## Local testing

- `.claude/commands/*.md` are relative symlinks to `commands/*.md`, so the slash commands work inside this repo without installing the plugin. Add a symlink there when adding a new command.
