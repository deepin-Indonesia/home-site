# deepin Indonesia — Home Site

Halaman utama komunitas deepin Indonesia: **[deepin.id](https://deepin.id)**

Landing page single-page dengan 8 section: Hero, Headline, Tentang deepin, Filosofi Desain, Why Deepin, Stats, Timeline, Awards, dan CTA.

---

## Tech Stack

| Technology | Detail |
|---|---|
| **Framework** | [Astro 7](https://astro.build) |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com) + `@tailwindcss/typography` |
| **Icons** | [Font Awesome 6](https://fontawesome.com) (CDN) |
| **Sitemap** | `@astrojs/sitemap` |
| **Deploy** | [Cloudflare Pages](https://pages.cloudflare.com) |
| **Analytics** | Google Analytics 4 (`G-2J4TLB9W7H`) |
| **Runtime** | Node.js 24 |

## Project Structure

```
home-site/
├── src/
│   ├── components/
│   │   ├── Layout.astro      # Base layout (HTML head, GA4, SEO meta)
│   │   ├── Header.astro      # Sticky header + nav + mobile menu
│   │   ├── Footer.astro      # Footer dengan social links
│   │   ├── Awards.astro      # Section penghargaan deepin
│   │   ├── Stats.astro       # Section "deepin dalam Angka"
│   │   ├── Timeline.astro    # Timeline rilis deepin
│   │   └── WhyDeepin.astro   # Section keunggulan deepin
│   ├── data/
│   │   └── site.ts           # Site config, MAIN_NAV, ABOUT_NAV, social
│   ├── pages/
│   │   ├── index.astro       # Main landing page
│   │   └── 404.astro         # Custom 404
│   └── styles/
│       └── global.css        # Tailwind import + @theme colors
├── public/
│   ├── images/               # Logo, favicon, desktop screenshot
│   └── robots.txt            # Crawler rules + Sitemap directive
├── astro.config.mjs          # site: https://deepin.id, integrations
├── package.json
└── tsconfig.json
```

## Getting Started

```bash
git clone https://github.com/deepin-Indonesia/home-site.git
cd home-site
npm install
npm run dev        # → http://localhost:4321
npm run build      # Production build → dist/
```

## Deployment

Push ke branch `main` → Cloudflare Pages auto-deploy.

| Setting | Value |
|---|---|
| Build command | `npm run build` |
| Output directory | `dist` |
| Branch | `main` |

## Contributing

Semua orang bisa berkontribusi — tidak perlu jadi anggota organisasi.

### Untuk kontributor luar (via Fork)

1. **Fork** repo ini (klik tombol Fork di GitHub)
2. Clone fork kamu: `git clone https://github.com/USERNAME/home-site.git`
3. `git checkout preview && git checkout -b feat/deskripsi`
4. Edit, commit, push ke fork kamu
5. Buka **Pull Request (PR)** ke `deepin-Indonesia/home-site` → target: `preview`

### Untuk anggota organisasi (push langsung)

1. `git checkout preview && git checkout -b feat/deskripsi`
2. Commit & push
3. Buat PR ke `preview`
4. Setelah review, merge `preview` → `main`

> ⚠️ Jangan push langsung ke `main` — harus lewat PR (Pull Request).

## Updating Content

### Ganti versi deepin di Hero

Edit `src/pages/index.astro` — cari badge versi dan teks headline.

### Update statistik

Edit `src/components/Stats.astro` — ubah array `stats`.

### Update penghargaan

Edit `src/components/Awards.astro` — ubah array `awards`.

### Update navigasi

Edit `src/data/site.ts` — ubah `MAIN_NAV` atau `ABOUT_NAV`.
