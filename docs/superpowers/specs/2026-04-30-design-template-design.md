# DESIGN.md Template Design

## Goal

Add `DESIGN.md` as an optional AOK template that target repositories can adopt when they need a project-specific UI design reference for coding agents.

## Positioning

`DESIGN.md` is not an always-read agent instruction file. It is a routed reference document read only for UI, UX, frontend, visual system, or component styling work.

The applied path in target repositories is `<repo>/DESIGN.md`. AOK stores the reusable source template at:

- `ko/aok/templates/design.md`
- `en/aok/templates/design.md`

## Required AOK Documentation Changes

- Add the template to the Korean and English AOK source indexes.
- Add component-selection guidance explaining when to create or skip `DESIGN.md`.
- Add the default path and role to the file-structure guide.
- Add application-guide language so AOK adoption can select `DESIGN.md` intentionally.
- Add minimal root `AGENTS.md` routing so UI work can discover `DESIGN.md` without making every task read it.
- Add nested `AGENTS.md` guidance so area-specific design notes do not duplicate the root design baseline.
- Add document-map language for managing `DESIGN.md` as a design source-of-truth when document governance is selected.
- Add README component-selection rows so the public overview reflects the new optional component.
- Add README attribution explaining that the template follows the Google Stitch / Google Labs DESIGN.md format but is adapted for AOK.

## Template Shape

The template should be project-native rather than brand-copy oriented. It should capture:

- Purpose and scope
- Visual theme and atmosphere
- Color palette and semantic roles
- Typography rules
- Layout and spacing
- Component styling
- Depth, radius, and motion
- Responsive behavior
- Accessibility guardrails
- Do and do not rules
- Agent usage notes
- Items to confirm

Applied output must not retain unresolved placeholders in the main body. Unknown values should be moved to an "Items To Confirm" section.

## Read Rules

Read `DESIGN.md` when:

- Creating or changing screens, landing pages, dashboards, components, or design systems.
- Changing colors, typography, spacing, radius, elevation, responsive behavior, or interaction tone.
- Reviewing whether a UI change matches the project's visual system.

Do not read `DESIGN.md` for documentation-only, backend-only, CLI-only, build-only, or test-only work unless those changes affect user-facing UI.

## Non-Goals

- Do not add a dedicated workflow file for `DESIGN.md`.
- Do not make `DESIGN.md` mandatory for all projects.
- Do not place long design tokens in root `AGENTS.md`.
- Do not claim third-party `DESIGN.md` files are official brand systems.

## Approval

The user approved the recommended approach: add `DESIGN.md` as an optional AOK template for target repositories, with selection criteria and routing updates.
