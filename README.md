# claude-prompt-patterns

Reusable prompting patterns packaged as Claude Code slash commands.

## Install

```
/plugin install claude-prompt-patterns@dig
```

## Commands

### `/rethink <task>`

Solve a problem from first principles instead of patching existing code. Claude reads the relevant code, questions whether the current approach is right, fixes the structure if it is wrong, and implements a clean solution — even if that means replacing code.

```
/rethink the retry logic in api/client.py keeps growing special cases
```

### `/architect [scope]`

Delegate implementation while this agent acts as architect. Once a design has been agreed upon in the conversation, Claude decomposes it into independent work packages with pinned-down interfaces, spawns one Opus agent per package in parallel, reviews each agent's actual diff against the brief, sends back precise fixes, and then verifies that the pieces integrate. Scope defaults to whatever has been agreed so far.

```
/architect
/architect the ingestion pipeline we just designed, not the UI yet
```

### `/deploy [target]`

Deploy the current project using a project-local cheat file, `.claude/deploy.md`. If the file exists, Claude follows it without exploring. If not, Claude figures out how the project is deployed, writes the steps to the file, and runs them. If a step fails, the file is corrected before continuing, so it always reflects what actually works.

```
/deploy
/deploy staging
```

## Development

```bash
claude plugin validate .
claude plugin install ./
```
