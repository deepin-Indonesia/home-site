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
│   │   ├── Analytics.astro   # Google Analytics 4 + pelacakan perilaku pengguna
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

## Analitik (Google Analytics 4)

Measurement ID: `G-2J4TLB9W7H` (satu property untuk kelima subdomain).

Pelacakan terpusat di `src/components/Analytics.astro` dan dirender sekali dari
`src/components/Layout.astro` (`<Analytics />`), jadi **semua halaman otomatis
terlacak** — tidak perlu menambah script per halaman.

Setiap event membawa parameter `site` (dari `location.host`) supaya data tiap
subdomain bisa dipisah di GA4. `site` juga dikirim sebagai *user property* agar
`page_view` ikut terpisah.

| Event | Dipicu oleh |
| --- | --- |
| `page_view` | Otomatis setiap halaman |
| `page_context` | Referrer, viewport, ukuran layar, bahasa, `utm_*` |
| `page_404` | Halaman tidak ditemukan (+ path-nya) |
| `scroll_depth` | Scroll 25/50/75/90/100% |
| `engaged_reader` | 30/60/180/600 detik benar-benar aktif |
| `visibility_change` | Tab berpindah/aktif kembali |
| `nav_click` | Klik menu di header atau drawer mobile |
| `dropdown_toggle` | Buka/tutup dropdown header |
| `menu_toggle` | Buka/tutup hamburger mobile |
| `menu_section_toggle` | Buka/tutup seksi di drawer mobile |
| `cta_click` | Tombol `.btn-primary` / `.btn-outline` / `.btn-ghost` |
| `footer_click` | Klik tautan di footer |
| `internal_site_click` | Pindah ke subdomain `deepin.id` lain |
| `outbound_click` | Keluar dari ekosistem `deepin.id` |
| `anchor_click` | Lompat ke section (`#...`) |
| `faq_toggle` | Buka accordion (`<details>`) |
| `contact_click` | Klik `mailto:` atau `tel:` |
| `copy_text` | Menyalin teks |
| `scroll_top` | Tombol kembali ke atas |
| `form_submit` | Mengirim form |
| `media_interaction` | Mulai memutar video/embed (mis. YouTube di hero) |
| `data_track` | Nama bebas dari atribut `data-track` di elemen `<a>` |

### Event kustom

Tempel `data-track` pada elemen `<a>` untuk mengirim event dengan nama sendiri:

```html
<a href="https://os.deepin.id" data-track="download_cta">Unduh deepin</a>
```

Atau panggil dari script mana pun:

```js
window.deepinTrack('os_select', { arch: 'arm64' });
```

`window.__gaReady === true` menandakan pelacakan siap (berguna untuk pengujian).

## Updating Content

### Ganti versi deepin di Hero

Edit `src/pages/index.astro` — cari badge versi dan teks headline.

### Update statistik

Edit `src/components/Stats.astro` — ubah array `stats`.

### Update penghargaan

Edit `src/components/Awards.astro` — ubah array `awards`.

### Update navigasi

Edit `src/data/site.ts` — ubah `MAIN_NAV` atau `ABOUT_NAV`.
