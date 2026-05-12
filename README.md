# jedediahpidareese.com

Personal academic website. Plain HTML/CSS, no build step. Hosted on GitHub Pages
with a custom Namecheap domain.

## Files

- `index.html` — home
- `research.html`, `teaching.html`, `cv.html`, `contact.html` — inner pages
- `404.html` — served when a URL doesn't exist
- `assets/css/style.css` — all styling lives here. Colors, fonts, and spacing
  are CSS custom properties at the top of the file.
- `assets/img/portrait.jpg` — your headshot (you need to add this — see below)
- `assets/cv.pdf` — your current CV PDF (you need to add this — see below)
- `CNAME` — tells GitHub Pages which domain serves this site
- `.nojekyll` — tells GitHub Pages not to run Jekyll on the site

## Design notes

A few elements you'll see and might want to know about:

- **Hanko (印)**: the small vermilion seal next to your name reads 経世
  (*keisei*) — the classical phrase meaning roughly "to govern the world",
  the etymological root of 経済 (*keizai*, "economy"). It's a scholar's seal,
  not a name seal — it marks the work, not the worker. Edit it in the header
  of each `.html` file if you'd prefer different characters.
- **Hero banner (home only)**: the seigaiha (青海波, "blue sea waves") wave
  pattern is hand-drawn in SVG inside `index.html`. The faint 史 (*shi*,
  "history") character on the right is a watermark; the line below reads
  江戸・明治・大正 — Edo, Meiji, Taishō. To swap the watermark to a
  different kanji (e.g. 政 *sei*, government; 経 *kei*, economy/classic),
  edit the `<text>` element in the hero `<svg>` block in `index.html`.
- **Footer wave**: the seigaiha pattern at the foot of every page.

If you'd rather replace the SVG hero with a real Edo-period artwork:

1. Find a public-domain image you like. Good sources: <https://www.metmuseum.org/art/collection/search>
   (filter "Open Access"), Library of Congress, Smithsonian Open Access.
   Recommended search terms: "tokugawa map", "hiroshige", "edo period scroll",
   "ukiyo-e landscape". Pick something wide (3:1 to 4:1).
2. Save it as `assets/img/hero.jpg`.
3. In `index.html`, replace the entire `<div class="hero">…</div>` block with:
   ```html
   <div class="hero" aria-hidden="true">
     <img class="hero-img" src="assets/img/hero.jpg" alt="">
   </div>
   ```
4. In `assets/css/style.css`, change `.hero { aspect-ratio: 1200 / 320; … }`
   so the image fits how you want — or add `.hero-img { width: 100%; height: 100%; object-fit: cover; display: block; }`.

## Editing the site

Easiest way (no command line): edit files directly in the GitHub web UI.

1. Open the repo on GitHub.
2. Click the file you want to change.
3. Click the pencil icon (top-right of the file view).
4. Edit, scroll down, write a short commit message, click **Commit changes**.
5. Wait ~1 minute. GitHub Pages rebuilds and serves the new version.

### Common edits

- **Add a new publication:** open `research.html`, find an existing
  `<article class="entry">…</article>` block, copy it, paste below, and edit
  the title / journal / abstract / link.
- **Update the CV summary:** edit `cv.html`. Each line is a `<div class="cv-row">`
  with a date on the left and a description on the right — copy a row and
  modify it to add new entries.
- **Change a course or evaluation:** edit `teaching.html`.
- **Change colors or fonts:** open `assets/css/style.css`. The first ~25 lines
  define `--ink`, `--paper`, `--indigo`, fonts, and spacing as variables. Change
  those and the whole site updates.
- **Change the kanji watermark on the home page:** in `index.html`, find
  `<span class="kanji-mark">…</span>` and edit the characters.

## Local preview

Open any `.html` file directly in a browser — most things will work. Some
features (e.g. paths starting with `/`) only resolve correctly when the site is
served over HTTP, so for full fidelity:

```
# in this folder, with Python installed:
python -m http.server 8000
```

Then open <http://localhost:8000>.

## Deployment notes

The site lives on GitHub Pages. The `CNAME` file binds it to
`jedediahpidareese.com`. Your Namecheap DNS records point the apex
(`jedediahpidareese.com`) and `www` subdomain at GitHub's Pages servers.

If the domain ever stops resolving:
- Check Namecheap DNS hasn't changed.
- Check the GitHub Pages settings (Settings → Pages on the repo) still shows
  the custom domain configured and HTTPS enforced.
