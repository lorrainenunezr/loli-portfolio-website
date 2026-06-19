# lorrainenunez.com

Personal portfolio for **Lorraine Nuñez** — bilingual integrated marketing strategist.
A single-page, editorial-style site (about, experience, skills, contact).
Plain HTML + [Tailwind Play CDN](https://tailwindcss.com/docs/installation/play-cdn)
(no build step). Hosted free on **GitHub Pages**, auto-deployed on every push to `master`.

## Run locally

No toolchain needed. From the repo root:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Edit `index.html` / `styles.css` and reload.

## How deploy works

Pushing to `master` triggers `.github/workflows/deploy.yml`, which publishes the repo
root to GitHub Pages. No build step — the files you commit are the files that ship.

### One-time GitHub setup

1. Push this repo to GitHub.
2. **Settings → Pages → Build and deployment → Source = GitHub Actions.**
3. Push to `master`; check the **Actions** tab for a green `Deploy to GitHub Pages` run.
   The site goes live at the Pages URL shown in the run.

### Custom domain (lorrainenunez.com)

`CNAME` in the repo root binds the apex domain. At your DNS provider, point
`lorrainenunez.com` at GitHub Pages:

- **A** records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- **AAAA** records → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
- *(optional)* **CNAME** `www` → `<username>.github.io`

> Verify the current IPs against the
> [GitHub Pages apex domain docs](https://docs.github.com/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
> before applying. After DNS propagates, enable **Enforce HTTPS** in Settings → Pages.

## Upgrade path

If this becomes the permanent production site, replace the Tailwind Play CDN with a
compiled Tailwind build (or a generator like Astro/Eleventy) and add a build step to the
workflow before `upload-pages-artifact`.
