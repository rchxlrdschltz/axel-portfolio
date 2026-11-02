# Axel Apelo — Portfolio

**Live site:** https://axelapelo-portfolio.netlify.app

The portfolio of Axel Apelo, a senior brand and visual designer. It has four case studies and a gallery of brand, web, social, ad, print and merch work.

Built with [Claude Code](https://claude.com/claude-code). Project rules for Claude are in [`CLAUDE.md`](CLAUDE.md).

## Pages

- **Home:** a 3D ring of design tools in the hero, selected work, experience and contact
- **Case studies:** [Kaia](https://axelapelo-portfolio.netlify.app/kaia), [Charlie AI](https://axelapelo-portfolio.netlify.app/charlie), [Mura](https://axelapelo-portfolio.netlify.app/mura) and [P3](https://axelapelo-portfolio.netlify.app/p3). Each opens with a Problem / Solution / Result summary.
- **[Gallery](https://axelapelo-portfolio.netlify.app/gallery):** a filterable masonry grid with a lightbox

## How it's built

- Plain HTML, CSS and JavaScript, with no framework and no build step
- One file per page, sharing a set of CSS design tokens
- Smooth scrolling with [Lenis](https://github.com/darkroomengineering/lenis), and scroll-in reveals on any element with `data-m`
- A reduced-motion version for visitors who turn animation off
- Responsive from phone to desktop
- WebP images, with Open Graph preview images for every page
- Deployed on Netlify

## Run it locally

Open `index.html` in a browser. Or, with Python installed:

```bash
python -m http.server 5178
```

Then go to http://localhost:5178.

---

All client work shown is © its respective owners and is included for portfolio purposes only.
