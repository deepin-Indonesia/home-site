# deepin Indonesia — Home Site

Halaman utama [deepin.id](https://deepin.id) — komunitas deepin Linux Indonesia.

## Setup

```bash
git clone --recurse-submodules https://github.com/deepin-Indonesia/home-site.git
cd home-site
bundle install
bundle exec jekyll serve
```

## Struktur

```
home-site/
├── _theme/              ← Git submodule → deepin-theme-site (Jekyll theme gem)
├── index.md             ← Halaman home
├── 404.html             ← Custom 404 page
├── _config.yml          ← Konfigurasi Jekyll + theme
├── assets/              ← CSS, JS, images (override theme)
├── robots.txt           ← SEO
├── Gemfile              ← Ruby dependencies + theme gem path
└── .gitmodules          ← Konfigurasi submodule
```

## Tema

Tema (layout, includes, data, assets) dikelola sebagai **Jekyll theme gem** di repo terpisah:

→ [deepin-Indonesia/deepin-theme-site](https://github.com/deepin-Indonesia/deepin-theme-site)

### Update tema

```bash
cd _theme
git pull origin master
cd ..
git add _theme
git commit -m "chore: update submodule theme"
```

## Deployment

| Environment | Branch | Trigger | URL |
|---|---|---|---|
| Preview (Netlify) | `preview` | Push `main` → `preview` | Netlify preview URL |
| Production (GitHub Pages) | `main` | Push ke `main` via GitHub Actions | deepin.id |

### Workflow

```bash
# Push ke preview (dari main)
git push origin main:preview

# Jika OK, push ke production
git push origin main
```

## Subdomain terkait

| Subdomain | Repo | Status |
|---|---|---|
| deepin.id | home-site | ✅ |
| os.deepin.id | download-site | 🔜 |
| news.deepin.id | news-site | 🔜 |
