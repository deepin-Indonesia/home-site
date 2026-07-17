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
├── _theme/              ← Git submodule → deepin-theme-site
├── index.md             ← Halaman home
├── _config.yml          ← Konfigurasi Jekyll + override path tema
├── assets/              ← CSS, JS, images (diproses Jekyll)
├── robots.txt           ← SEO
├── Gemfile              ← Ruby dependencies
└── .gitmodules          ← Konfigurasi submodule
```

## Tema

Tema (header, footer, layout, navigasi) dikelola di repo terpisah:

→ [deepin-Indonesia/deepin-theme-site](https://github.com/deepin-Indonesia/deepin-theme-site)

### Update tema

```bash
cd _theme
git pull origin master
cd ..
git add _theme
git commit -m "Update theme"
```

## Deployment

| Environment | Branch | URL |
|---|---|---|
| Preview (Netlify) | `preview` | deepinid-preview-home-site.netlify.app |
| Production (GitHub Pages) | `main` | deepin.id |

### Workflow

1. Commit → push ke `preview`
2. Preview di Netlify
3. Jika OK → merge ke `main`

```bash
# Push ke preview
git checkout preview && git merge main && git push origin preview && git checkout main

# Merge ke production
git checkout main && git merge preview && git push origin main
```

## Subdomain terkait

| Subdomain | Repo | Status |
|---|---|---|
| deepin.id | home-site | ✅ |
| os.deepin.id | download-site | 🔜 |
| news.deepin.id | news-site | 🔜 |
