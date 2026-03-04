# FilOz Home DeSite

Decentralized clone of filoz.org — static Hugo site deployed to Filecoin/IPFS via filecoin-pin, following the same architecture as deblog. The existing deblog project will be folded in as the `/blog` section, replacing the current Medium link.

## Source Sites

- **Main site:** https://www.filoz.org (Webflow)
- **Blog:** ~/claude/deblog/ (existing Hugo blog, currently at deblog.filoz.org)
- **Pages:** 4 (Home, Events, Resources, Blog)

## Target Architecture

- **Static generator:** Hugo Extended
- **Styling:** Webflow-exported CSS (self-hosted, zero external CDN)
- **Fonts:** IBM Plex Sans (self-hosted WOFF2)
- **JS:** jQuery + Webflow modules + Lottie player (all local)
- **Deployment:** GitHub Actions → filecoin-pin → DNSLink (same as deblog)
- **IPFS-compatible:** `baseURL: ""` + `relativeURLs: true`

## Pages

| Page | Route | Source | Status |
|------|-------|--------|--------|
| Home | `/` | filoz.org clone | Done |
| Events | `/events` | filoz.org clone | Done |
| Resources | `/resources` | filoz.org clone | Done |
| Blog | `/blog` | deblog migration (24 posts) | Done |

### Blog Integration (deblog → /blog)

