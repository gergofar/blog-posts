# blog-posts

Content source for the blog on **[gergofar.com](https://gergofar.com)**.

This repo holds nothing but Markdown and images — no build, no code. The website
([`gergofar.com`](https://github.com/gergofar/gergofar.com)) reads it at runtime
via ISR (`CONTENT_REPO=gergofar/blog-posts`), so **publishing a post needs no
redeploy** — push here and it appears within ~10 minutes.

## Layout

```
blog/<slug>.mdx     one file per post; the filename is the URL slug
                    (blog/my-post.mdx → gergofar.com/blog/my-post)
images/             images referenced by posts
```

## Writing a post

Create `blog/<slug>.mdx` with frontmatter, then the body in Markdown/MDX:

```mdx
---
title: "Your post title"
date: "2026-06-12"          # YYYY-MM-DD — original publish date (newest first)
updated: "2026-07-01"       # optional — last-updated date, shown when it differs
excerpt: "Shown in cards, RSS, and the page <meta>."
tag: "Applied AI"            # optional
draft: true                  # optional — hidden in production, shown in dev
---

Body. **Bold**, *italics*, `inline code`, [links](https://example.com), lists,
> blockquotes, tables, and fenced code blocks (syntax-highlighted on the site).
```

Reading time is computed automatically — don't set it.

### Code blocks

```` ```python title="evals.py" {3} ```` adds a title and highlights line 3.

### Images

Put the file in `images/` and reference it by **absolute jsDelivr URL** to this
repo, so the browser loads it straight from the CDN (off the website's host):

```md
![Alt text](https://cdn.jsdelivr.net/gh/gergofar/blog-posts@main/images/my-diagram.svg)
```

> jsDelivr caches `@main` aggressively. If an updated image doesn't show, purge
> it: `https://purge.jsdelivr.net/gh/gergofar/blog-posts@main/images/my-diagram.svg`
