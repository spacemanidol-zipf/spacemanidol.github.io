# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website for Daniel Campos (spacemanidol.com), built with Jekyll and deployed to GitHub Pages. The site serves as a professional portfolio, publication archive, and blog.

## Build & Development Commands

```bash
# Install dependencies
script/bootstrap

# Full CI build (build + validate HTML + lint + gem build)
script/cibuild

# Build site only (outputs to _site/)
bundle exec jekyll build

# Local dev server
bundle exec jekyll serve
```

The CI build runs: Jekyll build → HTMLProofer (HTML + SRI checks, no external links) → RuboCop → W3C HTML/CSS validation → gem build.

## Architecture

- **Static site generator**: Jekyll with Kramdown markdown parser
- **CSS**: Bootstrap 4.4.1 (CDN) + custom styles in `css/main.css`
- **Deployment**: GitHub Pages via CNAME (`spacemanidol.com`)
- **Config**: `_config.yml` — site name, markdown engine, permalink pattern (`/blog/:year/:month/:day/:title`)

### Layout System

- `_layouts/default.html` — Master template (Bootstrap CDN, nav, footer with social links, meta tags)
- `_layouts/post.html` — Blog post template extending default (adds title + date header)

### Content Pages

All pages use YAML front matter. Main sections:

- `index.html` — Homepage/bio
- `research/index.html` — Research themes and publications list
- `cv/index.html` — Full CV with publications, education, experience, awards
- `blog/index.html` — Blog listing; posts live in `_posts/` using `YYYY-MM-DD-Title.md` naming
- `blog/atom.xml` — RSS/Atom feed
- `principles/index.html` — Personal principles
- `about/index.html` — About page
- `wine/` — Personal fermentation tracking (yearly subdirectories)

### Style Conventions

- Link color: teal `#0B7A71`
- Container: 70% width, 60px top margin
- Nav and footer use inline `<ul>` lists
- No JavaScript beyond Bootstrap dependencies
