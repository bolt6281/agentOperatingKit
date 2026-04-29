# Global Codex Instructions

## Basic Work Principles

- Understand the goal, scope, and verification method according to task size.
- Do not implement large changes without a plan.
- Before claiming completion, run the relevant verification commands. If they cannot be run, state why.
- Do not add new production dependencies without user approval.
- Do not run risky operations such as `git reset`, force push, DB migrations, deployments, or secret changes unless explicitly requested.
- Avoid unrelated refactors, file moves, and formatting churn.

## Communication

- Keep responses direct and concise.
- If requirements are ambiguous, ask only the minimum questions needed to proceed.
- Prefer concrete choices over open-ended questions when possible.

## Documentation Principles

- Do not create new Markdown documents by default.
- Prefer updating an existing document or adding a section to it.
- If a new document seems necessary, first propose the filename, path, purpose, and why existing documents are insufficient.

## Encoding

- Preserve the existing file encoding.
- For Korean documents, check for encoding corruption before saving.

## Agent Instruction File Management

- Treat `AGENTS.md`, nested `AGENTS.md`, and `.agents/**` files as managed policy files.
- Do not create or meaningfully change agent instruction files unless the user explicitly asks.
- Meaning-preserving cleanup such as typo fixes, broken internal links, or path corrections after actual file moves is allowed.
- If a new rule seems necessary, propose the change instead of editing the file directly.
- A change proposal must include path, purpose, scope, conflict with existing rules, and verification method.
