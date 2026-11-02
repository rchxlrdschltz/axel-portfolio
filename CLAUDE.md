# CLAUDE.md

Rules for working on Axel Apelo's portfolio site. Read this before changing anything.

## What this is

A static portfolio site for a senior brand and visual designer. Plain HTML, CSS and JS, one file per page, no build step and no package manager. Live at https://axelapelo-portfolio.netlify.app (deployed with Netlify Drop).

| Page | What it is |
|---|---|
| `index.html` | Home: hero with 3D tool ring, selected work, experience, contact |
| `kaia.html`, `charlie.html`, `mura.html`, `p3.html` | Case studies |
| `gallery.html` | Filterable masonry gallery of individual pieces |
| `Apelo-CV.pdf` | CV, linked from every CV button |

## Brand rules

- **The site uses Axel's brand, not the client's.** Page chrome always uses the tokens in `:root` (search `DESIGN TOKENS`): background `#001C1A`, surfaces `#182323` / `#0C2422`, accent lime `#E5FE00`, text white with `--muted` / `--faint` for secondary text.
- **Fonts:** Space Grotesk (display), Plus Jakarta Sans (body), Space Mono (labels). Loaded from Google Fonts.
- **Client colours appear only inside the work** (logos, palette swatches, type specimens, mockups), and only the client's main colours. Never restyle the page in a client's palette.
- Never hard-code a colour or font in a component; use the tokens.

## Case study structure

Every case study follows `kaia.html`. A new one starts as a copy of Kaia, keeping the section order, class names and `data-chapter` labels (they drive the chapter navigation):

1. `.hero`: cover and title
2. `.brief`: opens with the **At a glance** strip (`<dl class="wrap glance">`): `01 · Problem`, `02 · Solution`, `03 · Result`. Problem and Solution each have a `<strong class="g-head">` hook and a `<span class="g-body">` line; Result is one line in the accent colour. Then the brief itself (`.brief-grid`).
3. `#idea`: the idea behind the mark
4. `#system`: the identity system (logos, colour, type; client's main colours and fonts only)
5. Applications: mockups, print, social, website (whichever the project has)
6. `#outcome`: the result
7. `#end`: credits and call to action

Copy is client-facing: lead with the business problem and the outcome, not the process. Only state results that are real and confirmed.

## Gallery

- All items live in `const GALLERY = [...]` near the bottom of `gallery.html`. Each entry: `{ src, w, h, cat, title, client, alt }`.
- `cat` must be one of: `Branding`, `Web & UI`, `Social`, `Merch`, `Static Ads`, `Print`. Filter chips are built from these automatically.
- Use a typographic apostrophe `’` inside strings. A plain `'` breaks the JS.
- After editing, check the array still parses:
  ```bash
  node -e "const s=require('fs').readFileSync('gallery.html','utf8');const g=eval(s.match(/const GALLERY = (\[[\s\S]*?\n\]);/)[1]);console.log(g.length+' items')"
  ```

## Images

- WebP, long side 1200–1600 px, quality 82. Gallery images go in `assets/gallery/<category>/`, case study images in `assets/<project>/`.
- Always set `width`, `height` and a descriptive `alt`.
- Link previews: every page has `og:image` and `twitter:image` with an **absolute** URL to a 1200×630 JPG in `assets/og/`, plus a matching `og:url`.

## Motion

- Smooth scroll is Lenis from jsDelivr (pinned version). The site must still work if it fails to load.
- Add `data-m` to an element to give it the scroll-in reveal.
- Respect `prefers-reduced-motion`: every animation needs a static fallback.

## Layout

- Content sits in `.wrap` (max 1280px, fluid gutter).
- Check every change at phone width (375px) with no horizontal scroll, and at desktop width.

## Previewing

`.claude/launch.json` defines a dev server named `portfolio` on port 5178. You can also open the HTML files directly in a browser.

## Deploying

Drag the whole folder onto https://app.netlify.com/drop for the `axelapelo-portfolio` site. Netlify serves `/kaia` from `kaia.html`.
