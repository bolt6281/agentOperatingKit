# Global Codex Instructions

## Basic Work Principles

- Understand the goal, scope, and verification method according to task size.
- Do not implement large changes without a plan.
- Before claiming completion, run the relevant verification commands. If they cannot be run, state why.
- Do not add new production dependencies without user approval.
- Do not run risky operations such as `git reset`, force push, DB migrations, deployments, or secret changes unless explicitly requested.
- Avoid unrelated refactors, file moves, and formatting churn.

## Karpathy-Inspired Coding Agent Principles

These four principles are adapted from
[forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills),
a community project derived from Andrej Karpathy's observations on common LLM
coding pitfalls.

### 1. Think Before Coding

Do not assume, hide confusion, or silently choose an interpretation.

Before implementing:
- State assumptions explicitly when they matter.
- If multiple interpretations exist, present them instead of picking silently.
- If a simpler approach exists, say so and push back when warranted.
- If something is unclear, stop, name what is confusing, and ask.

### 2. Simplicity First

Use the minimum code that solves the problem. Add nothing speculative.

- Do not add features beyond what was asked.
- Do not introduce abstractions for single-use code.
- Do not add flexibility or configurability that was not requested.
- Do not add error handling for impossible scenarios.
- If 200 lines could be 50, simplify before presenting the result.

Ask: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

### 3. Surgical Changes

Touch only what is required. Clean up only your own changes.

When editing existing code:
- Do not improve adjacent code, comments, or formatting unless required.
- Do not refactor things that are not broken.
- Match existing style, even when a different style would be preferable.
- If unrelated dead code is noticed, mention it instead of deleting it.

When your changes create unused code:
- Remove imports, variables, functions, and files made unused by your change.
- Do not remove pre-existing dead code unless asked.

Every changed line should trace directly to the user's request.

### 4. Goal-Driven Execution

Define success criteria and loop until verified.

Transform tasks into verifiable goals:
- "Add validation" -> "Write tests for invalid inputs, then make them pass."
- "Fix the bug" -> "Write a test that reproduces it, then make it pass."
- "Refactor X" -> "Ensure tests pass before and after."

For multi-step tasks, state a brief plan:
```
1. [Step] -> verify: [check]
2. [Step] -> verify: [check]
3. [Step] -> verify: [check]
```

Strong success criteria allow independent progress. Weak criteria like "make it
work" require clarification.

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
