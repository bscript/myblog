# bour.ch

Minimal Jekyll blog. Posts are plain Markdown files.

## Run locally

```sh
bundle install
bundle exec jekyll serve --livereload
```

Open http://localhost:4000

## Write a new post

Add a file to `_posts/` named `YYYY-MM-DD-your-slug.md`:

```md
---
layout: post
title: "Your Title"
date: 2026-11-06 10:00:00 +0000
---

Your text in Markdown.
```

The URL is the slug part of the filename: `/your-slug/`.
Put images in `assets/img/` and link them as `![alt](/assets/img/name.png)`.

## Deploy

Push to `main`. The GitHub Action in `.github/workflows/pages.yml` builds and publishes the site.
