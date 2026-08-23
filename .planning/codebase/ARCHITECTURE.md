# ARCHITECTURE

## Summary
This is a GitHub profile README repository with no application architecture. The "system" consists of a static Markdown profile page and one GitHub Actions automation workflow.

## Details

### System Overview
```
GitHub Profile Repo (xPAlien/xPAlien)
├── README.md         — Profile page rendered by GitHub
├── banner.png        — Static hero image
└── .github/
    └── workflows/
        └── blog-post-workflow.yml   — Fetches RSS feeds → updates README
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

## Key Files
- `README.md` — The entire "product"
- `.github/workflows/blog-post-workflow.yml` — RSS integration
