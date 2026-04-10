# Human Capital Quarterly — Brand Guide

## Overview

**Human Capital Quarterly (HCQ)** is a hands-on event series for skill and career exploration, co-presented by **DC Public Library** and **Levy**. The flagship event is the Spring Forum, held at MLK Memorial Library in Washington, D.C.

- **Domain**: `humancapital.withlevy.com`
- **Tagline**: A hands-on afternoon of skill and career exploration
- **Co-presenters**: DC Public Library · Levy

---

## Color Palette

The brand uses a strict four-color system. Every surface is one of these four colors; no tints or intermediate values are used.

| Name | Hex | CSS Variable | Usage |
|------|-----|-------------|-------|
| White | `#F9F9F8` | `--white` | Default page background, light text on dark fields |
| Carbon | `#121212` | `--carbon` | Primary text, dark section backgrounds, borders |
| Red | `#E4002B` | `--red` | CTAs, selection highlight, pull-quote border, hero serif rows |
| Blue | `#41B6E6` | `--blue` | Hero display text, punch/announcement fields, coalition section |

### Color Rules

- **Red = action and urgency.** Use it for primary calls to action, important emphasis, and text selection. Red text on light backgrounds uses `mix-blend-mode: multiply` so it blends like an overprint.
- **Blue = content and information.** Use it for large display text and full-width content fields.
- **Carbon = authority and structure.** Default text color, borders, and the ticker bar.
- **White = space and clarity.** Default background; never pure `#FFFFFF`.

### Text on Color Fields

| Background | Text Color |
|-----------|-----------|
| White | Carbon |
| Carbon | White |
| Blue | Carbon |
| Red | Carbon |

### Selection Color

```css
::selection { background: var(--red); color: var(--white); }
```

---

## Typography

Five typefaces are in use. Each has a specific role; do not substitute.

| Role | Family | CSS Variable | Weights | Source |
|------|--------|-------------|---------|--------|
| Display / System | Overpass | `--sys` | 700, 800, 900 | Google Fonts |
| Serif | Instrument Serif | `--serif` | 400, 400 italic | Google Fonts |
| Body | IBM Plex Sans | `--body` | 300, 400, 600 | Google Fonts |
| Monospace | IBM Plex Mono | `--mono` | 400, 600 | Google Fonts |
| Handwritten | Caveat | `--hand` | 400 | Google Fonts |

### Font Roles

**Overpass** (`--sys`, weight 900) — Large hero titles, display words. Always uppercase, negative letter-spacing (`-0.04em`). Colored blue in the hero interleave.

**Instrument Serif** (`--serif`) — Section headings, pull quotes, body elegance. Used italic for the red overprint rows in the hero and for `.hop` elements.

**IBM Plex Sans** (`--body`, weight 300 default) — All body copy and paragraphs. Line-height 1.6–1.7. Rendered at `clamp(.98rem, 1.5vw, 1.15rem)` for body text.

**IBM Plex Mono** (`--mono`) — Navigation labels, button text, metadata, form labels, the ticker bar. Always uppercase, letter-spacing `0.07em`–`0.10em`. Base size: `0.75rem` (`--meta`).

**Caveat** (`--hand`) — Decorative marginalia notes only. Never used for functional text. Hidden on mobile.

### Type Scale

| Context | Value |
|---------|-------|
| Metadata / labels | `0.75rem` (`--meta`) |
| Body copy | `clamp(.98rem, 1.5vw, 1.15rem)` |
| Pull quote | `clamp(1.2rem, 2.2vw, 2.1rem)` |
| Section heading | `clamp(2rem, 4.2vw, 4.6rem)` |
| Hero display | `clamp(3.2rem, 15.5vw, 16rem)` (`--hfs`) |
| Large hero stat | `clamp(2.8rem, 8.5vw, 8rem)` |

---

## Spacing & Layout

### CSS Tokens

```css
--sp-y:     clamp(4rem, 9vw, 8rem);   /* vertical section padding */
--sp-x:     clamp(1.5rem, 5.5vw, 6vw); /* horizontal padding */
--ticker-h: 2.35rem;                   /* fixed ticker bar height */
--meta:     0.75rem;                   /* base small-text size */
--hfs:      clamp(3.2rem, 15.5vw, 16rem); /* hero font size */
```

### Container

Max content width: **1340px** via `.inner { max-width: 1340px; margin: 0 auto; }`

### Section Borders

Adjacent `.sec` elements are separated by a `2px solid var(--carbon)` top border.

### Responsive Breakpoints

| Breakpoint | Width | What Changes |
|-----------|-------|-------------|
| Tablet | `800px` | 3-column grids drop to 2 columns; sidebar goes static |
| Small | `620px` | Nav links hidden (CTA pill remains visible) |
| Mobile | `600px` | Hero font-size adjusts; marginalia hidden |
| Very small | `460px` | 2-column grids collapse to 1 column; bottom row stacks |

---

## Components

### Navigation

The nav is two elements: a **ticker bar** (fixed, always topmost) and a **nav bar** (fixed below the ticker).

**Ticker bar** — Carbon background, white monospace text, uppercase, continuous scroll animation (65 seconds, `translateX(-50%)`). `z-index: 600`.

**Nav bar** — White background pills separated by `1.5px solid var(--carbon)` borders. The leftmost pill is the brand identifier; rightmost pill is the CTA (red background). Hover: carbon background / white text. `z-index: 500`. On mobile (`≤620px`), only the CTA pill is visible.

### Buttons

All buttons: monospace font, `0.75rem`, uppercase, `letter-spacing: 0.1em`, `2px solid` border, padding `0.85rem 2rem`.

