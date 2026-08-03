# 7Talents Website

Marketing site for [7talents.io](https://7talents.io) — fractional CIO and systems assessment services for nonprofits.

Plain static HTML/CSS. No build step, no framework, no dependencies.

## Structure

```
.
├── index.html      # All page content and section markup
├── style.css        # All styling (brand tokens, layout, responsive rules)
├── assets/           # Logos and background textures
└── README.md
```

## Local preview

No build tools required. Either:

- Open `index.html` directly in a browser, or
- Run a local server from the project root (recommended, avoids asset-path quirks):
  ```bash
  python3 -m http.server 8000
  ```
  then visit `http://localhost:8000`

## Making edits

- **Copy/content** — edit directly in `index.html`. Sections are commented (`<!-- ===== HERO ===== -->`, etc.) for easy navigation.
- **Colors, type, spacing** — edit `style.css`. Brand color and font variables are declared at the top of the file under `:root`.
- **Images** — add new files to `assets/` and reference them as `assets/filename.png`.
- **"Book a Discovery Call" links** — all point to `https://calendly.com/7talents/intro`. Update that URL in `index.html` if it ever changes (search for `calendly.com`).

## Deployment

This site deploys automatically via **Cloudflare Pages**, connected to this GitHub repository. Any push to `main` triggers a new deploy — no build command needed (leave the Cloudflare Pages build settings blank / "None").

See `DEPLOY.md` for the one-time setup steps.

## Brand assets

Only the logo and texture files actually used on the site are included in `assets/`:
- `7Talents-Logo-Secondary-2-Color.png` — header logo
- `7Talents-Logo-Primary-1-Color.png` — footer logo (white + accent blue, for dark backgrounds)
- `7T-Symbol.png` — hero graphic
- `Halftone_2.png`, `Halftone_3.png` — section background textures

The full 7Talents brand guide (colors, typography, logo variants, misuse rules) lives outside this repo — reference it directly if you need a brand asset not included here.
