# InstaDwell Blog

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
