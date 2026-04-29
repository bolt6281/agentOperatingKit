# AOK Application Guide

AOK keeps always-read agent instructions small and moves optional workflows, document maps, and governance details behind explicit read conditions.

When an agent is asked to apply AOK, it must not create files immediately. It should first explain what AOK is, inspect the current project state, and present choices in stages.

AOK succeeds when it reduces the amount of context an agent must read for ordinary work. If applying AOK makes every task read more documents by default, the application is wrong.

## Application Order

This document governs first-time AOK adoption and migration of existing projects into AOK structure. After AOK is applied, ordinary documentation, policy, and ADR changes follow `workflows/docs-change.md`.

1. Briefly explain the role of AOK.
2. For an existing project, inspect the current file structure, existing agent instructions, README, docs, workflows, and test/build commands.
3. Present the first-stage AOK interview as choices.
4. Ask only the second-stage questions needed for the user's selections.
5. Produce a recommended scope and component selection proposal.
6. Propose the files to create, modify, move, archive, or deprecate, along with a document migration trace.
7. Create files or change the meaning of existing documents only after user approval.

## Current Project Diagnosis

For existing projects, inspect:

- Existing agent instructions: `AGENTS.md`, `agent.md`, `CLAUDE.md`, `GEMINI.md`, `.cursor/rules`, `.windsurfrules`
- Project description: `README.md`, `docs/`, planning documents, architecture documents
- Work process: issue/PR templates, workflow docs, release docs, deployment docs
- Verification: package scripts, Makefile, CI config, test/lint/typecheck/build commands
- Document state: duplicate docs, outdated docs, conflicting rules, source-of-truth candidates
- Superpowers usage signals: `docs/superpowers/`, `.superpowers/`, existing skill names, spec/plan documents, Superpowers-based workflow wording

Summarize the result briefly for the user. If existing documents conflict, mark them as conflict candidates instead of resolving them silently.

## First-Stage Interview

Ask only these three questions first.

### 1. Starting Scope

- Minimal root `AGENTS.md` only: keep always-read guidance small and do not add optional workflow or governance documents.
- Root `AGENTS.md` plus selected document routing: add only the document map or governance sections the project actually needs.
- Workflows and long-term docs too: consider `.agents/INDEX.md`, selected workflows, ADR/current-status/version-history, or nested `AGENTS.md`.
- Diagnose only: produce a report and proposal without changing files.

### 2. Project State

- New repo: few or no existing documents or workflows.
- Existing repo: README, docs, agent instructions, or workflows already exist.
- Document-drift repo: source-of-truth documents conflict or many docs are stale.

### 3. Superpowers-Based Workflow Usage

- Use workflows: Superpowers is already installed or will be installed before applying AOK workflows.
- Need install guidance: the user wants workflows but needs Superpowers installation instructions.
- Do not use workflows: apply only root `AGENTS.md` guidance and any selected document routing. Do not create AOK workflow documents.
- Decide later: defer workflow creation for now.

If Superpowers is not used, do not provide `.agents/workflows/*.md`. Do not create converted workflows that replace skill calls with generic procedures.

If Superpowers usage is unclear, classify the project with these signals and confirm with the user:

- Likely used: `docs/superpowers/` outputs, `.superpowers/` config, skill names such as `brainstorming`, `writing-plans`, `test-driven-development`, or `verification-before-completion` in existing `AGENTS.md`, or existing spec/plan/review documents.
- Needs confirmation: Superpowers is not named, but agent workflow documents or plan/spec outputs repeat in the repo.
- Not used: there are no skill-call traces and the user says they do not want to install or use Superpowers.

## Second-Stage Interview

Ask only the questions needed based on the first-stage answers.

### AOK Adoption Purpose Details

Ask this only when the user selects more than minimal root `AGENTS.md` or asks for a diagnosis.

- Prepare for development: the repo has planning material and needs an agent operating structure before implementation starts.
- Stabilize work pipelines: feature work, bug fixes, refactors, and documentation changes need repeatable procedures.
- Restore document consistency: reduce drift between code and docs, and between docs themselves.
- Save context: split and index large documents so agents read only what is relevant.
- Clean up an existing project: absorb existing README, agent instructions, docs, and planning material into AOK structure.
- Strengthen collaboration and long-term operation: keep decisions and work history stable across people or agents.
- Control risky work: manage DB, deployment, CI, dependency, authentication, authorization, and other high-risk changes more strictly.

