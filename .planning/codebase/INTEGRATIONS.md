# External Integrations

**Analysis Date:** 2026-03-29

## Summary

This GitHub profile repository integrates with two external content sources (dev.to and Medium RSS feeds). All integrations are implemented through GitHub Actions. There are no API keys or application-level secrets beyond the built-in `GITHUB_TOKEN`.

## Details

### APIs & External Services

**RSS / Blog Feed Integration:**
- **dev.to** — RSS feed at `https://dev.to/feed/xpalien`
  - Used by: `.github/workflows/blog-post-workflow.yml`
  - Mechanism: `gautamkrishnar/blog-post-workflow@v1` polls this feed and injects post links into README between `BLOG-POST-LIST` comment tags
- **Medium** — RSS feed at `https://medium.com/feed/@xpalien`
  - Used by: `.github/workflows/blog-post-workflow.yml`
  - Mechanism: same action as above, up to 5 posts fetched

### Data Storage

**Databases:** None

**File Storage:** None

**Caching:** None

### Authentication & Identity

**Auth Provider:**
- `GITHUB_TOKEN` (built-in GitHub Actions secret) — used by GitHub Actions where required
- No external API keys or secrets required

### Monitoring & Observability

**Error Tracking:** None

**Logs:** GitHub Actions run logs only (accessible via GitHub UI)

### CI/CD & Deployment

**Hosting:**
- Profile rendered by GitHub.com natively from `README.md`

**CI Pipeline:**
- GitHub Actions — one workflow:
  - `blog-post-workflow.yml` — manually triggered (`workflow_dispatch`); scheduled trigger is commented out

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

- `.github/workflows/blog-post-workflow.yml` — blog post RSS integration targeting `BLOG-POST-LIST` comment tags in `README.md`
