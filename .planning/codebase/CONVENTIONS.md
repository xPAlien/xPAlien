# Coding Conventions

**Analysis Date:** 2026-03-29

## Summary

This repository is a GitHub profile README, not an application codebase. It contains a single Markdown file (`README.md`), a banner image (`banner.png`), and two GitHub Actions workflow YAML files. There is no source code, no linting toolchain, no formatting config, and no TypeScript or JavaScript to analyze. All "conventions" are authoring patterns found in Markdown and YAML.

## Details

### File Types Present

- `README.md` — GitHub profile display page, authored in GitHub Flavored Markdown (GFM)
- `banner.png` — Static image asset
- `.github/workflows/blog-post-workflow.yml` — GitHub Actions workflow (YAML)
- `.github/workflows/snake.yml` — GitHub Actions workflow (YAML)

### Markdown Conventions (`README.md`)

**Structure:**
- Sections separated by `---` horizontal rules
- Section headers use `##` (h2) level throughout; no h3 except inside `<table>` HTML blocks
- Emoji prefixes on every major heading and list item (e.g., `## 🚀 Featured Projects`)

**Badges:**
- Shields.io badges used exclusively for all technology and social links
- Badge style: `for-the-badge` used for tech stack and featured items; `flat` used for inline project labels
- Badge format: `![Label](https://img.shields.io/badge/...)`

**Links:**
- External links wrapped in `[![badge](url)](destination)` pattern for clickable badges
- Plain markdown links used for inline text references

**HTML in Markdown:**
- `<table>`, `<tr>`, `<td>` used for the featured projects grid layout
- `<details>` / `<summary>` used for collapsible tech stack sections
- `<p align="center">` used for centered image/badge blocks

**Content conventions:**
- `<details open>` for sections open by default (Cloud & Infrastructure, Security & DevOps, Programming)
- `<details>` (closed) for secondary sections (Creative, AI Tools, Hardware)

### YAML Conventions (`.github/workflows/`)

**Formatting:**
- 2-space indentation throughout
- `name:` fields at both workflow and step level
- `uses:` references pinned to major version tags (e.g., `@v3`, `@v1`)
- Multi-line `outputs:` use YAML block scalar (`|`)

**Workflow patterns:**
- `workflow_dispatch:` present in both workflows for manual triggering
- `schedule:` with cron in `snake.yml`; commented-out cron in `blog-post-workflow.yml`
- `runs-on: ubuntu-latest` used in all jobs
- Secrets referenced via `${{ secrets.GITHUB_TOKEN }}` (standard GitHub token only)

### Linting and Formatting Tools

- None detected. No `.eslintrc*`, `.prettierrc*`, `biome.json`, `editorconfig`, or any linter configuration is present.

### Language-Specific Conventions

- Not applicable. No TypeScript, JavaScript, Python, or other source language files exist in this repository.

## Key Files

- `/c/Users/noidl/test_prod/xPalien/xPAlien/README.md` — The sole authored document; all Markdown conventions are defined here
- `/c/Users/noidl/test_prod/xPalien/xPAlien/.github/workflows/snake.yml` — Reference for YAML workflow structure
- `/c/Users/noidl/test_prod/xPalien/xPAlien/.github/workflows/blog-post-workflow.yml` — Reference for workflow with manual trigger and commented-out schedule

---

*Convention analysis: 2026-03-29*
