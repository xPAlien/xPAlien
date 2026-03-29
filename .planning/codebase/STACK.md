# Technology Stack

**Analysis Date:** 2026-03-29

## Summary

This is a GitHub profile repository containing only a `README.md` and two GitHub Actions workflows. There is no application code, no package manager, no build system, and no runtime environment. The repository's sole purpose is to render a dynamic GitHub profile page using Markdown and automated GitHub Actions.

## Details

### Languages

**Primary:**
- Markdown - `README.md` — all profile content, badges, and layout

**Workflow Definitions:**
- YAML - `.github/workflows/blog-post-workflow.yml`, `.github/workflows/snake.yml`

### Runtime

**Environment:**
- No application runtime. GitHub Actions workflows run on `ubuntu-latest` (GitHub-hosted runners).

**Package Manager:**
- None. No `package.json`, `requirements.txt`, `Cargo.toml`, or any other manifest present.

### Frameworks

**Core:**
- None. No application framework.

**Build/Dev:**
- None. No build tooling.

### GitHub Actions Runners

- Runner OS: `ubuntu-latest` (used in both workflows)
- Timeout: 10 minutes (set in `snake.yml`)

### CI/CD Actions Used

| Action | Version | Purpose |
|--------|---------|---------|
| `actions/checkout` | v3 | Checks out repo in both workflows |
| `gautamkrishnar/blog-post-workflow` | v1 | Fetches blog posts from RSS feeds and updates README |
| `Platane/snk/svg-only` | v3 | Generates GitHub contribution snake SVG animation |
| `crazy-max/ghaction-github-pages` | v3 | Pushes generated SVGs to `output` branch |

### Static Assets

- `banner.png` — profile banner image committed to repository root

## Key Files

- `README.md` — entire profile content (Markdown, badges, project table, tech stack)
- `.github/workflows/snake.yml` — generates contribution snake SVG on schedule and push
- `.github/workflows/blog-post-workflow.yml` — pulls latest blog posts from RSS feeds into README
- `banner.png` — static banner image asset
