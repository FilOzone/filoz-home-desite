# Runbook: Updating the FilOz DeSite

This guide covers common content updates using [Claude Code](https://docs.anthropic.com/en/docs/claude-code). All changes are made by describing what you want — Claude Code reads the project files and makes the edits for you.

## Getting Started

1. Install [Claude Code](https://docs.anthropic.com/en/docs/claude-code)
2. Clone the repo: `git clone git@github.com:FilOzone/filoz-home-desite.git`
3. Run `claude` from the project directory

Changes pushed to `main` are automatically deployed to https://desite.filoz.org and pinned to Filecoin.

## Preview Changes Locally

Before pushing, preview with Hugo:

```bash
hugo server -D --bind 0.0.0.0 --disableFastRender
```

Or ask Claude Code: *"Start the Hugo dev server"*

## Common Updates

### Add a Team Member

Team members are in `layouts/index.html` (the team carousel section).

**What to prepare:**
- Photo (PNG, minimum 542px wide, transparent background preferred)
- Full name and job title
- Social links: Twitter/X handle, GitHub username, Slack user ID, LinkedIn (optional), Google Calendar booking link (optional)

**Tell Claude Code:**

> Add a new team member: [Name], [Title]. Twitter: @handle, GitHub: username, Slack: UXXXXXXXXXX. Photo is at [path]. Add them after [existing member name].

Claude Code will:
1. Copy your photo to `static/images/team/`
2. Add the HTML block to the team carousel in `layouts/index.html`
3. Set social links and hide any that don't apply

### Remove a Team Member

> Remove [Name] from the team section.

### Update a Team Member

> Update [Name]'s title to [new title] and change their Twitter handle to @newhandle.

---

### Add a Blog Post

Blog posts are Markdown files in `content/blog/`.

**What to prepare:**
- Post title, author name, and date
- Featured image
- Post content (Markdown, or paste the text and Claude Code will format it)

**Tell Claude Code:**

> Create a new blog post titled "[Title]" by [Author Name], dated [date]. The featured image is at [path]. Here's the content: [paste content]

Claude Code will:
1. Create `content/blog/YYYY-MM-DD_Title-Slug.md` with correct frontmatter
2. Copy the featured image to `static/images/blog/`
3. Format the content as Markdown

**Frontmatter reference:**

```yaml
---
title: 'Post Title Here'
description: Author Name
date: '2026-03-04T12:00:00.000Z'
categories: []
keywords: []
slug: post-title-here
featured_image: /images/blog/featured.png
---
```

---

### Update Events

Events appear in two places: the homepage (featured events section) and the events page. Both are hardcoded HTML in templates.

- **Homepage events:** `layouts/index.html` (the `section_event` section)
- **Events page:** `layouts/events/list.html`

**What to prepare:**
- Event title, description, date/time (UTC)
- Luma event URL
- Organizer name (must be an existing team member for the avatar image)

**Tell Claude Code:**

> Update the events to show: "[Event Title]" on [date] at [time] UTC, organized by [Name], Luma link: [URL]. Remove the old events.

Or to add an event:

> Add a new event: "[Event Title]" on [date] at [time] UTC, organized by [Name], Luma link: [URL]. Add it to both the homepage and the events page.

---

### Update Resources

Resources are in `layouts/resources/list.html`. Each resource has a title, description, and optional buttons (Google Drive, GitHub, or a custom "Access Here" link).

**Tell Claude Code:**

> Add a new resource: "[Title]" — "[Description]". Link to GitHub: [URL].

Or:

> Update the PDP resource description to "[new description]" and change its link to [new URL].

Or:

> Remove the FEVM resource.

---

### Update Navigation or Footer Links

The nav and footer are shared partials:
- `layouts/partials/nav.html`
- `layouts/partials/footer.html`

> Change the Blog nav link to point to /blog instead of Medium.

> Update the footer copyright year to 2026.

---

## Important Rules

These are critical — mention them to Claude Code if it makes mistakes:

1. **Never change `wf_page` values** in frontmatter — these control Webflow animations. Without them, page elements stay invisible.

2. **Never move blog CSS to global scope** — `index-custom.css` and `single-custom.css` must only load on `/blog` pages (controlled by `{{ if eq .Section "blog" }}` in `baseof.html`).

3. **Preserve all Webflow attributes** — every `data-w-id`, `data-wf-*`, and `w-*` class is required for animations and layout.

4. **Use `--disableFastRender`** when previewing — Hugo caches templates and won't show changes otherwise.

5. **Use `.RelPermalink` not `.Permalink`** in templates — the site uses empty `baseURL` for IPFS compatibility.

## Deployment

Push to `main` and the GitHub Actions workflow handles everything:

1. Hugo build
2. Deploy to GitHub Pages (https://desite.filoz.org)
3. Pin to Filecoin mainnet
4. Update DNSLink TXT record

No manual steps required. Check the [Actions tab](https://github.com/FilOzone/filoz-home-desite/actions) for build status.
