# CONCERNS

## Summary
This GitHub profile README repository has several broken or degraded features, outdated GitHub Actions dependencies, and security gaps around unpinned third-party actions. There is no application code, tests, or CI quality gates.

## Technical Debt

- **Outdated Actions versions** — Both workflows pin `actions/checkout@v3` and `crazy-max/ghaction-github-pages@v3`; `@v4` has been available for over a year.
- **Hardcoded stale timestamp** — `_Last updated: 2025-12-28_` in README.md is already out of date and requires manual updates.

## Security Concerns

- **Unpinned third-party actions** — `gautamkrishnar/blog-post-workflow@v1` and `Platane/snk/svg-only@v3` are mutable tags. A supply-chain compromise would execute in the repo's context. Should be pinned to commit SHAs.
- **Overly broad GITHUB_TOKEN** — No `permissions:` blocks in either workflow; token inherits repository-default write access.
- **`.planning/` directory is public** — This codebase map will be committed to a public GitHub profile repo and visible to anyone.

## Broken Features

- **Blog post workflow is non-functional** — The cron schedule is commented out (`# - cron: ...`), and the README lacks the required `<!-- BLOG-POST-LIST:START -->` / `<!-- BLOG-POST-LIST:END -->` anchor comments. The workflow cannot run automatically or insert content correctly.

## Performance Concerns

- **External activity graph dependency** — The activity graph is served from `github-readme-activity-graph.vercel.app` (third-party Vercel deployment). No fallback if the service goes down or changes its API.
- **No image optimization** — `banner.png` is a raw binary asset with no compression or sizing hints.

## Incomplete Features

- Blog post integration (broken, see above)
- No dynamic "currently playing" / "recently active" widgets that were likely intended

## Missing Infrastructure

- No link validation (README contains ~20+ external URLs, none checked automatically)
- No linting or Markdown formatting checks
- No tests (not applicable to this repo type, but automation correctness is unverified)
- No Dependabot or Renovate for keeping Actions versions current
