# Peebles — peebles.co (v1)

Static one-pager. Hero (Variant B) + scroll-one (three services). GitHub Pages-ready.

## Brand canon (locked)

- **River Teal** `#0C5B63` — primary
- **Bridge Stone** `#8F6A3A` — CTA, accents
- **Tweed Mist** `#F6F3ED` — surface
- **Ink** `#1F1B16` — body text
- **Slate** `#58524A` — muted text
- **Hairline** `#E4DED1` — dividers
- **Fonts:** Fraunces (display) + Inter (body), loaded from Google Fonts CDN

## Files

```
.
├── index.html          Hero + scroll-one
├── styles.css          All styling
├── assets/
│   ├── lockup.svg      Horizontal lockup, River Teal
│   └── mark.svg        Mark only, River Teal
└── README.md
```

No build step. Self-contained. Loads two web fonts from Google Fonts.

## Local preview

```bash
# from this folder
python3 -m http.server 8080
# then open http://localhost:8080
```

Or just open `index.html` directly in a browser.

## Deploy to GitHub Pages

### One-time setup

1. **Create a new public repo** on github.com — name it `peebles-site` (or anything; the repo name doesn't have to match the domain).
2. **Push these files** to the `main` branch:

   ```bash
   cd peebles-site
   git init
   git add .
   git commit -m "Initial: hero + scroll-one"
   git branch -M main
   git remote add origin git@github.com:<your-username>/peebles-site.git
   git push -u origin main
   ```

3. **Turn on Pages:** Repo → Settings → Pages → **Source: Deploy from a branch** → **Branch: `main` / `(root)`** → Save.
4. Wait ~1 minute. Pages will give you a temporary URL: `https://<your-username>.github.io/peebles-site/`. Visit it to confirm the site is live.

### Wire up peebles.co (custom domain)

1. **At your domain registrar** (wherever you bought `peebles.co`), add these DNS records:

   | Type  | Host | Value                                          |
   | ----- | ---- | ---------------------------------------------- |
   | A     | @    | `185.199.108.153`                              |
   | A     | @    | `185.199.109.153`                              |
   | A     | @    | `185.199.110.153`                              |
   | A     | @    | `185.199.111.153`                              |
   | CNAME | www  | `<your-username>.github.io`                    |

   These are GitHub's published Pages IPs and won't change.

2. **In the repo:** add a file named `CNAME` (no extension) in the root, containing one line:

   ```
   peebles.co
   ```

   Commit and push.

3. **Repo → Settings → Pages → Custom domain:** enter `peebles.co` → Save. Tick **Enforce HTTPS** once the certificate has provisioned (usually 5–60 minutes).
4. DNS propagation can take up to 24 hours but typically resolves within an hour. Once live, `https://peebles.co` serves the site and `https://www.peebles.co` redirects to it.

## Editing copy

- **Hero headline / supporting / CTA:** edit `index.html`, lines under `<!-- HERO -->`.
- **Three services:** edit the three `<article class="service">` blocks under `<!-- SCROLL ONE -->`.
- **Colours, type scale, layout:** edit `:root` and section blocks in `styles.css`.

Push to `main` and Pages re-deploys in ~30 seconds.

## What's intentionally not here (yet)

- No nav. Arrives with the second page.
- No contact form. The footer `mailto:` is enough for v1; add Formspree or Basin when inbound volume justifies.
- No analytics. Add Plausible or Fathom when the site is live and you want to measure.
- No research-note page. Lives at `/notes/machine-economy/` (or wherever); the hero CTA gets repointed when the note ships.
- No favicon yet. The 180px favicon PNG exists in the brand pack — drop it in `assets/` and reference from `<head>` when you're ready.

## Type scale (for handover)

| Role                 | Size                     | Font                         |
| -------------------- | ------------------------ | ---------------------------- |
| Hero headline        | clamp(40px, 5.6vw, 68px) | Fraunces 500, opsz 96        |
| Section title        | clamp(28px, 3.2vw, 40px) | Fraunces 500, opsz 60        |
| Service name         | clamp(20px, 2.0vw, 24px) | Fraunces 500, opsz 36        |
| Supporting / lede    | clamp(18px, 1.6vw, 22px) | Inter 400                    |
| Body                 | 16px                     | Inter 400                    |
| Eyebrow / small      | 14px, tracked 0.12em     | Inter 500 uppercase          |

## Accessibility

- All text ≥ 14px, body 16px, contrast checked at WCAG AA against Tweed Mist (`#F6F3ED`).
- River Teal body on Tweed Mist: 7.5:1 (AAA).
- Bridge Stone CTA on Tweed Mist: 4.6:1 (AA).
- `:focus-visible` is styled.
- `prefers-reduced-motion` is respected.

---

Built against Brand Guidelines v0.4. Hero copy from Hero Copy v0.2 (Variant B).
