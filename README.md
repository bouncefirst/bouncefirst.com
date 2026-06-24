# Bouncefirst website — static site for GitHub Pages

This folder is a complete, ready-to-host website. Every page is a single
self-contained HTML file (fonts, styles, scripts, and most images are inlined),
so there is **no build step and no dependencies** — just static files.

## Files

```
site/
├── index.html          → Home          (served at https://bouncefirst.com/)
├── portfolio.html      → Portfolio     (/portfolio.html)
├── contact.html        → Contact       (/contact.html)
├── assets/clients/     → client logos used by the Portfolio grid
├── CNAME               → custom domain (bouncefirst.com) for GitHub Pages
└── .nojekyll           → tells GitHub Pages to serve files as-is
```

The three HTML pages link to each other with relative links
(`index.html`, `portfolio.html`, `contact.html`), so the whole thing works
when opened locally or hosted anywhere.

---

## Deploy to GitHub Pages (free) — step by step

> A developer or Claude Code can run these. Replace `YOUR-USERNAME` with your
> GitHub username.

### 1. Create the repo and push these files

From inside this `site/` folder:

```bash
git init
git add -A
git commit -m "Bouncefirst website"
git branch -M main
# Create an empty repo named "bouncefirst" on github.com first, then:
git remote add origin https://github.com/YOUR-USERNAME/bouncefirst.git
git push -u origin main
```

(If you'd rather keep the repo and the `site/` folder separate, you can instead
publish from a `/docs` folder or a `gh-pages` branch — but the simplest path is
to make the repo root contain `index.html`, i.e. push the **contents** of this
folder, not the folder itself.)

### 2. Turn on GitHub Pages

In the repo on github.com: **Settings → Pages**
- **Source:** "Deploy from a branch"
- **Branch:** `main` · folder `/ (root)` → **Save**

Within a minute your site is live at `https://YOUR-USERNAME.github.io/bouncefirst/`.

### 3. Point bouncefirst.com at it (custom domain)

The included `CNAME` file already sets the domain to **bouncefirst.com**. In
**Settings → Pages → Custom domain** it should show `bouncefirst.com`. Leave
**Enforce HTTPS** checked (it becomes available after DNS resolves).

Then add these DNS records at your domain registrar (where you bought
bouncefirst.com):

**Apex domain (bouncefirst.com) — four A records:**

```
A   @   185.199.108.153
A   @   185.199.109.153
A   @   185.199.110.153
A   @   185.199.111.153
```

**Optional IPv6 (AAAA records):**

```
AAAA  @  2606:50c0:8000::153
AAAA  @  2606:50c0:8001::153
AAAA  @  2606:50c0:8002::153
AAAA  @  2606:50c0:8003::153
```

**www subdomain — one CNAME record:**

```
CNAME   www   YOUR-USERNAME.github.io.
```

DNS can take anywhere from a few minutes to 24 hours to propagate. Once it does,
`https://bouncefirst.com` serves this site over HTTPS for free.

---

## Editing the site later

These HTML files are **compiled bundles** (the original source was authored as
component files). For small text changes you can edit the copy directly inside
each `.html` file. For larger structural or design changes, it's best to update
the original design and re-export, rather than hand-editing the bundle.

## Notes

- The **Contact form was removed** by request; the Contact page shows phone
  (📞 (844) 268-6233) and email (✉️ support@bouncefirst.com) instead.
- Client logos on the Portfolio page load from `assets/clients/` — keep that
  folder next to `portfolio.html`.
- Everything else (fonts, the Bouncefirst logo, tech imagery, styles) is inlined
  into each page.
