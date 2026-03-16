---
name: filoz-home-desite
description: Update the FilOz website (filoz.org Hugo clone). Use when the user asks to update team members, add blog posts, change events, update resources, or modify navigation/footer on the FilOz site. Also use for any content changes to desite.filoz.org.
---

# FilOz Home DeSite -- Website Content Updates

Hugo static clone of filoz.org deployed to GitHub Pages + Filecoin mainnet. All content changes are made by editing Hugo templates and Markdown files, then pushing to `main` to trigger automated deployment.

## Golden Rules

1. **Never change `wf_page` frontmatter values.** These are Webflow page IDs that drive the IX2 animation engine. Without them, elements stay invisible (opacity:0, rotateX:90deg, blur:50px).
2. **Blog CSS must stay scoped to `/blog` only.** `index-custom.css` and `single-custom.css` are conditionally loaded via `{{ if eq .Section "blog" }}` in `baseof.html`. Moving them to global scope breaks hero height on all pages.
3. **Preserve all Webflow attributes.** Every `data-w-id`, `data-wf-*`, and `w-*` class drives animations, responsive behaviour, and layout. Never rename or remove them.
4. **Always use `.RelPermalink` not `.Permalink`.** The site uses `baseURL: ""` for IPFS compatibility -- `.Permalink` generates broken absolute URLs.

## File Locations

| What | Where |
|------|-------|
| Homepage (hero, sponsors, work tabs, community, team, events, fun facts) | `layouts/index.html` |
| Events page | `layouts/events/list.html` |
| Resources page | `layouts/resources/list.html` |
| Blog listing | `layouts/blog/list.html` |
| Blog post template | `layouts/blog/single.html` |
| Navigation | `layouts/partials/nav.html` |
| Footer | `layouts/partials/footer.html` |
| Base template (head, scripts, CSS) | `layouts/_default/baseof.html` |
| Global Webflow styles | `layouts/partials/global-styles.html` |
| Grid background animation | `layouts/partials/grid-animation.html` |
| Blog posts (Markdown) | `content/blog/*.md` |
| Page frontmatter | `content/_index.md`, `content/events/_index.md`, `content/resources/_index.md`, `content/blog/_index.md` |
| Team photos | `static/images/team/` |
| Blog images | `static/images/blog/` |
| Icons and logos | `static/images/` |
| Lottie animations | `static/lottie/` |
| CSS | `static/css/` |
| JS | `static/js/` |

## Operations

### Add a Team Member

Edit `layouts/index.html` -- find the team carousel section (`section_team`). Each member is a slide block with photo, name, title, and social links.

Required: photo (PNG, min 542px wide), name, title, at least one social link.
Optional: Twitter/X, GitHub, Slack user ID, LinkedIn, Google Calendar booking link.

Steps:
1. Copy the photo to `static/images/team/`
2. Duplicate an existing team member slide block in `layouts/index.html`
3. Update the photo `src`, name, title, and social link `href` values
4. For missing social links, add `style="display:none"` to hide the icon
5. Set a unique `data-w-id` on the new slide (use a UUID)

### Remove a Team Member

Delete the entire slide block for that member from `layouts/index.html`. Remove their photo from `static/images/team/` if no longer referenced.

### Update a Team Member

Find their block in `layouts/index.html` and edit the relevant fields (name, title, photo src, social links).

### Add a Blog Post

Create a new Markdown file at `content/blog/YYYY-MM-DD_Title-Slug.md`.

Frontmatter template:
```yaml
---
title: 'Post Title Here'
description: Author Name
date: 'YYYY-MM-DDT12:00:00.000Z'
categories: []
keywords: []
slug: post-title-slug
featured_image: /images/blog/featured-image.png
---
```

Steps:
1. Copy featured image to `static/images/blog/`
2. Create the Markdown file with frontmatter and content
3. Use standard Markdown -- the `blog/single.html` template handles rendering
4. For inline images, place in `static/images/blog/` and reference as `/images/blog/filename.png`

### Update Events

Events appear in two places -- update both:
- **Homepage:** `layouts/index.html` (the `section_event` div)
- **Events page:** `layouts/events/list.html`

Each event has: title, description, date/time, organiser name + avatar, Luma URL.

### Update Resources

Edit `layouts/resources/list.html`. Each resource card has a title, description, and optional link buttons (GitHub, Google Drive, Notion, or custom "Access Here").

### Update Navigation

Edit `layouts/partials/nav.html`. The nav has: logo, 4 page links (Home, Events, Resources, Blog), hamburger menu for mobile.

### Update Footer

Edit `layouts/partials/footer.html`. Contains: logo, tagline, nav links, social icons (Twitter, GitHub, Slack, LinkedIn), copyright line.

## Development

```bash
# Dev server (LAN-accessible, required flags)
hugo server -D --bind 0.0.0.0 --disableFastRender

# Production build
hugo --gc --minify
```

Always use `--disableFastRender` -- Hugo caches templates in Fast Render mode and won't reflect template changes.

## Deployment

Push to `main` triggers `.github/workflows/deploy.yaml`:
1. Hugo build with minification
2. Deploy to GitHub Pages (https://desite.filoz.org)
3. Pin to Filecoin mainnet via filecoin-pin v0.17.0 (Provider ID 1)
4. Update DNSLink TXT record at deSEC

No manual steps required.

## Webflow Page IDs (do not change)

| Page | wf_page | Frontmatter file |
|------|---------|-----------------|
| Home | `66a2ad2993901f5253eecd07` | `content/_index.md` |
| Events | `66d8ae3a2ef3a46e4340d614` | `content/events/_index.md` |
| Resources | `66d8ad27d0cac9d775e009b4` | `content/resources/_index.md` |
| Blog | `66d8ad27d0cac9d775e009ad` | `content/blog/_index.md` (cascades to all posts) |
