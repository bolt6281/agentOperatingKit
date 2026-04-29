# AOK Template Pack

This file is not an actual agent instruction file. It is the source index for applying Agent Operating Kit(AOK) to a new or existing project.

AOK is an operating kit that reduces context waste and document drift by organizing agent instructions, work workflows, document maps, and document governance.

When applying AOK, do not copy this file directly into the target project. Read only the documents needed for the selected scope and apply only the items approved by the user.

Korean version: [../ko/agentOperatingKit.md](../ko/agentOperatingKit.md)

## Reading Order

1. [AOK Application Guide](aok/application-guide.md)
2. [Adoption Levels](aok/adoption-levels.md)
3. [Recommended File Structure](aok/file-structure.md)
4. [Superpowers Installation and Workflow Preconditions](aok/superpowers-install.md), if workflows are selected
5. Only the selected template or workflow files

## Core Rules

- Keep only the core instructions that are safe to read every time in `AGENTS.md`.
- Split long procedures into `.agents/workflows/*.md` only for projects that use Superpowers.
- Do not create nested `AGENTS.md` files automatically. Create them only after user approval when repeated, scope-specific rules exist.
- Treat agent instruction files as managed policy files.
- Use uppercase `AGENTS.md` by default.
- Exclude `~/.codex/AGENTS.md` by default because the user may already have personal global instructions. Suggest it only when the user selects it.
- Apply AOK in this order: choice-based interview, application proposal, user approval, then implementation.
- If a project does not use Superpowers, do not provide `.agents/workflows/*.md`; apply only the basic root `AGENTS.md` operating guidance.

## Templates

| Purpose | File |
|---|---|
| Global Codex instructions | [aok/templates/global-agents.md](aok/templates/global-agents.md) |
| Repo root `AGENTS.md` | [aok/templates/repo-agents.md](aok/templates/repo-agents.md) |
| `.agents/INDEX.md` | [aok/templates/agents-index.md](aok/templates/agents-index.md) |
| Agent instruction change proposal chat form | [aok/templates/agent-change-proposal.md](aok/templates/agent-change-proposal.md) |
| Nested `AGENTS.md` | [aok/templates/subdir-agents.md](aok/templates/subdir-agents.md) |
| ADR | [aok/templates/adr.md](aok/templates/adr.md) |
| Current status document | [aok/templates/current-status.md](aok/templates/current-status.md) |
| Version history | [aok/templates/version-history.md](aok/templates/version-history.md) |
| Work log | [aok/templates/work-log.md](aok/templates/work-log.md) |

## Workflow Templates

Workflow templates are provided only for projects that use Superpowers.

| Work Type | File |
|---|---|
| Feature or behavior change | [aok/workflows/feature-change.md](aok/workflows/feature-change.md) |
| Bug fix | [aok/workflows/bugfix.md](aok/workflows/bugfix.md) |
| Refactor | [aok/workflows/refactor.md](aok/workflows/refactor.md) |
| Documentation, policy, or ADR change | [aok/workflows/docs-change.md](aok/workflows/docs-change.md) |
| Config, build, CI, dependency, deployment, or DB change | [aok/workflows/risky-change.md](aok/workflows/risky-change.md) |
| Research or technical decision | [aok/workflows/research-decision.md](aok/workflows/research-decision.md) |
| Review feedback handling | [aok/workflows/review-feedback.md](aok/workflows/review-feedback.md) |
| Repeated failure or project-specific skill extraction | [aok/workflows/repeated-failure.md](aok/workflows/repeated-failure.md) |

## Application Notes

- For existing projects, read the existing documents and workflows first, then ask the user how to preserve originals and handle conflicts.
- Before creating, modifying, moving, or archiving files in the target project, propose the exact file list and get user approval.
- Read only the documents relevant to the selected task. Do not read the entire AOK pack by default.
- Do not leave unresolved placeholders such as `[command]`, `[path]`, or TODO in applied output files. Put unknown values in a separate "Items To Confirm" section.
