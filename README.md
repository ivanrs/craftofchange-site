# craftofchange.com — Astro Site

The Astro repo that deploys to Cloudflare Pages. Part of the [Craft of Change](../README.md) project.

**Live site:** https://craftofchange.com
**Newsletter:** https://craftofchange.beehiiv.com
**GitHub:** https://github.com/ivanrs/craftofchange-site

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

**Note:** Uses `npm`, not `pnpm`.

---

## Publishing

Articles are written directly to `src/data/blog/<slug>.md` with `draft: true` by the `coc-article` or `ai-at-work-assembler` skills (in `~/.openclaw/workspace/skills/`). When Ivan approves, flip `draft: true` → `draft: false` and push.

```bash
git add -A && git commit -m "Publish: <article title>" && git push
```

Cloudflare auto-deploys.

**Frontmatter (Astro Paper schema):**
```yaml
---
title: "Article Title"
pubDatetime: 2026-MM-DDT12:00:00Z
description: "One sentence for SEO and previews"
type: ai-at-work        # or omit for long-form
tags:
  - tag-one
  - tag-two
draft: false
---
```

**Post-publish corrections:** edit the site file directly, commit with descriptive message. Git history is the audit trail. If a correction changes a verified fact, update the corresponding `fact-check.md` in the originating brief or AI at Work folder.

For the full publish workflow, see the relevant SKILL.md (`coc-article` or `ai-at-work-assembler`).

---

## Infrastructure

See `INFRASTRUCTURE.md` for credentials, the subscribe Worker, and deploy commands.
