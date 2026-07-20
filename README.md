# 🏠 deepin.id — Home Site

[![Preview](https://img.shields.io/badge/preview-Netlify-00C7B7?logo=netlify)](https://app.netlify.com/sites/deepinid-preview-home-site)
[![Production](https://img.shields.io/badge/production-deepin.id-1a6dd4)](https://deepin.id)
[![Jekyll](https://img.shields.io/badge/Jekyll-4.3-CC0000?logo=jekyll)](https://jekyllrb.com)

Landing page resmi komunitas **deepin Indonesia** — pusat informasi, download, dan komunitas deepin Linux di Indonesia. Dibangun dengan [Jekyll](https://jekyllrb.com) static site generator.

---

## 🧱 Arsitektur

```
home-site/                          # ← Repo ini
│
├── index.md                        # Halaman home (Markdown + HTML)
├── 404.html                        # Custom 404 error page
├── robots.txt                      # SEO / crawler rules
├── _config.yml                     # Konfigurasi Jekyll + site settings
│
├── _theme/                         # ← Git submodule → deepin-theme-site
│   ├── deepin-theme-site.gemspec   #    Theme gem specification
│   ├── _layouts/                   #    Template layout (default.html)
│   ├── _includes/                  #    Partial: header, footer, why-deepin
│   ├── _data/                      #    Navigation, social links
│   └── assets/                     #    CSS, JS, images, screenshots
│
├── assets/                         # Override / tambahan spesifik site ini
│   ├── css/main.scss               #    CSS tambahan (badge, layout spesifik)
│   ├── js/main.js                  #    JavaScript
│   └── images/                     #    Logo, favicon, foto
│
├── Gemfile                         # Ruby dependencies + theme gem (path: _theme)
├── Gemfile.lock                    # Locked dependency versions (gitignored)
├── .gitmodules                     # Submodule config
└── .github/workflows/pages.yml     # GitHub Actions → deploy ke Pages
```

### 🔗 Sistem Tema

Tema dikelola di repo terpisah sebagai **Jekyll theme gem**:

→ **[deepin-Indonesia/deepin-theme-site](https://github.com/deepin-Indonesia/deepin-theme-site)**

Mekanisme:
- `_theme/` adalah **git submodule** yang di-mount sebagai local gem via `Gemfile`
- `_config.yml` cukup satu baris: `theme: deepin-theme-site`
- Jekyll otomatis me-render `_layouts/`, `_includes/`, `_data/`, `assets/` dari theme
- File di `assets/` repo ini akan **menimpa** file dengan path yang sama di theme
- Semua repo deepin Indonesia (download-site, news-site, dll) pakai theme yang sama

---

## 🚀 Quick Start

### Prasyarat
- **Ruby** 3.0+
- **Bundler** (`gem install bundler`)
- **Git**

### Clone & Jalankan

```bash
# Clone beserta submodule theme
git clone --recurse-submodules https://github.com/deepin-Indonesia/home-site.git
cd home-site

# Install dependencies (termasuk theme gem dari _theme/)
bundle install

# Jalankan development server
bundle exec jekyll serve
# → Buka http://localhost:4000
```

### Update Theme

```bash
# Pull update dari repo theme
cd _theme
git pull origin master
cd ..

# Update pointer submodule di repo utama
git add _theme
git commit -m "chore: update submodule theme"
```

---

## 🔄 Workflow Deployment

```
┌─────────┐    push main:preview    ┌──────────┐
│  main   │ ───────────────────────→│ preview  │ → Netlify (staging)
│ (lokal) │                         │ (branch) │
└─────────┘                         └──────────┘
     │
     │ push origin main
     ▼
┌──────────┐
│  main    │ → GitHub Actions → GitHub Pages (production)
│ (remote) │
└──────────┘
```

| Tahap | Perintah | Trigger | URL |
|-------|----------|---------|-----|
| **Preview** | `git push origin main:preview` | Netlify auto-deploy | Netlify preview URL |
| **Production** | `git push origin main` | GitHub Actions | [deepin.id](https://deepin.id) |

> ⚠️ **Jangan push langsung ke `main` saat development.** Pakai `preview` dulu untuk testing.

---

## 🗺 Subdomain deepin Indonesia

| Subdomain | Repo | Framework | Status |
|-----------|------|-----------|--------|
| `deepin.id` | **home-site** (ini) | Jekyll | ✅ Live |
| `os.deepin.id` | download-site | Jekyll | 🔜 Coming soon |
| `news.deepin.id` | news-site | Jekyll | 🔜 Coming soon |

---

## 📄 Lisensi

Proyek ini bagian dari ekosistem open source deepin Indonesia. Kontribusi dipersilakan — buka issue atau pull request.

---

🐧 Dibangun dengan ❤️ oleh komunitas deepin Indonesia.
