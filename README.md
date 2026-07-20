# Home Site

Halaman utama deepin Indonesia — [deepin.id](https://deepin.id/)

Dibangun dengan [Jekyll](https://jekyllrb.com/), menggunakan tema bersama dari [deepin-theme-site](https://github.com/deepin-Indonesia/deepin-theme-site) sebagai Git submodule.

## Teknologi

| | |
|---|---|
| **Static site** | Jekyll 4.x |
| **Tema** | `_theme/` → submodule [deepin-theme-site](https://github.com/deepin-Indonesia/deepin-theme-site) |
| **Hosting** | GitHub Pages (`main`) + Netlify (`preview`) |
| **CSS** | `main.scss` (override) + `main.scss` (tema) |
| **JS** | `main.js` (tema) |
| **Icons** | Font Awesome 6 (CDN) |

## Local Development

```bash
git clone --recurse-submodules https://github.com/deepin-Indonesia/home-site.git
cd home-site
bundle install
bundle exec jekyll serve
```

Buka `http://localhost:4000`

## Struktur

```
home-site/
├── _theme/                    # Git submodule → deepin-theme-site
│   ├── _includes/             # header.html, footer.html, why-deepin.html
│   ├── _layouts/              # default.html
│   ├── _data/                 # navigation.yml
│   ├── assets/
│   │   ├── css/main.scss      # Stylesheet tema
│   │   ├── js/main.js         # Navigasi, scroll, mobile menu
│   │   └── images/            # Logo, favicon, screenshots
│   └── deepin-theme-site.gemspec
│
├── index.md                   # Halaman utama — hero, headline, intro, stats, CTA
├── 404.html                   # Custom 404 page
├── _config.yml                # Konfigurasi site (url: deepin.id, theme)
├── assets/
│   ├── css/
│   │   └── main.scss          # Override & styling spesifik home (badge, layout)
│   ├── js/
│   │   └── main.js            # Script spesifik home
│   └── images/                # deepin-id.png, zaky-nr.jpg
├── robots.txt
├── .github/workflows/         # CI/CD → GitHub Pages
├── Gemfile
└── .gitmodules
```

## Panduan Update

### Update versi deepin

Edit `index.md` — cari & replace semua angka versi:

| Lokasi | Contoh |
|--------|--------|
| `description` (front matter) | `Download deepin 25.2.0` |
| `<!-- Headline -->` | `Versi Terbaru deepin 25.2.0` |
| `h2` headline | `<h2>deepin 25.2.0 Kini Tersedia!</h2>` |
| `<strong>` di body | `<strong>deepin 25.2.0</strong>` |

### Update konten home

- **Hero**: `index.md` baris ~10-30 — tagline, tombol download, video YouTube
- **Headline**: `index.md` baris ~45-65 — badge rilis, judul, link berita
- **Apa itu deepin?**: `index.md` baris ~70-130 — teks intro, screenshot, highlight list
- **Why deepin?**: `_theme/_includes/why-deepin.html` — 6 kartu fitur
- **Filosofi Desain**: `index.md` — 5 kartu desain
- **Perjalanan deepin**: `index.md` — timeline 7 milestone
- **Statistik**: `index.md` — 6 kartu angka
- **Mengapa deepin Indonesia?**: `index.md` — subtitle + 3 fitur
- **Community Lead**: `index.md` — foto Zaky NR, link
- **CTA**: `index.md` — ajakan download + gabung komunitas

### Update screenshot

1. Commit gambar ke `_theme/assets/images/screenshots/deepin25/`
2. Pull submodule theme

### Update link download

Semua tombol download mengarah ke `https://os.deepin.id`:

```html
<a href="https://os.deepin.id" class="btn btn-primary">
  <i class="fas fa-download"></i> Download deepin
</a>
```

## Tema (Submodule)

```bash
# Cek update
cd _theme && git fetch origin && git status

# Update
cd _theme && git pull origin master

# Commit perubahan submodule di repo utama
cd .. && git add _theme && git commit -m "chore: update theme"
```

## Deployment

| Environment | Branch | URL |
|---|---|---|
| Preview | `preview` | Netlify |
| Production | `main` | [deepin.id](https://deepin.id/) |

```bash
# Push ke preview (dari main)
git push origin main:preview

# Push ke production
git push origin main
```

## Subdomain

| Subdomain | Repo | Status |
|---|---|---|
| deepin.id | **home-site** (ini) | ✅ |
| os.deepin.id | download-site | 🔜 |
| news.deepin.id | news-site | 🔜 |
