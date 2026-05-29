# DevBlock Technologies Website — Architecture

## Overview

The DevBlock Technologies corporate website is a **static single-page application (SPA)** built with vanilla HTML, CSS, and minimal JavaScript. It serves as the public-facing web presence for DevBlock Technologies — a Lagos-based software engineering company.

**URL:** https://devblocktechnologies.com.ng  
**Repository:** https://github.com/DEVBLOCK-TECHNOLOGIES-LIMITED/website  
**Hosting:** GitHub Pages (via repository deployment)

## Technology Stack

| Layer | Technology | Rationale |
|---|---|---|
| **Markup** | HTML5 | Semantic, accessible, no build step required |
| **Styling** | CSS3 (custom properties, flexbox, grid) | Zero-dependency, modern layout, responsive |
| **JavaScript** | Vanilla JS (~40 lines) | Smooth scrolling, navbar effects, mobile menu |
| **Typography** | Google Fonts — Inter | Clean, modern, widely available |
| **Icons** | Inline SVG | No icon library dependency, crisp at any size |
| **Favicon** | Data URI SVG | No external file, works offline |
| **Contact Form** | Formspree (freemium) | No backend required, email delivery |
| **Hosting** | GitHub Pages | Free, CDN-backed, auto-deploys on push |
| **Version Control** | Git + GitHub | Standard, PR-based workflow |

### Design Principles

1. **Zero Build Step** — No bundler, no framework, no npm. Editable with any text editor.
2. **Dark Theme** — Dark background (`#0a0a0f`) with blue accent (`#167CFA`) for a professional, modern look.
3. **Mobile-First Responsive** — Breakpoints at 1024px, 768px, and 480px. Mobile hamburger menu with slide-in nav.
4. **Performance** — Inline critical CSS patterns, SVG icons, no render-blocking JS. Lighthouse target: 95+.
5. **Accessibility** — Semantic HTML5, ARIA labels, keyboard-navigable, focus styles on form elements.

## File Structure

```
website/
├── index.html          # Single-page application (all sections)
├── style.css           # Complete stylesheet (~420 lines)
├── ARCHITECTURE.md     # This file
└── .git/               # Git repository
```

### Why a Single File?

- **Simplicity** — No routing, no frameworks, no server-side rendering
- **SEO** — All content is crawlable from one URL with proper meta tags
- **Performance** — Single HTTP request for HTML, one CSS file, no JS framework
- **Deploy** — Push to GitHub, Pages auto-deploys. Zero configuration.

## Page Sections

| Section | ID | Purpose |
|---|---|---|
| **Navigation** | `#navbar` | Fixed top nav, scroll-aware background blur |
| **Hero** | `#hero` | Value proposition, CTA, animated grid visual |
| **Services** | `#services` | 6 service cards in 3-column grid |
| **Products** | `#products` | 5 product items in list layout |
| **Industries** | `#industries` | 6 industry cards in 3-column grid |
| **About** | `#about` | Company narrative + value cards |
| **Contact** | `#contact` | Contact info + Formspree form |
| **Footer** | `footer` | Logo, link columns, copyright |

### Navigation Flow

All nav links use hash-based smooth scrolling (`href="#section-id"`). The mobile menu is a slide-in overlay triggered by a hamburger toggle. Nav items close the menu on click.

## CSS Architecture

### Custom Properties (Design Tokens)

```css
:root {
  --bg-primary: #0a0a0f;      /* Page background */
  --bg-secondary: #111118;    /* Alternating section background */
  --bg-card: #16161f;         /* Card surfaces */
  --bg-card-hover: #1c1c28;   /* Card hover state */
  --text-primary: #f0f0f5;    /* Headlines, body */
  --text-secondary: #a0a0b0;  /* Paragraphs, secondary text */
  --accent: #167CFA;          /* Primary brand color */
  --accent-glow: rgba(22,124,250,0.25);  /* Glow effects */
  --border: rgba(255,255,255,0.06);      /* Subtle borders */
  --radius: 12px;             /* Standard border radius */
  --max-width: 1200px;        /* Content width cap */
  --nav-height: 72px;         /* Fixed nav height */
}
```

### Layout Patterns

- **Flexbox** — Navigation, hero, about/contact split layouts, footer columns
- **CSS Grid** — Services grid (3-col), industries grid (3-col), hero visual grid (3×3)
- **clamp()** — Fluid typography for headlines (e.g., `clamp(36px, 5.5vw, 56px)`)
- **Custom scroll** — `scroll-behavior: smooth` + `scroll-padding-top` for fixed nav offset

### Responsive Breakpoints

| Breakpoint | Changes |
|---|---|
| **1024px** | Hide hero visual, 2-col grids, stack about/contact layouts |
| **768px** | Single-col grids, mobile nav (slide-in), stack CTA buttons |
| **480px** | Smaller headline sizes, stack footer columns |

## Contact Form

The form posts to **Formspree** (free tier: 50 submissions/month):

```html
<form action="https://formspree.io/f/xvgkgwnz" method="POST">
```

Fields: `name` (required), `email` (required), `company` (optional), `message` (required).

Formspree handles spam filtering, email delivery, and confirmation pages. No server-side code needed.

## Deployment

**Platform:** GitHub Pages  
**Branch:** `main` (or `gh-pages` if configured)  
**Custom Domain:** `devblocktechnologies.com.ng` (requires CNAME record)

### Deploy Steps

1. Push to `main` branch
2. GitHub Pages auto-deploys from the branch root
3. Site is live at the configured custom domain

### DNS Configuration (Cloudflare or similar)

```
CNAME  @  devblock-technologies-limited.github.io
CNAME  www  devblock-technologies-limited.github.io
```

## SEO & Meta

- **Title:** "DevBlock Technologies — Intelligent Software Engineering"
- **Description:** Company description with keywords
- **OG Tags:** Open Graph title, description, type, URL, image
- **Twitter Card:** `summary_large_image`
- **Theme Color:** `#0a0a0f` (dark background)
- **Favicon:** Inline SVG data URI (no external request)

## Future Considerations

- **Multi-page** — If content grows, split into separate HTML files (services.html, products.html, etc.)
- **Blog** — Could add a `/blog` directory with markdown-to-HTML posts
- **Analytics** — Add Plausible or Cloudflare Web Analytics for privacy-respecting metrics
- **CMS** — If frequent content updates needed, consider headless CMS + static site generator (Astro, 11ty)
- **i18n** — If international audience grows, add language switcher with locale-specific pages
- **Performance budget** — Keep total page weight under 200KB (currently ~42KB HTML + CSS)

## Maintenance

- Edit `index.html` for content changes
- Edit `style.css` for visual changes
- No build step — changes go live on push
- Test on mobile and desktop before merging