The existing deblog project (23 posts, custom layouts, all images) will be merged into this site:
- **Content:** `content/blog/` (migrated from deblog's `content/posts/`)
- **Layouts:** deblog's single.html and list.html adapted to match the main site's nav/footer
- **Images:** deblog's `/static/images/` merged into this project's static assets
- **URL change:** Posts move from `deblog.filoz.org/posts/<slug>` → `filoz.org/blog/<slug>`
- **Nav link:** Footer/nav "Blog" link changes from `medium.com/@filoz` → `/blog`
- **DNSLink:** Single deployment covers entire site (home + events + resources + blog)

## Homepage Sections

1. **Nav** — Logo + hamburger menu (Home, Events, Resources, Blog)
2. **Hero** — Rotating words (secure/upgrade/expand) + 2 Lottie backgrounds
3. **Sponsors** — 3 logos
4. **Work** — 4 tabs with Lottie animations (Network security, Protocol R&D, Core implementation, Developer & Community)
5. **Community** — Slack CTA + 3 feature cards
6. **Team** — 15-person carousel with social links
7. **Events** — Latest event card + "All Events" link
8. **Fun Fact** — 3 cat photos + decorative SVGs
9. **Footer** — Logo, tagline, nav links, social icons, copyright

## Assets to Download

### Lottie Animations (6)
- hero1.json, hero2.json
- network.json, protocol.json, core.json
- filecoin-developer.json

### Images — Logos & Icons (unique SVGs)
- Group 49.svg (main logo with text)
- Group 159.svg (main logo alternate)
- Symbol 2.svg (symbol only logo)
- prime_twitter.svg, mdi_github.svg, mdi_slack.svg, mdi_linkedin.svg
- mdi_blog-outline.svg, Group 482105.svg (calendar icon)
- prime_twitter (1).svg, mdi_github (1).svg, mdi_slack (1).svg (footer variants)
- calendar.svg, book.svg
- arrow-up-right.svg

### Images — Sponsors (3 SVGs)
- imagem_2024-09-16_115626560-Photoroom 1.svg
- image 4.svg
- Lotus Pond Association.svg

### Images — Team Photos (15)
- image.png (Molly Mackinlay)
- image-1.png (Jennifer Wang)
- image-2.png (Nicola G)
- image-5.png (Irene Giacomelli)
- image-6.png (James Bluett)
- image-7.png (Kuba Sztandera)
- image-8.png (Luca Nizzardo)
- image-10.png (Orjan Roren)
- image-11.png (Rod Vagg)
- image-13.png (Zenground0)
- biglep.png (Steve Loeppky)
- Tim.jpg (Tim Fong)
- William.jpg (William Morriss)
- Raj.jpg (Red Panda)
- russell.jpg (Russell Dempsey)

### Images — Gallery/Background (3 WEBPs)
- YUNI5959_VSCO.webp
- FILDEVSUMMIT_closing-03 1.webp
- YUNI5969_VSCO.webp

### Images — Cats (3 PNGs)
- Rectangle 25.png (Ozzy)
- Group 9.png (Ozzy & Izzy)
- Group 9 (1).png (Willow)

### Images — Decorative (3)
- Yarn.png
- Lookbackcat.svg
- Butterfly.svg

### Images — Slack Screenshot (1 WEBP, multiple sizes)
- slack-screen.webp (500w, 800w, 1080w, 1600w, 1770w)

### Images — Other
- Group 49.png (tab section background)

### CSS
- filoz-preview.webflow.shared.3762fb4da.min.css

### JS
- jquery-3.5.1.min.js
- webflow.schunk.36b8fb49256177c8.js
- webflow.schunk.8208d3e53b97e3c7.js
- webflow.schunk.45325fabecaaed19.js
- webflow.schunk.a5328fc6e4f79712.js
- webflow.f8334037.3458ddeef392f4df.js
- Finsweet CMS Slider (cmsslider.js + cmscore.js)
- Google WebFont loader (webfont.js)

### Fonts
- IBM Plex Sans (weights: 300, 400, 500, 600, 700) — download WOFF2 and self-host

## Team Data (15 members)

| Name | Role | Twitter | GitHub | Slack | LinkedIn | Calendar |
|------|------|---------|--------|-------|----------|----------|
| Molly Mackinlay | CEO | momack28 | momack2 | UG80LMR6Z | — | Yes |
| Jennifer Wang | COO | _jennijuju | jennijuju | D01636JEUKH | — | Yes |
| Nicola G | Protocol Research Lead | iamnotnicola | nicola | UEP3UAA0J | — | — |
| Irene Giacomelli | Protocol Researcher | Irene_2911 | irenegia | UMJTCK007 | igiacomelli | — |
| James Bluett | Community Engineer | TippyFlits | TippyFlitsUK | U017C2R8HM0 | james-bluett-31a75a235 | Yes |
| Kuba Sztandera | Software Engineer | Kubuxu | Kubuxu | UGAD953M4 | jakub-sztandera | — |
| Luca Nizzardo | Protocol Researcher | lucaniz_ | lucaniz | — | luca-nizzardo | — |
| Orjan Roren | Technical Project Manager | OrjanRoren | rjan90 | UG8Q67065 | — | Yes |
| Rod Vagg | Software Engineer | rvagg | rvagg | UGTGV0ELQ | rvagg | — |
| Zenground0 | Software Engineer | zenground0 | ZenGround0 | UELTR25UH | — | — |
| Steve Loeppky | Engineering Manager | big_lep | BigLep | U01MVUHC342 | steveloeppky | — |
| Tim Fong | Product Lead | timfong888 | timfong888 | D08P5LPHY14 | timfong888 | — |
| William Morriss | Protocol Engineer | willmorriss4 | wjmelements | U097R16J090 | william-morriss-b0bb9464 | — |
| Red Panda | Software Engineer | — | redpanda-f | U09K19NUA4T | — | — |
| Russell Dempsey | Software Engineer | sgtpooki | sgtpooki | U02V1Q2N5SR | russelldempsey | Yes |

## Events Data

Currently shows "Filecoin Implementer Sync" — bi-weekly, hosted by Orjan Roren, links to luma.com.

## Resources Data (6 cards)

| Title | Description | Links |
|-------|-------------|-------|
| Lotus - A Filecoin Implementation in Go | Keeping Filecoin systems up-to-date and secure | GitHub |
| Filecoin Network Upgrades | Latest network improvements and upgrade plans | Drive, GitHub |
| Proof of Data Possession (PDP) | Verifiable hot data storage solutions | Notion |
| FEVM | Filecoin EVM and decentralized applications | Drive |
| Data Onramp with Filecoin Bridges | Filecoin bridges for data onboarding | Drive |
| A Guide to Retrievability on Filecoin | Filecoin retrievability story | Notion |

## Blog Migration Checklist

- [x] Copy deblog `content/posts/` → `content/blog/`
- [x] Copy deblog blog images → `static/images/blog/`
- [x] Adapt deblog single.html layout to use main site nav/footer
- [x] Adapt deblog list.html layout to use main site nav/footer
- [x] Preserve deblog's rich text CSS (single-custom.css)
- [x] Update all internal image paths in blog posts
- [x] Update nav/footer "Blog" link to `/blog`
- [x] Verify all 24 posts render correctly
- [ ] Consider redirect strategy for deblog.filoz.org → filoz.org/blog

## Reference

See `CLAUDE.md` for development notes, pinning commands, and critical rules.

- **deblog repo:** ~/claude/deblog/ (original blog, now merged into /blog section)
- **Live Webflow site:** https://www.filoz.org (current, to be replaced)
- **IPFS gateway:** https://bafybeidfsh36hmxhxfrnk4mhfeervalumzotlwa2iph5qyjbxm4n2biw7m.ipfs.dweb.link
- **Target:** Single unified site on filoz.org with /blog section
