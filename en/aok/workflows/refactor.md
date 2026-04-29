# Refactor Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

Improve structure while preserving external behavior. Do not mix behavior changes into a refactor.

## Procedure

1. For medium or larger refactors, use `brainstorming` to define scope, goal, and forbidden behavior changes.
2. If the scope is broad, use `writing-plans` to create a step-by-step plan.
3. Write preservation tests for existing behavior first. If behavior preservation is central, use `test-driven-development`.
4. If a plan exists, use `executing-plans` to execute in small steps.
5. Use `subagent-driven-development` or `dispatching-parallel-agents` only when independent areas are clear and the user has allowed it.
6. For medium or larger refactors, shared-boundary changes, or regression risk, use `requesting-code-review` to check external behavior, responsibility boundaries, and missing tests.
7. Use `receiving-code-review` before applying review feedback.
8. Use `verification-before-completion` to confirm existing behavior was preserved.

## Before Completion

- Was the refactor scope and forbidden behavior change list explicit?
- Is there an existing-behavior preservation test or alternative verification?
- If behavior change appeared, was it treated as a separate behavior change?
- Were actual verification results checked before completion?
