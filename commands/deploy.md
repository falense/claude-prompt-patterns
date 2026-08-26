---
name: deploy
description: Deploy the current project, following the project's .claude/deploy.md cheat file (creating it if missing)
arguments:
  - name: target
    description: Optional environment or extra instructions (e.g. "staging")
    required: false
---

Deploy the current project.

Look for `.claude/deploy.md` in the project root.

**If it exists:** follow it step by step. Don't explore or second-guess it — it is the known-good procedure.

**If it doesn't exist:** work out how this project is deployed (CI workflows, Makefile/scripts, README, Dockerfiles, IaC, package scripts). Write `.claude/deploy.md` with the exact, ordered steps: prerequisites, the commands to run, and how to verify the deploy succeeded. Keep it terse — commands over prose. Then run it.

**If a step fails** or the file turns out to be wrong or outdated: fix the file first, then continue. The file must always reflect what actually works.

$ARGUMENTS
