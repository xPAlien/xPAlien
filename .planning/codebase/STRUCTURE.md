# STRUCTURE

## Summary
Minimal flat repository structure: 3 files at root plus one GitHub Actions workflows directory. No src/, lib/, or nested package structure exists.

## Details

### Directory Tree
```
xPAlien/
├── README.md                                      # GitHub profile page
├── banner.png                                     # Static hero banner image
└── .github/
    └── workflows/
        ├── blog-post-workflow.yml                 # RSS blog post updater
        └── snake.yml                              # Contribution snake generator
```

### File Inventory
| File | Purpose | Size |
|------|---------|------|
| `README.md` | Profile README rendered by GitHub | ~200 lines |
| `banner.png` | Static hero image embedded in README | binary |
| `.github/workflows/blog-post-workflow.yml` | GitHub Actions workflow | ~25 lines |
| `.github/workflows/snake.yml` | GitHub Actions workflow | ~30 lines |

### Branches
- `main` — Primary branch with README and workflow source
- `output` — Auto-generated branch hosting SVG animation assets (`dist/`)

### Naming Conventions
- Lowercase kebab-case for workflow files
- No source code files present, so no language-level conventions apply

## Key Files
- `README.md` — Core deliverable
- `.github/workflows/` — All automation logic
