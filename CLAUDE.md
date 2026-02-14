# CLAUDE.md

Guide for AI assistants working on this repository.

## Project Overview

This is a **Jekyll-based personal portfolio/resume site** hosted on GitHub Pages at [www.davidnn.se](https://www.davidnn.se). The site content is in Swedish and showcases system architect credentials and academic background.

## Repository Structure

```
/
├── _config.yml              # Jekyll configuration
├── CNAME                    # GitHub Pages custom domain (www.davidnn.se)
├── index.md                 # Main landing page content (Markdown)
├── README.md                # Project readme
├── CLAUDE.md                # This file
└── stylesheets/
    ├── styles.css           # Custom theme overrides and layout
    └── github-light.css     # Code syntax highlighting (Apache 2.0)
```

## Tech Stack

- **Static site generator:** Jekyll (built automatically by GitHub Pages)
- **Theme:** `jekyll-theme-minimal`
- **Plugins:** `jekyll-mentions`
- **Deployment:** GitHub Pages with automatic builds on push
- **Custom domain:** www.davidnn.se (via CNAME)

There is no `package.json`, `Gemfile`, or local build tooling. The site relies entirely on GitHub Pages' built-in Jekyll pipeline.

## Development Workflow

### Local Development

To run locally, install Jekyll and serve:

```bash
gem install jekyll bundler
jekyll serve
```

The site will be available at `http://localhost:4000`.

### Deployment

Push to the default branch and GitHub Pages builds and deploys automatically. No CI/CD configuration or GitHub Actions are used.

### Testing

There are no automated tests. Verify changes by running `jekyll serve` locally or reviewing the GitHub Pages deployment.

## Key Conventions

### Content

- Site content is written in **Swedish**.
- The main page (`index.md`) uses standard Markdown with Jekyll front matter handled by the theme.
- The theme provides the default layout; there are no custom `_layouts/`, `_includes/`, or `_data/` directories.

### Styling

- `stylesheets/styles.css` contains all custom CSS: typography (Noto Sans font family), two-column layout (270px sidebar + 500px content), and responsive breakpoints at 960px, 720px, and 480px.
- `stylesheets/github-light.css` provides code syntax highlighting and should not need modification.
- The site uses no JavaScript.

### Configuration

- `_config.yml` is minimal. The `title` field sets the site header. `google_analytics` and `description` are currently empty.
- `show_downloads: false` hides the GitHub download buttons from the theme.

## Guidelines for Changes

- Keep the site simple and static. Avoid adding build complexity or JavaScript unless explicitly requested.
- Preserve the Swedish language for all user-facing content.
- When adding new pages, use Markdown files at the repository root. Jekyll will process them automatically with the theme layout.
- CSS changes go in `stylesheets/styles.css`. Maintain the existing responsive breakpoints.
- Do not modify `github-light.css` unless updating the syntax highlighting scheme.
