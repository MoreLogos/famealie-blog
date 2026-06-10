# The famealie Blog

Marketing/content blog for famealie — separate from the app. Built with
[Astro](https://astro.build), deployed on Vercel.

## Develop

```bash
npm install      # first time
npm run dev      # http://localhost:4321
npm run build    # production build into dist/
```

## Write a post

Add a Markdown/MDX file in `src/content/blog/`. Front-matter:

```md
---
title: 'Your title'
description: 'One-line summary used for SEO + social cards'
pubDate: 'Jun 10 2026'
# heroImage: '../../assets/your-image.jpg'   # optional
---
Body in Markdown…
```

Every post automatically gets the "Try famealie" CTA and the comments section.

## Deploy to Vercel

1. `git init && git add -A && git commit -m "initial blog"`, then push to a new
   GitHub repo (e.g. `famealie-blog`).
2. Vercel → **Add New → Project** → import the repo (auto-detects Astro) → Deploy.
3. **Settings → Domains** → add `blog.famealie.io`, then add the CNAME Vercel
   shows in your DNS.

## Configure

- **Analytics:** set `PUBLIC_POSTHOG_KEY` (and `PUBLIC_POSTHOG_HOST`) in Vercel
  env vars to send blog pageviews + `blog_cta_clicked` events to your existing
  PostHog project. See `.env.example`.
- **Comments (Giscus):** follow the setup notes in
  `src/components/Comments.astro` (enable Discussions on the repo, install the
  Giscus app, paste the four ids). Until configured, the comments box is hidden.
- **Branding:** title/description and the app URL live in `src/consts.ts`.

## Project layout

- `src/content/blog/` — posts (Markdown/MDX)
- `src/components/AppCta.astro` — "Try famealie" call-to-action
- `src/components/Comments.astro` — Giscus comments
- `src/components/BaseHead.astro` — SEO meta, OG tags, PostHog snippet
- `src/consts.ts` — site title/description + `APP_URL`
- `astro.config.mjs` — `site` URL (set to the production domain)
