# DevBlock Technologies — Website

Corporate website for [DevBlock Technologies](https://devblocktechnologies.com.ng) — a Lagos-based software engineering company building AI-powered products, mobile apps, web platforms, and blockchain solutions.

## Tech Stack

- **HTML5** — Semantic, accessible markup
- **CSS3** — Custom properties, flexbox, grid, responsive (no framework)
- **Vanilla JS** — Smooth scrolling, navbar effects, mobile menu (~40 lines)
- **Formspree** — Contact form backend (no server needed)
- **GitHub Pages** — Free CDN-backed hosting
- **Google Fonts** — Inter typeface

## File Structure

```
website/
├── index.html          # Single-page application (all sections)
├── style.css           # Complete stylesheet
├── og-image.svg        # Open Graph social preview image
├── CNAME               # Custom domain: devblocktechnologies.com.ng
├── ARCHITECTURE.md     # Architecture documentation
└── README.md           # This file
```

## Local Development

1. Clone the repo:
   ```bash
   git clone https://github.com/DEVBLOCK-TECHNOLOGIES-LIMITED/website.git
   cd website
   ```

2. Open `index.html` in your browser — no build step required.

3. Edit HTML and CSS directly. Changes go live on push to `main`.

## Design

- **Dark theme** — `#0a0a0f` background with `#167CFA` blue accent
- **Mobile-first responsive** — Breakpoints at 1024px, 768px, 480px
- **Zero dependencies** — No npm, no bundler, no framework

## Deploy

Push to `main` branch. GitHub Pages auto-deploys to `devblocktechnologies.com.ng`.

```bash
git add -A && git commit -m "Update" && git push
```

## DNS

```
CNAME  @   devblock-technologies-limited.github.io
CNAME  www devblock-technologies-limited.github.io
```

## License

Copyright &copy; 2026 DevBlock Technologies. All rights reserved.
