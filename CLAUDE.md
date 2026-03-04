# FilOz Home DeSite

Decentralized Hugo static clone of filoz.org. Preserves exact Webflow HTML/CSS/JS — only CDN URLs changed to local paths. Deblog (24 posts) merged as `/blog` section.

## Architecture

- **Hugo Extended v0.139.3** with `baseURL: ""` + `relativeURLs: true` for IPFS compatibility
- **Webflow CSS/JS** — self-hosted, zero external CDN dependencies
- **Fonts** — IBM Plex Sans WOFF2 (self-hosted)
- **Deployment** — filecoin-pin v0.17.0 → Filecoin mainnet → IPFS → DNSLink

## Project Structure

```
layouts/
├── _default/baseof.html    # Base template (head, scripts, CSS loading)
├── index.html              # Homepage
├── events/list.html        # Events page
├── resources/list.html     # Resources page
├── blog/list.html          # Blog listing
├── blog/single.html        # Blog post
└── partials/
    ├── nav.html            # Navigation (shared)
    ├── footer.html         # Footer (shared)
    ├── global-styles.html  # Webflow global styles
    └── grid-animation.html # Grid background animation
content/
├── _index.md               # Homepage (wf_page: 66a2ad2993901f5253eecd07)
├── events/_index.md        # Events (wf_page: 66d8ae3a2ef3a46e4340d614)
├── resources/_index.md     # Resources (wf_page: 66d8ad27d0cac9d775e009b4)
└── blog/
    ├── _index.md           # Blog index (wf_page: 66d8ad27d0cac9d775e009ad, cascades to posts)
    └── *.md                # 24 blog posts
static/
├── css/                    # webflow.css, fonts.css, common.css, blog CSS
├── js/                     # jQuery, Webflow chunks, Finsweet CMS slider
├── fonts/                  # IBM Plex Sans WOFF2
├── images/                 # All images (team, sponsors, icons, blog/)
└── lottie/                 # 6 Lottie JSON animations
```

## Critical Rules

### Never break Webflow IX2 animations
Every page needs a `wf_page` frontmatter value containing the correct Webflow page ID. The Webflow IX2 engine reads `data-wf-page` from `<html>` to find animation data in the JS bundle. Without it, animated elements stay at their initial state (opacity:0, rotateX:90deg, blur:50px) — the page looks broken/invisible.

Page IDs:
- Home: `66a2ad2993901f5253eecd07`
- Events: `66d8ae3a2ef3a46e4340d614`
- Resources: `66d8ad27d0cac9d775e009b4`
- Blog: `66d8ad27d0cac9d775e009ad` (cascaded to all posts via `_index.md`)

### Blog CSS must be scoped
`index-custom.css` and `single-custom.css` override `.section_hero .padding-section-xhuge` which breaks hero height on non-blog pages. They are conditionally loaded in `baseof.html`:
```html
{{ if eq .Section "blog" }}
<link rel="stylesheet" href="/css/index-custom.css" type="text/css">
<link rel="stylesheet" href="/css/single-custom.css" type="text/css">
{{ end }}
```
Never move these to global scope.

### Always use .RelPermalink
With empty `baseURL`, `.Permalink` generates broken absolute URLs (`//localhost:1314/...`). Always use `.RelPermalink` in templates.

### Preserve all Webflow attributes
Every `data-w-id`, `data-wf-*`, `w-*` class, and Webflow class name must be preserved exactly. These drive animations, responsive behavior, and layout.

## Development

```bash
# Dev server (accessible on LAN)
hugo server -D --bind 0.0.0.0 --disableFastRender

# Production build
hugo --gc

# Pin to Filecoin mainnet
filecoin-pin add ./public/ --mainnet --provider-id 1
```

Use `--disableFastRender` — Hugo's Fast Render mode caches templates and won't reflect template changes without a full restart.

## Filecoin Pinning (Mainnet)

- **Tool:** filecoin-pin v0.17.0 (v0.7.2 uses incompatible contracts)
- **Wallet:** `0x4714C4F258978D9a261bE4994dA5431a5e483e4d`
- **Provider ID:** 1 (ezpdpz-main)
- **Latest CID:** `bafybeidfsh36hmxhxfrnk4mhfeervalumzotlwa2iph5qyjbxm4n2biw7m` (Data Set 279)
- **Setup:** `filecoin-pin payments setup --auto --mainnet`