### AOK Core File Scope

Default paths and structures for these items follow [Recommended File Structure](file-structure.md).

- Root `AGENTS.md`: short always-read project overview, common commands, verification routing, and minimal document routing. Prefer 50-100 lines for small projects.
- Document map section: add only when current project documents need source-of-truth status and explicit read conditions.
- Agent instruction governance section: add only when `AGENTS.md`, nested `AGENTS.md`, or `.agents/**` changes need approval rules.
- Global `~/.codex/AGENTS.md`: only when the user wants AOK-aligned personal global rules.
- `.agents/INDEX.md`: index for agent workflows and instruction files.
- `.agents/workflows/*.md`: task-specific procedures only for projects that use Superpowers.
- `.agents/skills/<skill-name>/SKILL.md`: create only through the `repeated-failure` workflow after repeated failures show that a stable judgment procedure is needed and automation is not enough.
- `docs/adr.md` or `docs/adr/`: source of truth for product, architecture, UX, data, and operations decisions. When ADR content grows, prefer `docs/adr/<domain>/<decision-topic>.md` over a numbered file list.
- `docs/current-status.md`: short current operating baseline, verification baseline, deployment/external dependency snapshot, and remaining risks.
- `docs/VERSION_HISTORY.md`: major changes and decision history by version.
- `docs/work-log.md`: only for long-running operational notes that cannot be tracked well in issues, PRs, or plans. Use it as a history sink during ordinary work, and read it only for rollback, recovery, incident investigation, or regression tracing.
- Nested `AGENTS.md`: scope-specific instructions for a repeated project area.
- Not now: exclude this from the current scope and propose it again later if it becomes needed.

### Existing Document Handling

AOK preserves existing documents first, then reflects them into the new structure without information loss.

- Preserve originals: leave existing documents in place and link or summarize them from AOK documents.
- Archive originals: move existing documents to `docs/archive/` and leave only current rules in source-of-truth docs.
- Merge first: absorb existing content into AOK formats and mark duplicates as deprecated candidates.
- Report conflicts first: if existing documents disagree, report the conflict list before changing anything.
- Approve every change: require user approval before moving, deleting, or marking documents as deprecated.

### Existing Workflow Conflict Handling

- Existing rules first: existing project workflows remain primary and AOK supplements them.
- AOK rules first: reshape existing workflows around AOK workflows.
- Mixed adoption: keep valid existing rules and fill only missing parts with AOK.
- Conflict list approval: list conflicts in a table and do not modify them before approval.

### Existing `AGENTS.md` Decomposition

If an existing `AGENTS.md` is large or contains workflow procedures directly, propose a decomposition using this rule:

| Destination | Content |
|---|---|
| Root `AGENTS.md` | Short always-read project overview, common commands, verification routing, and minimal document routing |
| Document map section | Source-of-truth status, read conditions, document status, and document maintenance rules when selected |
| Agent instruction governance section | Approval rules for changing `AGENTS.md`, nested `AGENTS.md`, and `.agents/**` when selected |
| `.agents/INDEX.md` | Workflow routing, approved agent instruction file list, project-specific skill index, AOK adoption decision summary |
| `.agents/workflows/*.md` | Repeated procedures such as feature work, bug fixes, refactors, documentation changes, risky changes, and review feedback |
| Nested `AGENTS.md` | Directory- or area-specific coding rules, verification commands, design rules, or operations rules |
| General docs | Product decisions, current operating state, version history, deployment procedures, and long-running notes that belong in project reference documents rather than agent instructions |

If placement is ambiguous, keep only a short routing rule in root `AGENTS.md` and list the candidate destination and reason in the application proposal.

### Document Governance Strictness

- Minimal: no document map; root `AGENTS.md` only lists key document locations.
- Loose: agents may update relevant docs, but new document creation is proposed first.
- Standard: document map records source-of-truth, archive, and deprecated status.
- Strict: source of truth, document status, last review date, and conflict-handling rules are enforced.

### Existing File Change Approval

