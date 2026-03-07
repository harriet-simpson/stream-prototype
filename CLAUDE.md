# Myndstream — Stream Prototype

## Project Overview

A frontend-only UI prototype for **Myndstream**, a therapeutic music streaming service targeting wellness, spa, and healthcare settings. The prototype demonstrates the core user experience across three HTML pages — no build step, no framework, no backend.

## Stack

- **Pure HTML/CSS/JS** — single-file pages, no bundler, no dependencies
- **Vanilla JS** for all interactivity (state, timers, DOM manipulation)
- **CSS** is written inline in each page's `<style>` block
- Assets: `assets/myndstream.svg` (logo)
- External images sourced from Unsplash (prototyping only)

## Pages

| File | Purpose |
|------|---------|
| `index.html` | Home dashboard — main music browsing UI |
| `circadian-radio.html` | Always-on radio stations (Drift / Balance / Uplifting) |
| `session-filter.html` | Treatment Timer — filter by duration, then run a timed session |

## Design System

- **Background**: `#0b0c16` (page), `#0d0e1b` (sidebar/main), `#12131f` (banner)
- **Borders**: `#1a1b2c`
- **Accent blue**: `#7dd3e8` (active nav), `#5bacd4` / `#7b6cf8` (gradient CTA)
- **Text muted**: `#6a7090`, `#7a7b94`
- Dark-mode-only design — no light mode
- All pages share identical sidebar markup and nav structure

## Navigation Structure (Sidebar — replicated per page)

- Home (`index.html`)
- Search / My Favorites / Music Shaker / Zones (placeholder `#` links)
- **Features** section:
  - Circadian Radio -> `circadian-radio.html`
  - Treatment Timer -> `session-filter.html`
- Your Plan -> Mobile Treatments (placeholder)

## Key Patterns

### Shared Layout
Every page uses the same flex layout: `.top-banner` -> `.layout` (`.sidebar` + `.main`). CSS is duplicated across pages — there is no shared stylesheet.

### Active State
Nav links get `.active` class. `#` links prevent default and toggle active via JS. Real page links navigate normally, with the destination page hard-coding `.active` on the correct nav item.

### Card Backgrounds
Colour-coded `.bg-*` classes (e.g. `.bg-relax`, `.bg-pain`, `.bg-sleep`) applied as gradient overlays on music cards.

### Player State (index.html)
Simple `setInterval` ticker advances a `progress` variable; toggling play/pause starts/stops the interval.

### Circadian Radio (circadian-radio.html)
Two views: station grid (`#view-stations`) and full-screen player (`#view-player`). Station data in a `STATIONS` const object; "Also on" pills switch between stations.

### Treatment Timer (session-filter.html)
Three views: filter + grid (`#view-filter`) -> playlist detail (`#view-playlist`) -> active session countdown (`#view-session`). `PLAYLISTS` array drives the grid; `setInterval` drives the countdown timer.

## Development

Open any `.html` file directly in a browser — no server required. For live reload, a simple static server works:

```sh
npx serve .
# or
python3 -m http.server
```

## Notes

- This is a **prototype** — interactions are mocked, no real audio is played
- The "Psychedelic" card on the home page is intentionally locked
- The `bg` property on playlist cards in `session-filter.html` is referenced but no `.bg-*` CSS classes exist on that page — cards fall back to Unsplash `card-img` images
- Brand/partner cards (Crunchfit, Forbes, Marriott, etc.) are visual-only with no action
