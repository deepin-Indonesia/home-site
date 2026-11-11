<div align="center">

# deepin Indonesia — Home Site

**The home page of the deepin Indonesia community**

[deepin.id](https://deepin.id) · 🇬🇧 **English** · [🇮🇩 Bahasa Indonesia](README.md)

</div>

---

A single-page static landing page for **[deepin.id](https://deepin.id)** — the entry point of the deepin Indonesia ecosystem. Built with [Astro](https://astro.build) + [Tailwind CSS v4](https://tailwindcss.com), fully static, no client-side framework.

## Table of Contents

- [About](#about)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Editing Content](#editing-content)
- [Deployment](#deployment)
- [SEO, Performance & AdSense](#seo-performance--adsense)
- [Analytics](#analytics)
- [Contributing](#contributing)
- [License](#license)

## About

`home-site` is the **deepin Indonesia** home page. It introduces deepin as an operating system, highlights the latest release, showcases the community's strengths and achievements, and guides visitors to download deepin or join the community.

### The deepin Indonesia ecosystem

| Subdomain | Repo | Purpose |
|---|---|---|
| [deepin.id](https://deepin.id) | `home-site` ← this repo | Home page |
| [os.deepin.id](https://os.deepin.id) | `download-site` | deepin 25 image downloads |
| [news.deepin.id](https://news.deepin.id) | `news-site` | News, release notes, tips |
| [about.deepin.id](https://about.deepin.id) | `about-site` | Community & product planning |
| [donasi.deepin.id](https://donasi.deepin.id) | `donasi-site` | Community donations |

### Features

- **Single-page landing** with anchor navigation and light animations.
- **Hero with a lite YouTube embed** — the player loads only on click (saves ~1 MB on initial load).
- **Release banner** linking to the latest release-notes article.
- **Full sections**: About deepin, Design Philosophy, Why deepin, Stats, Timeline, Awards, and CTA.
- **Sticky header** with dropdowns, mobile drawer, and donation CTA.
- **Dark hero + gradients**, fully responsive from 320px.
- **Complete SEO**: Open Graph, Twitter Card, JSON-LD, canonical, hreflang, sitemap, robots.
- **Google AdSense** & **Google Analytics 4** integrated via shared components.

## Tech Stack

| Technology | Detail |
|---|---|
| **Framework** | [Astro 7](https://astro.build) — static site, no client framework |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com) via `@tailwindcss/vite` |
| **Language** | TypeScript (`strict`), alias `@/*` → `src/*` |
| **Icons** | [Font Awesome 6](https://fontawesome.com) (CDN, non-blocking) |
| **Sitemap** | `@astrojs/sitemap` |
| **Analytics** | Google Analytics 4 — `G-2J4TLB9W7H` |
| **Ads** | Google AdSense — `ca-pub-1345939033565649` |
| **Deploy** | [Cloudflare Pages](https://pages.cloudflare.com) |
| **Runtime** | Node.js 20+ (developed on Node 24) |

## Project Structure

```
home-site/
├── src/
│   ├── components/
│   │   ├── Layout.astro      # <head>, SEO meta, AdSense, GA, skip-link, scroll-top
│   │   ├── Header.astro      # Sticky header + nav + mobile drawer
│   │   ├── Footer.astro      # Footer + social + privacy policy link
│   │   ├── Analytics.astro   # GA4 + user behavior tracking
│   │   ├── WhyDeepin.astro   # deepin advantages section
│   │   ├── Stats.astro       # "deepin in numbers" section
│   │   ├── Timeline.astro    # deepin journey timeline
│   │   └── Awards.astro      # Awards section
│   ├── data/
│   │   └── site.ts           # Site config, navigation, social
│   ├── pages/
│   │   ├── index.astro       # Landing page
│   │   └── 404.astro         # 404 page (noindex)
│   └── styles/
│       └── global.css        # Tailwind + deepin color palette
├── public/
│   ├── images/               # Logo, favicon, video poster, screenshot
│   ├── ads.txt               # Google AdSense authorization
│   ├── robots.txt            # Crawler rules + sitemap
│   ├── llms.txt              # Site summary for LLMs
│   └── site.webmanifest      # PWA metadata
├── astro.config.mjs
├── tsconfig.json
└── package.json
```

> **Note:** `dist/` is build output and is **not** committed (`.gitignore`). Cloudflare Pages builds the site from source.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org) 20 or newer
- npm (bundled with Node.js)

### Install & develop

```bash
git clone https://github.com/deepin-Indonesia/home-site.git
cd home-site
npm install
npm run dev        # → http://localhost:4321
```

### Commands

| Command | Purpose |
|---|---|
| `npm run dev` | Dev server with hot reload |
| `npm run build` | Production build to `dist/` |
| `npm run preview` | Preview the build locally |
| `npm run start` | Alias for `npm run dev` |

## Configuration

- **`astro.config.mjs`** — `site: 'https://deepin.id'`, Tailwind plugin, sitemap, asset folder.
- **`src/data/site.ts`** — site name, tagline, description, `url`, email, `ga4`, social, plus `MAIN_NAV` and `ABOUT_NAV`.
- **`src/styles/global.css`** — `deepin-50 … deepin-950` palette, button styles (`.btn-primary`, `.btn-outline`, `.btn-ghost`), cards, accordion, animations.

## Editing Content

| What to change | Where |
|---|---|
| **deepin version in hero & banner** | `src/pages/index.astro` — version badge, banner text, article link |
| **Hero video (poster + YouTube ID)** | `src/pages/index.astro` — `data-video-id` and poster `src` in `public/images/hero-video-poster.webp` |
| **Stats** | `src/components/Stats.astro` — `stats` array |
| **Timeline** | `src/components/Timeline.astro` — `milestones` array |
| **Awards** | `src/components/Awards.astro` — `awards` array |
| **Navigation** | `src/data/site.ts` — `MAIN_NAV`, `ABOUT_NAV` |

> **Hero video** uses a *click-to-play* pattern: a local poster (`hero-video-poster.webp`) is shown first, and the YouTube `iframe` is injected only when the play button is clicked. To change the video, download the YouTube thumbnail, compress it to WebP (~1280×720), save as `public/images/hero-video-poster.webp`, and update `data-video-id`.

## Deployment

Push to the `main` branch → **Cloudflare Pages** builds and deploys automatically.

| Setting | Value |
|---|---|
| Build command | `npm run build` |
| Output directory | `dist` |
| Production branch | `main` |

Contributions use the `preview` branch (see [Contributing](#contributing)); merge to `main` only after review, because `main` goes live immediately.

## SEO, Performance & AdSense

- **Meta**: title, description, `robots` (`index, follow, max-image-preview:large`), canonical, `hreflang` (`id-ID`, `x-default`).
- **Open Graph & Twitter Card**: `og:url`, `og:image` (+ `type`, `width`, `height`, `alt`), `twitter:creator`.
- **JSON-LD**: `Organization`.
- **404 page**: `noindex, follow` without `hreflang`.
- **Sitemap**: `@astrojs/sitemap`; `robots.txt` points to `sitemap-index.xml`; `llms.txt` for AI assistants.
- **Performance**: `preconnect`/`dns-prefetch` to cdnjs, GTM, GA, and AdSense; Font Awesome is non-blocking; the LCP image uses `fetchpriority="high"`; `fade-up` animation is avoided on LCP elements.
- **Accessibility**: "Skip to content" link, consistent `focus-visible`, decorative icons marked `aria-hidden`, `aria-label` on icon buttons.
- **AdSense**: script + `google-adsense-account` in `<head>`, `public/ads.txt` with `google.com, pub-1345939033565649, DIRECT, f08c47fec0942fa0`.
- **Privacy Policy**: a single centralized page at **https://deepin.id/privacy/** (this repo). Other subdomains link there and 301-redirect `/privacy/`.

## Analytics

Measurement ID: `G-2J4TLB9W7H` (one property for all five subdomains). Tracking is centralized in `src/components/Analytics.astro` and rendered once from `Layout.astro`, so every page is tracked automatically.

Every event carries a `site` parameter (from `location.host`) so data can be split per subdomain in GA4. Tracked events include: `page_view`, `page_context`, `scroll_depth`, `engaged_reader`, `nav_click`, `cta_click`, `footer_click`, `outbound_click`, `internal_site_click`, `download_click`, `faq_toggle`, `share_click`, `copy_text`, `scroll_top`, `media_interaction`, and `data_track` (custom name from a `data-track` attribute on `<a>`).

Custom events:

```html
<a href="https://os.deepin.id" data-track="download_cta">Download deepin</a>
```

```js
window.deepinTrack('os_select', { arch: 'arm64' });
```

## Contributing

Anyone can contribute — no organization membership required.

1. **Fork** this repo on GitHub.
2. Clone your fork, then branch from `preview`:
   ```bash
   git checkout preview && git checkout -b feat/description
   ```
3. Commit with a clear message (e.g., `fix(home): ...`, `feat(home): ...`).
4. Push to your fork, then open a **Pull Request** against `deepin-Indonesia/home-site` targeting the **`preview`** branch.
5. After review and testing, changes are merged `preview` → `main`.

> ⚠️ **Do not push directly to `main`.** The `main` branch deploys to production automatically.

## License

Released under the [MIT License](LICENSE) © deepin Indonesia.

---

<div align="center">

Made with ❤️ by the [deepin Indonesia](https://deepin.id) community · [Telegram](https://t.me/Linux_deepin_ID) · [GitHub](https://github.com/deepin-Indonesia)

</div>
