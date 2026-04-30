---
version: alpha
name: Project Design System
description: Project visual identity for coding agents. Replace the sample values with project-specific tokens before using this as a source of truth.
colors:
  primary: "#1A1C1E"
  secondary: "#6C7278"
  tertiary: "#B8422E"
  neutral: "#F7F5F2"
  surface: "#FFFFFF"
  on-surface: "#1A1C1E"
  error: "#B3261E"
typography:
  headline-lg:
    fontFamily: Inter
    fontSize: 48px
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.02em
  body-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.6
  label-md:
    fontFamily: Inter
    fontSize: 13px
    fontWeight: 600
    lineHeight: 1.2
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 32px
  xl: 64px
rounded:
  sm: 4px
  md: 8px
  lg: 12px
  full: 9999px
components:
  button-primary:
    backgroundColor: "{colors.tertiary}"
    textColor: "{colors.surface}"
    typography: "{typography.label-md}"
    rounded: "{rounded.md}"
    padding: 12px
  button-primary-hover:
    backgroundColor: "{colors.primary}"
  card-default:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.md}"
    padding: 24px
---

# DESIGN.md

## Overview

This file describes the project's visual identity in a form coding agents can read. When applied to a real project, place it at `<repo>/DESIGN.md` and replace the sample YAML front matter tokens with project-specific values.

`DESIGN.md` is not an always-read agent instruction file. Read it only when creating screens, landing pages, dashboards, components, or design systems, or when changing colors, typography, spacing, radius, elevation, or responsive behavior.

Design direction: `[Describe the overall impression the project should have, the primary users, and the impressions it should avoid in 3-6 sentences.]`

## Colors

Describe colors by role, not just by brand name. YAML tokens are the exact values; this prose explains when and how to apply them.

- **Primary (#1A1C1E):** Used for core text, structural emphasis, and areas that need strong contrast.
- **Secondary (#6C7278):** Used for supporting text, metadata, dividers, and inactive states.
- **Tertiary (#B8422E):** Used sparingly for the most important action, key highlights, and critical emphasis.
- **Neutral (#F7F5F2):** Used for page backgrounds and broad calm surfaces.
- **Surface (#FFFFFF):** Used for cards, panels, inputs, and content layers.
- **Error (#B3261E):** Used only for errors, deletion, and dangerous states.

## Typography

Manage typography with semantic levels such as `headline`, `body`, and `label`. Hierarchy must be clear within each screen, and hero-scale type should not appear inside compact panels or tables.

- **Headlines:** Used for important page titles and section entry points. Use only when strong hierarchy is needed.
- **Body:** Used for descriptions, form help, and ordinary content. Keep line height readable for longer text.
- **Labels:** Used for buttons, tabs, metadata, form labels, and technical labels.

## Layout

Layout follows a consistent spacing scale and grid rhythm. Work surfaces can be denser; marketing or editorial surfaces can use more generous section rhythm.

- Default content width: `[example: 1120px]`
- Default page padding: `[example: 24px desktop, 16px mobile]`
- Spacing baseline: prefer YAML `spacing` tokens.
- On mobile, navigation, tables, and toolbars must collapse or use an alternative narrow-width presentation.

## Elevation & Depth

Create depth with tonal layers, borders, spacing, and contrast before using heavy shadows. Use shadows only for real foreground hierarchy such as modals, popovers, and floating menus.

- Flat surfaces use borders and background contrast for separation.
- Floating surfaces use short, soft shadows.
- Interactive states should prefer color, border, focus ring, and motion over depth changes.

## Shapes

Shape language follows the YAML `rounded` tokens. Do not mix sharp corners and highly rounded corners in the same screen without a clear reason.

- Default containers and inputs prefer `rounded.md`.
- Small chips and badges may use `rounded.full`.
- Dense tables, grids, and editor surfaces should keep radius low.

## Components

Component tokens define default styles for repeated atoms. State variants should use related keys such as `button-primary-hover`.

- **Buttons:** The primary button is reserved for the single most important action on a screen. Secondary actions use lower emphasis and should not compete with the primary action.
- **Inputs:** Focus states must be visible to keyboard users. Errors must appear near the relevant field with specific copy.
- **Cards / panels:** Use for repeated items, modals, and framed tools. Do not wrap entire page sections as cards or nest cards inside cards.
- **Navigation:** Active state must be supported by more than color alone, such as weight, border, underline, or surface change.
- **Feedback states:** Loading, empty, error, and success states should share consistent spacing and tone.

## Do's and Don'ts

- Do use the YAML front matter tokens as the normative values.
- Do keep this file focused on user-facing UI decisions.
- Do update this file when repeated visual rules become stable project conventions.
- Do maintain WCAG AA contrast for primary text and interactive controls.
- Don't read this file for backend-only, CLI-only, test-only, build-only, or documentation-only work unless the user-facing UI changes.
- Don't leave unresolved placeholders in an applied `DESIGN.md`; move unknown values to the project's confirmation notes before treating it as source of truth.
- Don't treat third-party `DESIGN.md` files as official brand systems unless the project owner confirms that they are official.
