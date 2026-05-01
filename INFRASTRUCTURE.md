# Craft of Change — Infrastructure Reference

*Last updated: 2026-04-05*

---

## Live URLs

- **Site:** https://craftofchange.com (also: https://craftofchange-site.pages.dev)
- **GitHub:** https://github.com/ivanrs/craftofchange-site
- **Newsletter:** https://newsletter.craftofchange.com (also: https://craftofchange.beehiiv.com)
- **Subscribe Worker:** https://coc-subscribe.i-rapinsmith.workers.dev

---

## Stack

| Layer | Service | Notes |
|-------|---------|-------|
| Site | Astro (static) + Cloudflare Pages | Auto-deploys from GitHub main branch |
| Theme | Astro Paper | Clean, dark/light, blog-ready |
| Newsletter | Beehiiv | craftofchange.beehiiv.com |
| Signup proxy | Cloudflare Worker (`coc-subscribe`) | Routes browser → Beehiiv API (avoids CORS) |
| Analytics | Cloudflare Web Analytics | Enabled in Pages dashboard, no code needed |
| Content | Markdown files in `src/data/blog/` | YAML frontmatter, deploy = git push |

---

## Credentials (all in macOS Keychain)

| Service | Keychain key | Account |
|---------|-------------|---------|
| Cloudflare API token | `cloudflare-api-token` | `openclaw` |
| Cloudflare account ID | `cloudflare-account-id` | `openclaw` |
| Beehiiv API key | `beehiiv-api-key` | `openclaw` |
| Beehiiv publication ID | `beehiiv-publication-id` | `openclaw` |
| GitHub PAT | `github-pat` | `ivanrs` |

Raw values also in `projects/craftofchange/API Keys.md` (local only, never commit).

**Cloudflare token permissions required:**
- Cloudflare Pages → Edit
- Workers Scripts → Edit

Token type: Account API Token (not user token) — created under Manage Account → Account API Tokens.

---

## Deployment

### Auto-deploy (active ✅)
The site is connected to GitHub via Cloudflare Pages Git integration.
**Every push to `main` triggers an automatic build and deploy.** No manual step needed.

Build config (set in Cloudflare Pages dashboard):
- Framework: Astro
- Build command: `npm run build`
- Output directory: `dist`
- Node version: 20 (env var NODE_VERSION=20)

### Publish a new article
```bash
# 1. Write article in Obsidian → save to projects/craftofchange/content/drafts/
# 2. When ready: copy to the site repo
cp /Users/ivan/.openclaw/workspace/projects/craftofchange/content/drafts/YYYY-MM-DD-slug.md \
   /Users/ivan/.openclaw/workspace/projects/craftofchange-site/src/data/blog/

# 3. Commit and push — Cloudflare auto-deploys
cd /Users/ivan/.openclaw/workspace/projects/craftofchange-site
git add -A && git commit -m "New article: title" && git push
```

### Manual deploy (fallback only)
```bash
bash /Users/ivan/.openclaw/workspace/scripts/deploy-pages.sh \
  /Users/ivan/.openclaw/workspace/projects/craftofchange-site \
  craftofchange-site \
  "Your commit message"
```

### Redeploy the subscribe Worker
```bash
cd projects/craftofchange-site
CLOUDFLARE_API_TOKEN=$(security find-generic-password -s "cloudflare-api-token" -a "openclaw" -w) \
CLOUDFLARE_ACCOUNT_ID=$(security find-generic-password -s "cloudflare-account-id" -a "openclaw" -w) \
  wrangler deploy worker/subscribe.js --name coc-subscribe
```

### Update Worker secret (if Beehiiv key changes)
```bash
echo "NEW_KEY" | CLOUDFLARE_API_TOKEN=... CLOUDFLARE_ACCOUNT_ID=... \
  wrangler secret put BEEHIIV_API_KEY
```

---

## Article Frontmatter

Articles in `src/data/blog/` use Astro Paper's frontmatter schema:

```yaml
---
title: "Your Article Title"
pubDatetime: 2026-04-05T12:00:00Z
description: "One sentence description for SEO and previews"
tags:
  - technology-adoption
  - history
  - ai
draft: false
---
```

**Do not** include `linkedin_version`, `series`, `issue`, or `status` fields — Astro Paper doesn't use them. Keep those in the draft file in `content/drafts/`.

---

## How Email Signup Works

```
Browser form (EmailSignup.astro)
    → POST { email } to Cloudflare Worker (coc-subscribe.i-rapinsmith.workers.dev)
        → Worker POSTs to Beehiiv API v2 with BEEHIIV_API_KEY secret
            → Beehiiv creates subscriber + sends welcome email
```

The Worker exists purely to avoid CORS — browsers can't call the Beehiiv API directly. The API key never appears in client-side code.

---

## Content Pipeline

```
Obsidian (write in markdown)
    → projects/craftofchange/content/drafts/   ← working drafts
    → projects/craftofchange/content/published/ ← archive of published pieces
    → projects/craftofchange-site/src/data/blog/ ← live on site
```

Move file from drafts → site repo → deploy. Then archive a copy in `content/published/`.

---

## To-Do (pending)

- [ ] Connect custom domain `craftofchange.com` in Cloudflare Pages settings
- [ ] Enable Cloudflare Web Analytics in Pages dashboard
- [ ] Add Beehiiv welcome email sequence
- [ ] Add LinkedIn social link to site config (`src/config.ts`)
- [ ] Delete the test@example.com subscriber from Beehiiv
- [ ] **Sources & Research section** — collapsible section at the bottom of each article listing sources used. Closed by default. Also include a line "This article draws on N entries from The Digital Ratchet" with a link — credibility signal + DR flywheel. Needs custom Astro component. Data already exists in research JSONs.
