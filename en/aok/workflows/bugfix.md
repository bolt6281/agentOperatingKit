# Bug Fix Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Fix bugs through reproduction and root-cause confirmation instead of guessing.

## Procedure

1. Use `systematic-debugging`.
2. Confirm reproduction conditions, expected behavior, actual behavior, and impact scope.
3. Confirm root cause and record evidence for excluding other plausible causes.
4. Use `test-driven-development` to create a failing test or reproduction script first.
5. Implement the minimal fix.
6. For medium or larger fixes, shared-boundary changes, or regression risk, use `requesting-code-review` to check the fix direction and regression risk.
7. If review feedback arrives, use `receiving-code-review`.
8. Use `verification-before-completion` to confirm that the reproduction case and related regression tests pass.

## Before Completion

- Were reproduction conditions and expected/actual behavior separated?
- Was root cause confirmed?
- Was a failing test or reproduction script created first, or was the reason it could not be created explained?
- Were related regression checks actually run?
