# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # dev server (localhost:4321)
npm run build     # production build → dist/
npm run preview   # preview production build
npm run deploy    # deploy to Vercel production
```

## Architecture

Single-page site. `src/pages/index.astro` assembles sections in order:
`Navbar → Hero → About → Stack → Projects → Contact → Footer`

`src/layouts/Layout.astro` provides:
- Google Fonts (Inter + JetBrains Mono) + Devicon CDN
- Cursor-glow effect (`#cursor-glow` div on mousemove)
- Scroll-reveal via `IntersectionObserver` (`.reveal`, `.reveal-left`, `.reveal-right`)
- 3D card tilt on `.card-tilt` elements

## Design Tokens (`tailwind.config.mjs`)

Colors: `space` (#050510), `neon-violet` (#7C3AED), `neon-cyan` (#06B6D4), `neon-amber` (#F59E0B)  
Fonts: `font-sans` = Inter, `font-mono` = JetBrains Mono  
Animations: `float-slow/med/fast`, `spin-slow`, `pulse-slow`, `scroll-down`

## CSS Utility Classes (`src/styles/global.css`)

Do not duplicate these in Tailwind — defined in `global.css` only:

- `.glass`, `.glass-hover` — frosted glass cards
- `.text-gradient`, `.text-gradient-amber`, `.text-gradient-3` — gradient text
- `.gradient-border` — animated gradient border via `::before` pseudo-element
- `.btn-primary`, `.btn-secondary` — CTA buttons
- `.section-badge` — monospace pill labels
- `.glow-violet/cyan/amber` — neon box-shadow utilities
- `.reveal`, `.reveal-left`, `.reveal-right` + `.reveal-delay-1…6` — scroll animation
- `.glitch-wrapper` — glitch effect (requires `data-text` attribute matching inner text)
- `.input-field` — form input styling

Astro config: `tailwind({ applyBaseStyles: false })` — base styles from `global.css` only, never from Tailwind preflight.
