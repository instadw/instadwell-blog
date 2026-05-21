# InstaDwell Blog

## Local development

The site is served under `/blog` (matches production at `https://instadwell.com/blog/`).

```bash
bundle exec jekyll serve
```

Open **http://localhost:4000/blog/** (not the root URL). FAQ hub: **http://localhost:4000/blog/coliving-faq/**

## Noindex a Blog Post

This project supports per-post noindex via front matter.

### How it works

- The post layout checks `page.noindex`.
- If `noindex: true` is present, the page renders:

```html
<meta name="robots" content="noindex, nofollow" />
```

- If `noindex` is not set (or false), normal `{% seo %}` tags are rendered.

### Add noindex to a post

1. Open the target file in `_posts/`.
2. Add `noindex: true` in front matter.

Example:

```yaml
---
title: "Example Post"
noindex: true
description: "..."
layout: post
---
```

### Important SEO note

- Do not block the same URL in `robots.txt` while using `noindex`.
- Search engines must be able to crawl the page to see the `noindex` tag.

### Verify after deployment

1. Open the live post URL.
2. View page source.
3. Confirm this appears in `<head>`:

```html
<meta name="robots" content="noindex, nofollow" />
```

4. Optional: submit URL in Google Search Console `Indexing -> Removals` for faster temporary suppression.

## Co-living FAQ section

Hub: `https://instadwell.com/blog/coliving-faq/`

Micro-pages: `https://instadwell.com/blog/coliving-faq/{slug}/`

### Categories (H2 on hub)

Defined in `_data/coliving_faq_categories.yml`:

- Cost & Pricing
- Safety & Security
- Lease & Move-in
- Localities — Bengaluru
- Localities — Gurgaon
- Amenities & Facilities

### Add a new FAQ micro-page

1. Create `_coliving_faq/{slug}.md` (filename = URL slug).
2. Use this front matter template:

```yaml
---
title: "The exact question (H1)"
description: "Short answer for SEO / schema"
layout: coliving-faq-post
category: "Cost & Pricing"
order: 1
author: Sanchit
date: 2026-05-19T10:00:00.000+05:30
money_page_url: "/best-co-living-spaces-in-bengaluru-and-ultimate-rent-guide-2026"
money_page_label: "Browse verified listings on InstaDwell"
related_faq: "is-coliving-cheaper-than-pg-bengaluru"
related_faq_label: "Is co-living cheaper than a PG in Bengaluru?"
---

~120 words in plain paragraphs. One CTA and one related FAQ link are rendered by the layout.
```

### Hub page

- `coliving-faq/index.md` — `hub_h1` for on-page H1, `title` for browser tab (`Co-living FAQ | InstaDwell`)

### Main blog listing

FAQ micro-pages also appear on the blog homepage with a **Co-living FAQ** badge. Existing `_posts` URLs are unchanged.

### Noindex

Set `noindex: true` in FAQ front matter; `coliving-faq-post` layout respects it.
