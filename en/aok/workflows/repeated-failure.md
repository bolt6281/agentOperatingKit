# Repeated Failure / Project-Specific Skill Workflow

> Managed agent workflow document. Do not meaningfully change without user approval.
> Prerequisite: this workflow assumes an agent environment where Superpowers skills are installed.

## Purpose

When the same kind of mistake or failure repeats, look for automation before adding documents or skills.

## Procedure

1. When the same type of mistake or failure repeats, summarize root cause and recurrence conditions.
2. If automation can prevent it, prefer scripts, tests, lint, or CI over a skill.
3. If judgment is needed, use the principles of `writing-skills`, but write project-specific skills with an abbreviated procedure.
4. Treat project-specific skills as project-local operational knowledge, not global or official skills.
5. If a new project-specific skill is needed, propose `.agents/skills/<skill-name>/SKILL.md` and the `.agents/INDEX.md` project-specific skill table update before creating it.
6. If project-specific skills become numerous, create `.agents/skills/INDEX.md` only after user approval.
7. For future tasks of the same type, check the project-specific skill table in `.agents/INDEX.md`.

## Priority

1. If tests, lint, or CI can prevent the issue, automate it.
2. If automation is hard and judgment is needed, document the workflow.
3. If the pattern is frequent and stable, extract it into a project-specific skill.

## Before Completion

- Was the root cause categorized as documentation shortage or automation shortage?
- Can the issue be solved without a new document or skill?
- Was user approval received before creating a new project-specific skill?
