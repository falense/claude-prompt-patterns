# Deploy

This is a Claude Code plugin. "Deploy" = publish to GitHub, let release-please version it, and make sure the marketplace index points at it.

## Prerequisites

- On `main`, clean working tree, all work committed with conventional commits
- `gh auth status` logged in as `falense`
- `claude plugin validate .` passes
- One-time: the repo must allow Actions to open PRs, or release-please fails with "GitHub Actions is not permitted to create or approve pull requests":
  ```
  gh api -X PUT repos/falense/claude-prompt-patterns/actions/permissions/workflow -f default_workflow_permissions=write -F can_approve_pull_request_reviews=true
  ```

## Steps

1. Push:
   ```
   git push -u origin main
   ```
2. Release-please runs on push (`.github/workflows/release-please.yml`). Wait for it, then merge the release PR it opens (if any):
   ```
   gh run watch --exit-status $(gh run list --workflow release-please.yml -L1 --json databaseId -q '.[0].databaseId')
   gh pr list --label "autorelease: pending"
   gh pr merge <n> --squash
   ```
   Merging triggers a second run that tags the release and bumps `.claude-plugin/plugin.json`.
3. Marketplace index (`../claude-marketplace`): the entry for `claude-prompt-patterns` must point at `falense/claude-prompt-patterns`. If it changed, commit and push it:
   ```
   git -C ../claude-marketplace pull --rebase && git -C ../claude-marketplace push
   ```

## Verify

```
gh release list -R falense/claude-prompt-patterns
claude plugin marketplace update dig && claude plugin install claude-prompt-patterns@dig
```
