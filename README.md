# higeja.tech — blog

Minimal Astro blog. Static output, deployed via GitHub Pages on a custom domain.

## Design

- **Signature**: the QRT mark — a three-node graph (Query → Relate → Transform),
  reused as logo, hero animation, and footer mark. Ties the doctrine name
  directly to the graph-theory interest.
- **Type**: IBM Plex Serif (display) / IBM Plex Sans (body) / IBM Plex Mono
  (labels, dates, nav) — one family, three roles. Chosen for the enterprise/
  technical association (IBM Plex was built for an enterprise systems brand),
  not for being a trendy pairing.
- **Color**: cool paper background (`#f7f7f4`), near-black ink, teal accent
  for "query" (`#0f6e6e`), copper accent for "transform" (`#c2622a`).
- **Post list as ledger**: numbered rows (001, 002, ...) are justified here
  because posts genuinely are a chronological sequence — not decoration.

## Run locally

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # outputs to ./dist
npm run preview  # serve the built ./dist locally
```

## Publish your first post

1. Open `src/content/blog/qrt-doctrine.md`.
2. Replace the placeholder body with your real text.
3. Set `draft: false` in the frontmatter.
4. Adjust `pubDate` if needed.
5. Commit. The GitHub Action rebuilds and redeploys automatically on push to `main`.

New posts: add a new `.md` file under `src/content/blog/` with the same
frontmatter shape (`title`, `description`, `pubDate`, optional `draft`).

## Deploy to GitHub Pages (one-time setup)

1. Create a new **public** GitHub repo (e.g. `Qrt69/higeja-blog`). Keep this
   repo limited to blog source — no notes, scripts, or data referencing your
   private tools (Library Indexer, n8n, VPS internals).
2. Push this project to that repo's `main` branch.
3. In the repo: **Settings → Pages → Source → GitHub Actions**. The included
   workflow (`.github/workflows/deploy.yml`) handles the rest on every push.
4. In the repo: **Settings → Pages → Custom domain** → enter `higeja.tech` →
   save. GitHub will check DNS and offer to enforce HTTPS once it resolves —
   enable that.
5. At your DNS provider, on the **apex** `higeja.tech` record, add GitHub
   Pages' four A records (check
   <https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site>
   for the current IPs, they occasionally change). For `www.higeja.tech`, add
   a `CNAME` record pointing to `qrt69.github.io` (adjust to your GitHub
   username/org).
6. The `CNAME` file in `public/` is already set to `higeja.tech` — that's
   what tells GitHub Pages which custom domain to serve. Don't delete it.

This is fully separate infrastructure from your Hetzner VPS — no shared
server, no shared deploy credentials, nothing for the blog repo to leak about
the VPS side.

## Keeping this separate from your private subdomains

- `higeja.tech` (this blog) → GitHub Pages, public, static, source in a
  public repo.
- `pdf-books.higeja.tech`, `automations.higeja.tech`, etc. → your VPS via
  Caddy, separate infrastructure entirely.
- Never link from this blog to the private subdomains.
- Worth checking (separately from this blog work): does
  `pdf-books.higeja.tech` currently sit behind any auth, or is it reachable
  by anyone who guesses/finds the URL? If it's open today, that's a VPS/Caddy
  config item, unrelated to anything here — flag it if you want help locking
  it down.
- Add `Disallow: /` style rules or `noindex` meta on the private subdomains
  if you haven't already, so they don't surface in search results.
