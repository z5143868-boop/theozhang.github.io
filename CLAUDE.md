# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for 张润哲 (Theo Zhang) — a bilingual (Chinese/English) single-page site hosted on GitHub Pages at `theozhang.top`.

## Architecture

- **Single-file site**: Everything (HTML, CSS, JS) lives in `index.html` (~980 lines)
- **No build system**: Static HTML served directly via GitHub Pages
- **No dependencies**: Pure vanilla HTML/CSS/JS, no frameworks or package managers
- **Deployment**: Push to `main` branch auto-deploys via GitHub Pages. Custom domain configured in `CNAME`.

## Key Patterns

### Bilingual System

The site uses CSS class toggling for language switching — not separate pages or i18n libraries:

- `body.lang-en` toggles English mode; default (no class) is Chinese
- Block-level: `.zh` / `.en` classes (display: block/none)
- Inline-level: `.zh-i` / `.en-i` classes (display: inline/none)
- `setLang()` function in the script section handles the toggle

When adding new content, always provide both `zh` and `en` variants.

### Sections

Six sections with IDs `s0`–`s5`: Hero, About, Skills, Experience, AI, Contact. Navigation dots track scroll position via IntersectionObserver.

### Scroll Reveal

Elements with class `reveal` get animated in via IntersectionObserver. Add `reveal` to new content blocks for consistent entrance animations.

## Development

Open `index.html` directly in a browser — no server needed. For live reload during development, use any static file server (e.g., `python -m http.server`).
