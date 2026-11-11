<div align="center">

# deepin Indonesia — Home Site

**Halaman utama komunitas deepin Indonesia**

[deepin.id](https://deepin.id) · 🇮🇩 **Bahasa Indonesia** · [🇬🇧 English](README.en.md)

</div>

---

Landing page statis satu halaman untuk **[deepin.id](https://deepin.id)** — pintu masuk ekosistem deepin Indonesia. Dibangun dengan [Astro](https://astro.build) + [Tailwind CSS v4](https://tailwindcss.com), sepenuhnya statis, tanpa framework client-side.

## Daftar Isi

- [Tentang Proyek](#tentang-proyek)
- [Fitur](#fitur)
- [Tech Stack](#tech-stack)
- [Struktur Proyek](#struktur-proyek)
- [Memulai](#memulai)
- [Konfigurasi](#konfigurasi)
- [Mengubah Konten](#mengubah-konten)
- [Deployment](#deployment)
- [SEO, Performa & AdSense](#seo-performa--adsense)
- [Analitik](#analitik)
- [Berkontribusi](#berkontribusi)
- [Lisensi](#lisensi)

## Tentang Proyek

`home-site` adalah halaman beranda **deepin Indonesia**. Halaman ini memperkenalkan deepin sebagai sistem operasi, menyoroti rilis terbaru, menampilkan keunggulan dan pencapaian komunitas, lalu mengarahkan pengunjung untuk mengunduh deepin atau bergabung ke komunitas.

### Ekosistem deepin Indonesia

| Subdomain | Repo | Fungsi |
|---|---|---|
| [deepin.id](https://deepin.id) | `home-site` ← repo ini | Halaman utama |
| [os.deepin.id](https://os.deepin.id) | `download-site` | Download image deepin 25 |
| [news.deepin.id](https://news.deepin.id) | `news-site` | Berita, release notes, tips |
| [about.deepin.id](https://about.deepin.id) | `about-site` | Tentang komunitas & product planning |
| [donasi.deepin.id](https://donasi.deepin.id) | `donasi-site` | Donasi komunitas |

### Fitur

- **Landing page single-page** dengan navigasi anchor dan animasi ringan.
- **Hero dengan video YouTube lite embed** — player baru dimuat saat diklik (menghemat ~1 MB beban awal).
- **Banner rilis** yang menautkan ke artikel release notes terbaru.
- **Section lengkap**: Tentang deepin, Filosofi Desain, Why deepin, Statistik, Timeline, Penghargaan, dan CTA.
- **Header sticky** dengan dropdown, menu mobile, dan CTA donasi.
- **Dark hero + gradient**, sepenuhnya responsif dari 320px.
- **SEO lengkap**: Open Graph, Twitter Card, JSON-LD, canonical, hreflang, sitemap, robots.
- **Google AdSense** & **Google Analytics 4** terintegrasi lewat salah satu komponen bersama.

## Tech Stack

| Teknologi | Detail |
|---|---|
| **Framework** | [Astro 7](https://astro.build) — static site, tanpa framework client |
| **Styling** | [Tailwind CSS v4](https://tailwindcss.com) via `@tailwindcss/vite` |
| **Bahasa** | TypeScript (`strict`), alias `@/*` → `src/*` |
| **Ikon** | [Font Awesome 6](https://fontawesome.com) (CDN, dimuat non-blocking) |
| **Sitemap** | `@astrojs/sitemap` |
| **Analitik** | Google Analytics 4 — `G-2J4TLB9W7H` |
| **Iklan** | Google AdSense — `ca-pub-1345939033565649` |
| **Deploy** | [Cloudflare Pages](https://pages.cloudflare.com) |
| **Runtime** | Node.js 20+ (dikembangkan di Node 24) |

## Struktur Proyek

```
home-site/
├── src/
│   ├── components/
│   │   ├── Layout.astro      # <head>, meta SEO, AdSense, GA, skip-link, scroll-top
│   │   ├── Header.astro      # Header sticky + nav + drawer mobile
│   │   ├── Footer.astro      # Footer + social + link kebijakan privasi
│   │   ├── Analytics.astro   # GA4 + pelacakan perilaku pengguna
│   │   ├── WhyDeepin.astro   # Section keunggulan deepin
│   │   ├── Stats.astro       # Section "deepin dalam Angka"
│   │   ├── Timeline.astro    # Timeline perjalanan deepin
│   │   └── Awards.astro      # Section penghargaan
│   ├── data/
│   │   └── site.ts           # Konfigurasi situs, navigasi, sosial
│   ├── pages/
│   │   ├── index.astro       # Landing page
│   │   └── 404.astro         # Halaman 404 (noindex)
│   └── styles/
│       └── global.css        # Tailwind + palet warna deepin
├── public/
│   ├── images/               # Logo, favicon, poster video, screenshot
│   ├── ads.txt               # Otorisasi Google AdSense
│   ├── robots.txt            # Aturan crawler + sitemap
│   ├── llms.txt              # Ringkasan situs untuk LLM
│   └── site.webmanifest      # Metadata PWA
├── astro.config.mjs
├── tsconfig.json
└── package.json
```

> **Catatan:** `dist/` adalah build output dan **tidak** di-commit (ada di `.gitignore`). Cloudflare Pages membangun situs dari source.

## Memulai

### Prasyarat

- [Node.js](https://nodejs.org) 20 atau lebih baru
- npm (disertakan bersama Node.js)

### Instalasi & pengembangan

```bash
git clone https://github.com/deepin-Indonesia/home-site.git
cd home-site
npm install
npm run dev        # → http://localhost:4321
```

### Perintah

| Perintah | Kegunaan |
|---|---|
| `npm run dev` | Server pengembangan dengan hot reload |
| `npm run build` | Build produksi ke `dist/` |
| `npm run preview` | Menjalankan hasil build secara lokal |
| `npm run start` | Alias dari `npm run dev` |

## Konfigurasi

- **`astro.config.mjs`** — `site: 'https://deepin.id'`, plugin Tailwind, sitemap, dan folder aset.
- **`src/data/site.ts`** — nama situs, tagline, deskripsi, `url`, email, `ga4`, sosial, serta `MAIN_NAV` dan `ABOUT_NAV`.
- **`src/styles/global.css`** — palet `deepin-50 … deepin-950`, gaya tombol (`.btn-primary`, `.btn-outline`, `.btn-ghost`), kartu, accordion, dan animasi.

## Mengubah Konten

| Yang diubah | Lokasi |
|---|---|
| **Versi deepin di hero & banner** | `src/pages/index.astro` — badge versi, teks banner, dan link artikel |
| **Video hero (poster + ID YouTube)** | `src/pages/index.astro` — `data-video-id` dan `src` poster di `public/images/hero-video-poster.webp` |
| **Statistik** | `src/components/Stats.astro` — array `stats` |
| **Timeline** | `src/components/Timeline.astro` — array `milestones` |
| **Penghargaan** | `src/components/Awards.astro` — array `awards` |
| **Navigasi** | `src/data/site.ts` — `MAIN_NAV`, `ABOUT_NAV` |

> **Video hero** memakai pola *click-to-play*: poster lokal (`hero-video-poster.webp`) ditampilkan lebih dulu, dan `iframe` YouTube baru disuntikkan saat tombol play diklik. Untuk mengganti video, unduh thumbnail YouTube, kompres ke WebP (~1280×720), lalu simpan sebagai `public/images/hero-video-poster.webp` dan perbarui `data-video-id`.

## Deployment

Push ke branch `main` → **Cloudflare Pages** otomatis build & deploy.

| Setting | Nilai |
|---|---|
| Build command | `npm run build` |
| Output directory | `dist` |
| Production branch | `main` |

Alur kontribusi memakai branch `preview` (lihat [Berkontribusi](#berkontribusi)); merge ke `main` hanya setelah review karena `main` langsung tayang.

## SEO, Performa & AdSense

- **Meta**: title, description, `robots` (`index, follow, max-image-preview:large`), canonical, `hreflang` (`id-ID`, `x-default`).
- **Open Graph & Twitter Card**: `og:url`, `og:image` (+ `type`, `width`, `height`, `alt`), `twitter:creator`.
- **JSON-LD**: `Organization`.
- **Halaman 404**: `noindex, follow` + tanpa `hreflang`.
- **Sitemap**: `@astrojs/sitemap`; `robots.txt` menunjuk ke `sitemap-index.xml`; `llms.txt` untuk asisten AI.
- **Performa**: `preconnect`/`dns-prefetch` ke cdnjs, GTM, GA, dan AdSense; Font Awesome dimuat non-blocking; gambar LCP diberi `fetchpriority="high"`; animasi `fade-up` dihindari pada elemen LCP.
- **Aksesibilitas**: skip-link "Langsung ke konten", `focus-visible` konsisten, ikon dekoratif `aria-hidden`, `aria-label` pada tombol ikon.
- **AdSense**: script + `google-adsense-account` di `<head>`, `public/ads.txt` berisi `google.com, pub-1345939033565649, DIRECT, f08c47fec0942fa0`.
- **Kebijakan Privasi**: satu halaman terpusat di **https://deepin.id/privacy/** (repo ini). Subdomain lain menautkan ke sana dan mengarahkan `/privacy/` dengan 301.

## Analitik

Measurement ID: `G-2J4TLB9W7H` (satu property untuk kelima subdomain). Pelacakan terpusat di `src/components/Analytics.astro`, dirender sekali dari `Layout.astro`, sehingga semua halaman otomatis terlacak.

Setiap event membawa parameter `site` (dari `location.host`) agar data per subdomain bisa dipisah di GA4. Event yang dicatat antara lain: `page_view`, `page_context`, `scroll_depth`, `engaged_reader`, `nav_click`, `cta_click`, `footer_click`, `outbound_click`, `internal_site_click`, `download_click`, `faq_toggle`, `share_click`, `copy_text`, `scroll_top`, `media_interaction`, dan `data_track` (nama bebas dari atribut `data-track` pada `<a>`).

Event kustom:

```html
<a href="https://os.deepin.id" data-track="download_cta">Unduh deepin</a>
```

```js
window.deepinTrack('os_select', { arch: 'arm64' });
```

## Berkontribusi

Semua orang bisa berkontribusi — tidak perlu menjadi anggota organisasi.

1. **Fork** repo ini di GitHub.
2. Clone fork kamu, lalu buat branch dari `preview`:
   ```bash
   git checkout preview && git checkout -b feat/deskripsi
   ```
3. Commit perubahan dengan pesan yang jelas (mis. `fix(home): ...`, `feat(home): ...`).
4. Push ke fork, lalu buka **Pull Request** ke `deepin-Indonesia/home-site` dengan target branch **`preview`**.
5. Setelah review dan pengujian, perubahan di-merge `preview` → `main`.

> ⚠️ **Jangan push langsung ke `main`.** Branch `main` otomatis ter-deploy ke produksi.

## Lisensi

Dirilis di bawah [MIT License](LICENSE) © deepin Indonesia.

---

<div align="center">

Dibuat dengan ❤️ oleh komunitas [deepin Indonesia](https://deepin.id) · [Telegram](https://t.me/Linux_deepin_ID) · [GitHub](https://github.com/deepin-Indonesia)

</div>
