# DESIGN.md Template Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add `DESIGN.md` as an optional AOK template for target repositories.

**Architecture:** Keep `DESIGN.md` as a routed reference document, not an always-read instruction. Add bilingual templates and update the AOK catalog, selection criteria, file structure, root routing template, and document-map template.

**Tech Stack:** Markdown documentation in the existing Korean and English AOK template pack.

---

### Task 1: Add Bilingual DESIGN.md Templates

**Files:**
- Create: `ko/aok/templates/design.md`
- Create: `en/aok/templates/design.md`

- [x] **Step 1: Create the Korean template**

Add a Markdown template that defines purpose, read conditions, visual theme, colors, typography, layout, components, depth/radius/motion, responsive behavior, accessibility, do/don't rules, agent usage notes, and confirmation items.

- [x] **Step 2: Create the English template**

Add the same structure in English with matching semantics and AOK wording.

### Task 2: Register The Template In AOK Indexes

**Files:**
- Modify: `ko/agentOperatingKit.md`
- Modify: `en/agentOperatingKit.md`

- [x] **Step 1: Add `DESIGN.md` to the templates table**

Add a row for the optional UI design reference template:

`DESIGN.md` / `aok/templates/design.md`

### Task 3: Add Selection And File-Structure Guidance

**Files:**
- Modify: `ko/aok/component-selection.md`
- Modify: `en/aok/component-selection.md`
- Modify: `ko/aok/file-structure.md`
- Modify: `en/aok/file-structure.md`
- Modify: `ko/aok/application-guide.md`
- Modify: `en/aok/application-guide.md`
- Modify: `README.md`

- [x] **Step 1: Add component-selection criteria**

Document when to create or skip `<repo>/DESIGN.md`, emphasizing that it is optional and read only for UI-related work.

- [x] **Step 2: Add file-structure entry**

Document `<repo>/DESIGN.md` as the project visual design reference for UI/frontend work.

- [x] **Step 3: Add application and overview guidance**

Add `DESIGN.md` to the AOK adoption choices and README component-selection overview.

### Task 4: Add Routing To Existing Templates

**Files:**
- Modify: `ko/aok/templates/repo-agents.md`
- Modify: `en/aok/templates/repo-agents.md`
- Modify: `ko/aok/templates/document-map.md`
- Modify: `en/aok/templates/document-map.md`
- Modify: `ko/aok/templates/subdir-agents.md`
- Modify: `en/aok/templates/subdir-agents.md`

- [x] **Step 1: Update root `AGENTS.md` template routing**

Add a UI/design row to the "documents to read" table and mention `DESIGN.md` in optional extensions.

- [x] **Step 2: Update document-map template**

Add `DESIGN.md` examples to the maintenance rules only as an optional design source-of-truth document.

- [x] **Step 3: Update nested `AGENTS.md` template**

Keep area-specific design notes scoped to local differences when root `DESIGN.md` exists.

### Task 5: Verify Documentation Consistency

**Files:**
- Read all modified Markdown files.

- [x] **Step 1: Check references**

Run `rg "design.md|DESIGN.md" ko en README.md docs/superpowers` and confirm references are intentional.

- [x] **Step 2: Check git status**

Run `git status --short` and confirm only intended files plus pre-existing untracked files are present.
