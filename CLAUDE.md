# CLAUDE.md

## Project Overview

**MrZhang.me** is a minimalist personal blog/static site hosted on GitHub Pages. It is a Jekyll-based project that currently serves as a redirect page (the blog content has been retired). The site redirects visitors to a GitHub issue and serves a custom 404 page.

- **Domain:** mrzhang.me (via CNAME)
- **Hosting:** GitHub Pages, deployed from the `gh-pages` branch
- **Author:** wǒ_is神仙

---

## Repository Structure

```
MrZhang.me/
├── _config.yml          # Jekyll site configuration
├── _layouts/
│   └── default.html     # Single layout template (all pages use this)
├── _sass/
│   └── _highlight.scss  # GitHub-style syntax highlighting styles
├── fonts/
│   ├── fontello/        # Icon font (single "time" icon, prefix: iconfont-)
│   │   ├── config.json
│   │   ├── fontello.ttf
│   │   └── fontello.woff
│   └── typewriter/      # Custom typewriter font
│       ├── typewriter.ttf
│       └── typewriter.woff
├── 404.html             # Custom 404 page (uses default layout)
├── CNAME                # GitHub Pages custom domain: mrzhang.me
└── favicon.ico
```

---

## Technology Stack

| Layer | Technology |
|-------|-----------|
| Static site generator | Jekyll |
| Markdown parser | Redcarpet |
| CSS preprocessor | SASS/SCSS |
| Hosting | GitHub Pages |
| Fonts | Fontello (icons) + custom Typewriter font |

No `package.json`, no Node.js tooling, no build scripts — this is a pure Jekyll project.

---

## Jekyll Configuration (`_config.yml`)

| Setting | Value |
|---------|-------|
| `author` | wǒ_is神仙 |
| `name` | MrZhang.me |
| `url` | http://mrzhang.me |
| `permalink` | `blog/:title.html` |
| `paginate` | 5 posts per page |
| `paginate_path` | `/page/:num` |
| `excerpt_separator` | `<!-- 么么哒 -->` |
| `markdown` | redcarpet |
| `timezone` | Asia/Shanghai |
| `safe` | true (required for GitHub Pages) |
| `exclude` | Gemfile, Gemfile.lock |

---

## Development Workflow

### Local Development

Jekyll is required locally. No Gemfile is present in the working tree (it is excluded from builds), so install Jekyll manually:

```bash
gem install jekyll
jekyll serve
```

The site will be available at `http://localhost:4000`.

### Deployment

Deployment is automatic via GitHub Pages. Push to the `gh-pages` branch to deploy to production.

```bash
git push origin gh-pages
```

### Branch Strategy

- `gh-pages` — production branch, auto-deployed by GitHub Pages
- Feature/documentation branches follow the pattern `claude/<description>-<id>`

---

## Key Conventions

### Layout System

There is only one layout: `default.html`. All pages must specify it in front matter:

```yaml
---
layout: default
---
```

The layout includes a `<meta http-equiv="refresh">` that redirects visitors to `https://github.com/jsw0528/MrZhang.me/issues/3` after 2 seconds. This is intentional — the blog has been retired and this is the "goodbye" redirect.

### Content

- The site is bilingual (Chinese and English).
- The 404 page uses a classical Chinese Buddhist poem (《菩提偈》by Huineng) with a humorous English "translation" of the last line.
- Post excerpt separator is `<!-- 么么哒 -->` (Chinese internet slang for "kisses").

### Fonts

- Fonts are delivered in both TTF and WOFF formats for broad browser compatibility.
- The icon font uses the CSS class prefix `iconfont-`.
- Only one icon is configured in Fontello: `time` (Unicode U+E800).

### SCSS

- Syntax highlighting styles in `_sass/_highlight.scss` follow GitHub's color conventions.
- SASS partials use the underscore prefix naming convention (`_highlight.scss`).

---

## What NOT to Do

- Do not add a build pipeline (Webpack, Vite, etc.) — this project intentionally has no JS toolchain.
- Do not set `safe: false` — GitHub Pages requires safe mode.
- Do not push directly to `gh-pages` for documentation or non-production changes.
- Do not remove the meta-refresh redirect in `default.html` — it is the intended behavior of the site.
- Do not add blog posts — the blog has been retired ("Goodbye" commit `8d4db2f`).

---

## Current State

The site is effectively in a **retired/archived state**. The main layout redirects to a GitHub issue explaining the shutdown. The only active content is the 404 page. Future changes to this repo are likely limited to documentation and minor configuration updates.
