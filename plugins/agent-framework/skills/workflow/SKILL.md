---
name: workflow
description: Run the multi-agent engineering workflow for a feature, bug fix or refactor. Uses Haiku discovery, Sonnet implementation, Haiku verification and Opus review.
user-invocable: true
---

# Multi-agent development workflow

For the user's requested task:

1. **Discover:** delegate read-only repository exploration to `explorer` (Haiku). Identify stack, relevant files, conventions, test commands and risks. Do not assume project structure.
2. **Plan:** summarize acceptance criteria, implementation scope and test strategy. Ask only if a blocking requirement is ambiguous.
3. **Implement:** delegate implementation to `code-developer` (Sonnet). For UI/API boundary work, delegate test design/implementation to `e2e-engineer` (Sonnet). Avoid overlapping file ownership.
4. **Verify:** delegate actual checks to `test-runner` (Haiku). Run targeted checks first. Never use production services or data.
5. **Review:** delegate the diff to `reviewer` (Opus), read-only. For auth, payments, data access or sensitive flows, also use `security-reviewer` (Opus).
6. **Fix loop:** send confirmed findings to `code-developer` (Sonnet), rerun affected checks and request reviewer verification.
7. **Report:** list changed files, commands executed, pass/fail results, review findings resolved and remaining risks.

Right-size the process:
- Small change: implement, targeted test, review if risk warrants.
- Medium change: full discover → implement → test → review.
- Large/cross-service change: split independent tasks only after contracts are agreed.

Do not claim completion unless required checks actually ran. If a tool/agent is unavailable, state the limitation and continue safely where possible.
