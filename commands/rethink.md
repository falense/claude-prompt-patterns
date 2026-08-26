---
name: rethink
description: Solve a problem from first principles instead of patching existing code
arguments:
  - name: task
    description: The problem, bug, or change to apply first-principles thinking to
    required: true
---

Do NOT patch or bandaid the existing code. Instead:

1. Read and understand the relevant code thoroughly
2. Step back and consider: is the current approach the right one?
3. If the existing structure is wrong or clumsy, fix the structure — don't work around it
4. Implement the solution properly from first principles, even if that means replacing existing code

A clean implementation that solves the problem correctly is always better than a minimal hack on top of a flawed approach. Don't preserve bad code just because it's already there.

Apply this thinking to: $ARGUMENTS
