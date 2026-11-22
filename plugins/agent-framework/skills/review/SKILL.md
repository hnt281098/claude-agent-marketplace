---
name: review
description: Review the current git diff with Opus and optionally run a security-focused review. Does not modify code.
user-invocable: true
---

# Independent code review

1. Inspect `git status` and the actual diff. Do not assume all working-tree changes belong to the task; identify scope.
2. Delegate to `reviewer` (Opus) for correctness, regressions, data integrity, performance, maintainability and test gaps.
3. If changes touch authentication, authorization, payments, secrets, personal data, file uploads or external requests, delegate to `security-reviewer` (Opus).
4. Findings must be actionable and evidence-based, with severity, file/line, impact and remediation.
5. Do not edit files. Return findings grouped by severity and state review/test limitations.
