# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **static HTML marketing presentation** for "Sophia" — a smart home system by Soul Hi (soulhi.com.ar). The deliverable is a single self-contained HTML file converted from the original PDF proposal.

There are no build tools, package managers, or backend. To view the project, open `Propuesta Sophia.html` in a modern browser.

## File Structure

- `Propuesta Sophia.html` — The entire application (HTML + embedded CSS + JavaScript, ~863 lines)
- `imagenes2/` — High-resolution section background images (PNG, ~1.5–2 MB each)
- `uploads/sophia pdf limpio.pdf` — Source PDF the HTML was derived from
- `pdf-images/imagenes/` — Images extracted from the original PDF (reference assets)

## Architecture

The HTML file is a linear single-page presentation. All CSS and JavaScript are embedded inline.

**Sections** are `<section>` elements with `data-chapter` attributes:
`inicio` → `sistema` → `luces` → `audio` → `clima` → `seguridad` → `gaia` → `app` → `contacto`

**Navigation:**
- Fixed top navbar with anchor links
- Left-sidebar chapter dots (desktop only) that highlight based on scroll position — driven by `IntersectionObserver`

**JavaScript responsibilities (all inline at bottom of `<body>`):**
- Scroll-triggered reveal animations via `IntersectionObserver`
- Chapter dot active state sync
- Navbar background/color switching when entering dark vs. light sections

**CSS structure (embedded in `<head>`):**
- CSS custom properties (variables) for the design system: colors, typography scale, spacing
- Color palette: `--c-black`, `--c-white`, `--c-gold` (`oklch(0.84 0.06 82)`)
- Fonts: Manrope (body), JetBrains Mono (technical/mono text) — loaded from Google Fonts CDN
- Responsive breakpoints: `720px` (tablet), `980px` (desktop)
- Reveal animation utility: `.reveal` + `.reveal.visible` classes toggled by JS

## Deployment

Copy the entire `Sophia/` folder to any static web server. No server-side processing required.
