# The Craft of Change

A newsletter and publication for transformation leaders who study and improve their craft.

**Live site:** https://craftofchange.com  
**Newsletter:** https://craftofchange.beehiiv.com  
**GitHub:** https://github.com/ivanrs/craftofchange-site

---

## What This Is

The Craft of Change is written by Ivan Rapin-Smith. It covers technology-led transformation inside established organisations — grounded in documented history, written for people who are actually in the rooms making it happen.

---

## Stack

| Layer | Service |
|-------|---------|
| Site | Astro (Astro Paper theme) + Cloudflare Pages |
| Newsletter | Beehiiv (craftofchange.beehiiv.com) |
| Email signup proxy | Cloudflare Worker (`coc-subscribe`) |
| Analytics | Cloudflare Web Analytics |
| Deploy | Auto-deploy on push to `main` via Cloudflare Pages Git integration |

---

## Local Development

```bash
npm install
npm run dev        # dev server at localhost:4321
npm run build      # build to ./dist/
npm run preview    # preview build locally
```

**Note:** Uses `npm`, not `pnpm`. The `pnpm-lock.yaml` has been removed.

---

## Publishing an Article

1. Write in Obsidian → save draft to `../craftofchange/content/drafts/YYYY-MM-DD-slug.md`
2. When ready: copy to `src/data/blog/YYYY-MM-DD-slug.md`
3. Ensure frontmatter matches Astro Paper schema:

```yaml
---
title: "Your Article Title"
pubDatetime: 2026-04-05T12:00:00Z
description: "One sentence for SEO and previews"
tags:
  - tag-one
  - tag-two
draft: false
---
```

4. `git add -A && git commit -m "New article: title" && git push` — Cloudflare auto-deploys.

---

## Infrastructure

See `INFRASTRUCTURE.md` for full details on credentials, the subscribe Worker, and deploy commands.

---

## Content Pipeline

```
projects/craftofchange/content/drafts/   ← working drafts (Obsidian)
    ↓  copy when ready
src/data/blog/                           ← live articles
    ↓  git push
Cloudflare Pages                         ← auto-deploy
```

Archive published articles in `../craftofchange/content/published/` for reference.