- Approve proposal once: approve the full list of files to create, modify, move, or archive.
- Approve per file: ask before each existing file is modified or moved.
- Backup first: preserve originals in an archive or backup path before changing them.
- Read-only diagnosis first: produce only a diagnosis report and application proposal.
- Exclude global files: do not inspect or modify `~/.codex/AGENTS.md`.

## Selection Mapping Rules

| User Selection | AOK Behavior |
|---|---|
| Minimal root `AGENTS.md` only | Create or update only the short always-read root instructions. Do not add workflows, ADR, current status, version history, work log, or archive unless separately selected. |
| Root `AGENTS.md` plus selected document routing | Add only the selected document map or governance sections. Keep optional details behind explicit read conditions. |
| Workflows and long-term docs too | Consider `.agents/INDEX.md`, workflows, nested `AGENTS.md`, ADR, current status, and version history using the component selection criteria. |
| Prepare for development | Create root `AGENTS.md`, common commands, and verification routing first. |
| Global `~/.codex/AGENTS.md` | Inspect existing global instructions, then propose add/merge/keep/skip options and modify only after approval. |
| Stabilize work pipelines | Apply `.agents/INDEX.md` and selected `.agents/workflows/*.md` only if Superpowers is used. |
| Need Superpowers guidance | Provide installation instructions for the current LLM environment, then confirm workflow adoption after installation. |
| Do not use Superpowers | Do not create workflow documents; apply only basic root `AGENTS.md` operating guidance and any selected document routing. |
| Restore document consistency | Prioritize document maps, source-of-truth markers, conflict lists, and archive policy. |
| Save context | Split large documents and strengthen indexing rules so agents read only relevant files. |
| Clean up existing project | Read existing documents one by one and record loss risks in the migration trace. |
| Strengthen collaboration | Review ADR, current status, version history, and nested `AGENTS.md` candidates. If long-running operations documents already exist, mark them as preserve or cleanup candidates instead of creating new ones. |
| Control risky work | If Superpowers is used, prioritize risky-change workflow, approval rules, rollback, and verification. |
| Repeated failure or project-specific judgment | First check whether tests, lint, CI, or scripts can prevent the issue. Propose a project-specific skill only when automation is not enough and the judgment procedure has stabilized. |
| Preserve originals | Do not delete or move existing documents; connect them by links and summaries. |
| Archive originals | Propose documents that should move to `docs/archive/`. |
| Merge first | Merge duplicate content into source-of-truth docs and check for information loss. |
| Report conflicts first | Build a conflict table before finalizing source-of-truth documents. |

## Document Migration Trace

When absorbing existing project documents into AOK structure, include this table in the proposal.

| Original Path | Extracted Information | Destination | Preservation Method | Conflict | Loss Risk |
|---|---|---|---|---|---|
| `[existing document]` | `[core information]` | `[new or retained location]` | keep / merge / archive / deprecated candidate | yes / no | low / medium / high |

Do not delete, move, or deprecate items with medium or high loss risk before user confirmation.

## Application Proposal Format

After receiving the user's choices, the agent proposes:

```md
## AOK Application Proposal

- Adoption purpose:
- Recommended scope:
- Selected AOK components:
- Files to create:
- Files to modify:
- Existing files to preserve or move:
- Deprecated or archived candidates:
- Superpowers installation or workflow deferral:
- Existing workflow and AOK workflow conflicts:
- Document migration trace:
- Information-loss prevention:
- Items to confirm:
- User approval required before applying: yes
```

Do not create files or change the meaning of existing documents before the user approves.

## Output Quality Rules

- Final applied files must not contain unresolved placeholders such as `[command]`, `[path]`, `[document]`, or TODO.
- Unknown values must go into `Items To Confirm` instead of being guessed in the document body.
- If examples are needed, label them clearly as examples so they are not confused with project facts.
- Before creating a new Markdown document, check whether updating an existing document is enough.

## Existing-Project Application Rules

- Read existing files one by one and preserve all information that can fit into the AOK format.
- Mark information that might be lost as preservation candidates, conflict candidates, or items to confirm.
- If existing work pipelines overlap with AOK workflows, follow the selected conflict-handling option.
- Do not delete, move, deprecate, or archive existing documents before confirming original preservation.
- If the current source of truth is unclear, propose candidates and evidence instead of deciding silently.
