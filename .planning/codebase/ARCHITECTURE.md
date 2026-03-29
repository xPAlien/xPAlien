# ARCHITECTURE

## Summary
This is a GitHub profile README repository with no application architecture. The "system" consists of a static Markdown profile page augmented by two GitHub Actions automation workflows that generate and commit dynamic SVG assets on a schedule.

## Details

### System Overview
```
GitHub Profile Repo (xPAlien/xPAlien)
├── README.md         — Profile page rendered by GitHub
├── banner.png        — Static hero image
└── .github/
    └── workflows/
        ├── blog-post-workflow.yml   — Fetches RSS feeds → updates README
        └── snake.yml               — Generates contribution snake SVG → pushes to output branch
```

### Data Flow

**Blog Post Workflow:**
```
Cron trigger (disabled) / Manual trigger
  → actions/checkout
  → gautamkrishnar/blog-post-workflow
      → Fetches RSS from dev.to + Medium
      → Writes post links into README.md between anchor tags
  → Commits updated README.md back to main
```

**Snake Animation Workflow:**
```
Cron trigger (daily 12:00 UTC)
  → actions/checkout
  → Platane/snk/svg-only
      → Reads GitHub contribution graph
      → Generates snake SVG animation
  → crazy-max/ghaction-github-pages
      → Pushes SVG to output branch (dist/github-contribution-grid-snake*.svg)
```

### Asset Hosting
- SVG snake animation served from the `output` branch via `raw.githubusercontent.com`
- Activity graph served externally from `github-readme-activity-graph.vercel.app`
- No CDN, no caching layer, no fallback

## Key Files
- `README.md` — The entire "product"
- `.github/workflows/blog-post-workflow.yml` — RSS integration
- `.github/workflows/snake.yml` — Contribution animation
