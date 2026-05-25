# decrypt.fail

Personal site / digital garden, built with [Jekyll](https://jekyllrb.com) and served by
[GitHub Pages](https://pages.github.com). Plain Markdown in, static site out — no build
server, no JavaScript framework, free hosting.

## Structure

```
.
├── _config.yml          # site config (title, permalinks, defaults)
├── CNAME                # custom domain: decrypt.fail
├── Gemfile              # only needed for local preview
├── index.html           # homepage (digital garden link hub)
├── whoami.md            # /whoami/
├── tags.md              # /tags/  (auto-groups posts by tag, no plugin)
├── _layouts/            # default / page / post templates
├── _posts/              # blog posts (YYYY-MM-DD-title.md)
└── assets/
    ├── css/style.css    # the whole theme
    └── img/             # post images
```

## Deploying to GitHub Pages

1. Create a repo and push these files to the `main` branch.
   - For a **user site** at `https://<username>.github.io`, name the repo
     `<username>.github.io`.
   - For a **project site** plus a custom domain (your case), any repo name works.
2. In the repo: **Settings → Pages → Build and deployment → Source = "Deploy from a
   branch"**, branch `main`, folder `/ (root)`. GitHub builds the Jekyll site for you.
3. **Custom domain:** Settings → Pages → Custom domain → `decrypt.fail`. The included
   `CNAME` file already sets this. Then at your DNS provider, point the domain at GitHub:
   - Apex `decrypt.fail` → four `A` records (IPv4):
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Apex `decrypt.fail` → four `AAAA` records (IPv6):
     `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
     (GitHub recommends keeping the `A` records alongside these, given uneven IPv6 adoption.)
   - `www.decrypt.fail` → `CNAME` to `<username>.github.io`.
   - Tick **Enforce HTTPS** once the cert provisions.

Push to `main` and the site rebuilds automatically — usually live within a minute.

## Local preview (optional)

You don't need this to deploy, but to see changes before pushing:

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

## Two things to finish by hand

1. **Post images.** I couldn't pull your existing images off the live site, so
   `assets/img/` currently holds placeholders. Replace them with the originals
   (keep the same filenames):
   - `assets/img/soc-build.png` ← `https://www.decrypt.fail/img/user/decrypt/assets/xd32Qct3.png`
   - `assets/img/soc-tales-ai-war.png` ← `https://www.decrypt.fail/img/user/decrypt/assets/Pasted image 20241209212752.png`

2. **Post dates.** The `SOC Tales - AI war` date (2024-12-09) came from your image's
   timestamp. The two 2022 posts have estimated dates — change them by renaming the
   files in `_posts/` if you have the real publish dates.

## Notes on what changed from the old site

- The old site ran on Obsidian + the Digital Garden plugin on Vercel. This is a plain
  Jekyll repo instead — same content, simpler hosting.
- The `CTRL+K` search wasn't carried over (it needs a JS search index). Easy to add later
  if you want it.
- The original `/whoami/oss` page content wasn't reachable, so the "open source" link in
  `whoami.md` now points to your GitHub. Repoint it if you migrate that page.
- Old blog URLs (`/blog/<slug>/`) are preserved via the permalink setting in `_config.yml`.
