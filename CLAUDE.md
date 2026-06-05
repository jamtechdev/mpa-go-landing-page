# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static marketing website for MPA (a student internship placement company). The entire site is a **single `index.html`** with no build step, no package manager, and no framework.

## Running Locally

Open `index.html` directly in a browser — no server required. Tailwind CSS is loaded via CDN, so an internet connection is needed for styles to render correctly.

## Architecture

Everything lives in `index.html`:

- **Styles**: Tailwind CSS via CDN with an inline `tailwind.config` block defining the custom palette and Montserrat font family
- **Custom color tokens** (defined in `tailwind.config`): `blue` (#00aeff), `orange` (#ff6a00), `green` (#75b900), `turquoise` (#9ddfdf), plus `*Light` variants for each, and `textColor` (#262626)
- **Clip-path chevron shape**: applied repeatedly via Tailwind's arbitrary `[clip-path:polygon(...)]` syntax — the pattern `(0px 0px, calc(100%-Npx) 0px, 100% 50%, calc(100%-Npx) 100%, 0px 100%)` creates the rightward-pointing arrow shape; the mirrored version points left
- **Responsive dual layout**: desktop (lg+) uses a tab interface (`#tabs`, `.tab-btn`, `.tab-content`); mobile uses an accordion (`#accordion`, `.accordion-btn`, `.accordion-content`) — both contain the same content but are toggled via `hidden lg:block` / `block lg:hidden`
- **Inline `<script>`** at the bottom handles all interactivity: tab switching, accordion toggling, and the "Get Started" dropdown menu

## Assets

`assets/images/` contains all images — logos, banner images (separate desktop/mobile variants), social icons, and decorative images. No image optimization pipeline exists.
