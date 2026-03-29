# External Integrations

**Analysis Date:** 2026-03-29

## Summary

This GitHub profile repository integrates with two external content sources (dev.to and Medium RSS feeds) and uses GitHub's own infrastructure for SVG generation and static page hosting. All integrations are implemented entirely through GitHub Actions workflows. There are no API keys or application-level secrets beyond the built-in `GITHUB_TOKEN`.

## Details

### APIs & External Services

**RSS / Blog Feed Integration:**
- **dev.to** — RSS feed at `https://dev.to/feed/xpalien`
  - Used by: `.github/workflows/blog-post-workflow.yml`
  - Mechanism: `gautamkrishnar/blog-post-workflow@v1` polls this feed and injects post links into README between `BLOG-POST-LIST` comment tags
- **Medium** — RSS feed at `https://medium.com/feed/@xpalien`
  - Used by: `.github/workflows/blog-post-workflow.yml`
  - Mechanism: same action as above, up to 5 posts fetched

**GitHub Contribution Graph:**
- **GitHub API (implicit)** — contribution data read by `Platane/snk/svg-only@v3`
  - User: `xPAlien`
  - Used by: `.github/workflows/snake.yml`
  - Outputs: `dist/github-contribution-grid-snake-dark.svg` (github-dark palette), `dist/github-contribution-grid-snake.svg` (github-light palette)

### Data Storage

**Databases:** None

**File Storage:**
- GitHub repository `output` branch — generated SVG snake animations are pushed here by `crazy-max/ghaction-github-pages@v3`
  - Source dir: `dist/`
  - Target branch: `output`

**Caching:** None

### Authentication & Identity

**Auth Provider:**
- `GITHUB_TOKEN` (built-in GitHub Actions secret) — used in `.github/workflows/snake.yml` to push SVGs to the `output` branch
- No external API keys or secrets required

### Monitoring & Observability

**Error Tracking:** None

**Logs:** GitHub Actions run logs only (accessible via GitHub UI)

### CI/CD & Deployment

**Hosting:**
- GitHub Pages (implicitly, via `output` branch serving SVG assets)
- Profile rendered by GitHub.com natively from `README.md`

**CI Pipeline:**
- GitHub Actions — two workflows:
  - `blog-post-workflow.yml` — manually triggered (`workflow_dispatch`); scheduled trigger is commented out
  - `snake.yml` — runs on schedule (`0 */12 * * *`, every 12 hours), on `push` to `main`, and on manual trigger

### Webhooks & Callbacks

**Incoming:** None

**Outgoing:**
- RSS poll to `https://dev.to/feed/xpalien`
- RSS poll to `https://medium.com/feed/@xpalien`

## Environment Configuration

**Required env vars:**
- `GITHUB_TOKEN` — automatically provided by GitHub Actions; no manual setup needed

**Secrets location:**
- No manually configured secrets. Only `secrets.GITHUB_TOKEN` (built-in).

## Key Files

- `.github/workflows/snake.yml` — snake animation generation; uses `GITHUB_TOKEN` and pushes to `output` branch
- `.github/workflows/blog-post-workflow.yml` — blog post RSS integration targeting `BLOG-POST-LIST` comment tags in `README.md`
