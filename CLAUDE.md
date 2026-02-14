# CLAUDE.md

Guide for AI assistants working on this repository.

## Project Overview

This is a **Jekyll-based personal portfolio/resume site** hosted on GitHub Pages at [www.davidnn.se](https://www.davidnn.se). The site content is in Swedish and showcases system architect credentials and academic background.

## Repository Structure

```
/
├── .github/
│   └── workflows/
│       └── pages.yml        # GitHub Actions deployment workflow
├── _config.yml              # Jekyll configuration
├── CNAME                    # GitHub Pages custom domain (www.davidnn.se)
├── Gemfile                  # Ruby dependencies (github-pages gem)
├── .gitignore               # Ignores _site/, .jekyll-cache/, Gemfile.lock
├── index.md                 # Main landing page content (Markdown)
├── README.md                # Project readme
├── CLAUDE.md                # This file
└── stylesheets/
    ├── styles.css           # Custom theme overrides and layout
    └── github-light.css     # Code syntax highlighting (Apache 2.0)
```

## Tech Stack

- **Static site generator:** Jekyll (via `github-pages` gem)
- **Theme:** `jekyll-theme-minimal`
- **Plugins:** `jekyll-mentions`, `jekyll-seo-tag`, `jekyll-sitemap`
- **Deployment:** GitHub Actions (`.github/workflows/pages.yml`)
- **Custom domain:** www.davidnn.se (via CNAME)

## Development Workflow

### Local Development

Install dependencies and serve locally:

```bash
gem install bundler
bundle install
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`.

### Deployment

The site deploys automatically via GitHub Actions when changes are pushed to the `main` branch. The workflow (`.github/workflows/pages.yml`) uses the official two-job pattern:

1. **Build** — `actions/jekyll-build-pages@v1` builds the site
2. **Deploy** — `actions/deploy-pages@v4` publishes to GitHub Pages

The Pages source must be set to **GitHub Actions** in the repository settings (Settings > Pages > Build and deployment > Source).

### Testing

There are no automated tests. Verify changes by running `bundle exec jekyll serve` locally or reviewing the GitHub Pages deployment.

## Key Conventions

### Content

- Site content is written in **Swedish**.
- The main page (`index.md`) uses standard Markdown with Jekyll front matter handled by the theme.
- The theme provides the default layout; there are no custom `_layouts/`, `_includes/`, or `_data/` directories.

### Styling

- `stylesheets/styles.css` contains all custom CSS: Noto Sans (loaded via Google Fonts), two-column layout (270px sidebar + 500px content), and responsive breakpoints at 960px, 720px, and 480px.
- `stylesheets/github-light.css` provides code syntax highlighting and should not need modification.
- The site uses no JavaScript.

### Configuration

- `_config.yml` uses `plugins:` (not the deprecated `gems:`) to declare Jekyll plugins.
- The `title` field sets the site header. `description` provides SEO metadata.
- `show_downloads: false` hides the GitHub download buttons from the theme.

## Git Workflow

- Create a new feature branch for each distinct change. Never reuse a branch after its PR has been merged.
- After a PR is merged, pull the latest `main` and start a fresh branch for the next change.

## Guidelines for Changes

- Keep the site simple and static. Avoid adding build complexity or JavaScript unless explicitly requested.
- Preserve the Swedish language for all user-facing content.
- When adding new pages, use Markdown files at the repository root. Jekyll will process them automatically with the theme layout.
- CSS changes go in `stylesheets/styles.css`. Maintain the existing responsive breakpoints.
- Do not modify `github-light.css` unless updating the syntax highlighting scheme.
- Add new plugins to both `_config.yml` (under `plugins:`) and ensure they are supported by the `github-pages` gem.
