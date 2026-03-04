# FilOz Home DeSite

Decentralized static website for [FilOz](https://filoz.org) — built with Hugo, deployed to GitHub Pages and pinned to the [Filecoin Onchain Cloud](https://filecoin.cloud) via [Filecoin Pin](https://www.npmjs.com/package/filecoin-pin) and served over IPFS.

**Live site:** https://desite.filoz.org

## Overview

This is a static Hugo clone of the Webflow-hosted filoz.org. It preserves the exact Webflow HTML, CSS, JS, and animations while serving all assets locally with zero external CDN dependencies. The blog section (24 posts migrated from deblog) is integrated at `/blog`.

## Pages

| Page | Route | Description |
|------|-------|-------------|
| Home | `/` | Hero, sponsors, work tabs, community, team carousel, events, fun facts |
| Events | `/events` | Upcoming events with Luma links |
| Resources | `/resources` | Links to Lotus, PDP, FEVM, and other project resources |
| Blog | `/blog` | 24 blog posts covering F3, PDP, Filecoin upgrades, and more |

## Making Updates

Common updates (team members, events, blog posts, resources) are documented in **[RUNBOOK.md](RUNBOOK.md)**. The recommended workflow is to use [Claude Code](https://docs.anthropic.com/en/docs/claude-code) to make changes — describe what you want in natural language and it will edit the correct files.

## Local Development

Requires [Hugo Extended v0.139.3](https://gohugo.io/installation/).

```bash
# Dev server (accessible on LAN)
hugo server -D --bind 0.0.0.0 --disableFastRender

# Production build
hugo --gc --minify
```

Always use `--disableFastRender` — Hugo caches templates otherwise and won't reflect changes.

## Deployment

Fully automated via GitHub Actions on push to `main`:

1. **Hugo build** with minification
2. **GitHub Pages** deploy → https://desite.filoz.org (HTTPS via Let's Encrypt)
3. **Filecoin pin** via `filecoin-pin` (mainnet, Provider ID 1)
4. **DNSLink update** at deSEC for IPFS resolution

### Required GitHub Secrets

| Secret | Purpose |
|--------|---------|
| `FILECOIN_PRIVATE_KEY` | Wallet key for Filecoin pinning |
| `DESEC_TOKEN` | deSEC API token for DNSLink TXT updates |

### DNS

| Record | Provider | Value |
|--------|----------|-------|
| NS `desite.filoz.org` | GoDaddy | `ns1.desec.io` / `ns2.desec.org` |
| A `desite.filoz.org` | deSEC | GitHub Pages IPs (185.199.108-111.153) |
| TXT `_dnslink.desite.filoz.org` | deSEC | Updated automatically by deploy workflow |

## Project Structure

```
layouts/
  _default/baseof.html      # Base template (head, scripts, conditional CSS)
  index.html                 # Homepage (team, events, all sections)
  events/list.html           # Events page
  resources/list.html        # Resources page
  blog/list.html             # Blog listing
  blog/single.html           # Blog post
  partials/                  # Nav, footer, global styles, grid animation
content/
  _index.md                  # Homepage frontmatter
  events/_index.md           # Events frontmatter
  resources/_index.md        # Resources frontmatter
  blog/_index.md             # Blog index (wf_page cascades to posts)
  blog/*.md                  # Blog posts (Markdown)
static/
  css/                       # Webflow CSS, fonts, blog styles
  js/                        # jQuery, Webflow JS, Finsweet CMS slider
  fonts/                     # IBM Plex Sans WOFF2
  images/                    # Team photos, icons, blog images, sponsors
  lottie/                    # 6 Lottie JSON animations
```

## Architecture Notes

- **Webflow fidelity:** All `data-w-id`, `data-wf-*` attributes, and Webflow class names are preserved exactly — they drive animations, responsive behavior, and layout
- **`data-wf-page`:** Each page requires a specific Webflow page ID in frontmatter (`wf_page`) for the IX2 animation engine. Without it, elements stay invisible. See `CLAUDE.md` for the full list.
- **Blog CSS scoping:** `index-custom.css` and `single-custom.css` are conditionally loaded only on `/blog` pages to avoid overriding hero styles
- **IPFS-compatible:** `baseURL: ""` with `relativeURLs: true` — all internal links use `.RelPermalink`
