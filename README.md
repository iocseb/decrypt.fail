# decrypt.fail

Personal site / digital garden, built with [Jekyll](https://jekyllrb.com) and served by [GitHub Pages](https://pages.github.com).

## Structure

```
.
├── _config.yml          # site config (title, permalinks, defaults)
├── CNAME                # custom domain: decrypt.fail
├── Gemfile              # only needed for local preview
├── index.html           # homepage (digital garden link hub)
├── whoami.md            # /whoami/
├── tags.md              # /tags/  (auto-groups posts by tag)
├── _layouts/            # default / page / post templates
└── _posts/              # blog posts (YYYY-MM-DD-title.md)
```

## Local preview

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```

## Adding a blog post

Drop a file in `_posts/` named `YYYY-MM-DD-some-title.md`:

```markdown
---
title: My new post
date: 2026-05-25
tags: [infosec, linux]
---

Body in Markdown…
```

It appears automatically on the homepage and the tags page, at `/blog/some-title/`.

Push to `main` and GitHub Pages rebuilds the site automatically.