| Class | Default | Hover |
|-------|---------|-------|
| `.btn-red` | Red bg / white text / red border | Carbon bg / carbon border |
| `.btn-dark` | Transparent / carbon text / carbon border | Carbon bg / white text |
| `.btn-white` | White bg / carbon text / white border | Transparent / white text / faded border |
| `.btn-ghost` | Transparent / white text / faded white border | White border |
| `.btn-blue` | Blue bg / carbon text / blue border | *(page-specific)* |

### Forms

- Border: `1.5px solid var(--carbon)` on inputs and selects
- Focus: `outline: 2px solid var(--red)`
- Labels: monospace, uppercase
- Input padding: `0.9rem 1rem`
- Submit button uses `.btn-red` styling

### Cards / Grid

- Default grid: 3 columns → 2 at `800px` → 1 at `460px`
- Card borders: `1px solid` carbon (often with opacity)
- Cards reveal on scroll: `opacity: 0` → `opacity: 1` with `translateY` over `0.7s ease`

### Pull Quotes

`.pull` — Instrument Serif, `clamp(1.2rem, 2.2vw, 2.1rem)`, carbon, `border-left: 3px solid var(--red)`, padding-left `1.5rem`.

`.pull-motto` — Instrument Serif italic, `clamp(1.35rem, 2.6vw, 2.6rem)`, carbon, `opacity: 0.72`, no border.

---

## Special Treatments

### Hero Interleave Effect

The hero uses alternating rows of:
- **Blue Overpass** (`.hw`) — weight 900, uppercase, `letter-spacing: -0.04em`, full `--hfs` height
- **Red Instrument Serif italic** (`.hop`) — `52%` of `--hfs`, uses `mix-blend-mode: multiply` and negative top/bottom margins (`-0.28 × --hfs`) to mathematically overlap the blue rows

This creates an overprint/letterpress visual. It only works correctly in light color-scheme contexts; the hero sets `color-scheme: only light` to prevent dark-mode inversions.

### Paper Grain Texture

All pages apply a subtle SVG fractal noise texture as a fixed `::after` pseudo-element on `body`. Opacity: `0.028`. The texture adds an analog, printed quality without affecting readability.

### Marginalia

Handwritten Caveat notes (`.mg`, `.mg-lg`, `.mg-dark`, `.mg-blue`) are absolutely positioned decorative annotations. They are `aria-hidden="true"` and hidden on mobile. Colors:
- `.mg` / `.mg-lg` — red
- `.mg-dark` — carbon
- `.mg-blue` — blue

### Scroll Reveal

Elements with the `.reveal` class animate in on scroll via an `IntersectionObserver`: `opacity: 0; transform: translateY(20px)` → `opacity: 1; transform: translateY(0)` over `0.7s ease`. Respects `prefers-reduced-motion`.

---

## Logos & Assets

### Logo Files

| File | Path | Dimensions | Use Case |
|------|------|-----------|----------|
| DCPL 4-color vertical | `/DCPL_2020_Logo_4C_Vertical_w-tagline.png` | 1454 × 1440 px | White or light backgrounds |
| DCPL knockout | `/logos/dcpl-knockout.png` | 350 × 288 px | Dark or colored backgrounds |
| Levy knockout | `/logos/levy-knockout.png` | 20367 × 9880 px | Dark or colored backgrounds |

**On white/light backgrounds**: use the 4-color DCPL logo at `opacity: 0.85`.  
**On carbon/blue backgrounds**: use knockout logos with `filter: invert(1)` and `opacity: 0.9`.

Logo display heights: `28px` (hero, `.logo-ph`) · `22px` (sidebar, `.logo-ph-sm`)

### Open Graph Images

| Page | File | Dimensions |
|------|------|-----------|
| Spring Forum | `/images/og-spring-forum.jpg` | 1200 × 630 px |
| Practitioner Sessions | `/images/og-practitioner-sessions.jpg` | 1872 × 996 px |

---

## Pages

| Page | Path | Hero Color | Purpose |
|------|------|-----------|---------|
| Spring Forum | `/index.html` | White (blue/red interleave) | Primary event landing |
| Request a Table | `/expo/index.html` | Blue | Exhibitor registration |
| Practitioner Sessions | `/sessions/index.html` | Red | April 10 sessions day |
| Spread the Word | `/spread-the-word/index.html` | Blue | Promotional asset kit |
| Downloads | `/sessions/downloads/index.html` | — | Worksheet distribution |

Each page shares the same CSS token system. The hero background color and section field order vary by page, but all color, type, and spacing tokens remain constant.

---

## Accessibility

- **Skip link**: `.sr-only` skip-to-content link at the top of each page
- **Focus styles**: `outline: 2px solid var(--red)` on `:focus-visible`
- **Reduced motion**: Scroll reveal and hero animations are disabled when `prefers-reduced-motion: reduce` is set
- **Decorative elements**: Ticker content and marginalia carry `aria-hidden="true"`
- **Navigation**: `role="navigation"` on nav elements
- **Touch targets**: Nav pills and buttons have `min-height: 44px`
- **Semantic HTML**: Proper heading hierarchy, `<main>`, `<section>`, `<footer>` throughout

---

## Voice & Tone

HCQ's visual language reflects its editorial voice: **direct, warm, credible, and energetic**.

- **Direct**: Short imperative headings, concrete outcomes, no jargon
- **Warm**: Handwritten marginalia annotations add personality and human presence alongside the formal monospace structure
- **Credible**: Co-presenter authority (DCPL + Levy), specific event details (dates, addresses, names)
- **Energetic**: Bold display typography, high-contrast color fields, animated ticker

Copy is written in sentence case for body text and ALL CAPS for labels, navigation, and metadata. Serif italic is used for emphasis and rhetorical weight; it is not used for informational text.
