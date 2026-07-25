# Blink — Typography

Blink runs two typefaces on purpose. Choose by surface, never by preference.

## Brand surfaces — IBM Plex Sans

Decks, slides, web, social, print, merch, documentation, diagrams, internal tools.

IBM Plex Sans is open source (SIL OFL). Available from Google Fonts.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
```

```css
font-family: "IBM Plex Sans", system-ui, sans-serif;
```

### Scale

Taken from the live blink.sv stylesheet so web, decks and social agree.

| Role | Size | Line height | Weight | Use |
|---|---|---|---|---|
| `display` | 68px | 1.0em | Bold 700 | Title slides, hero headlines |
| `h1` | 38px | 1.15em | Bold 700 | Section headings |
| `h2` | 24px | 1.2em | Bold 700 | Subsection headings |
| `h3` | 20px | 1.3em | Medium 500 | Card titles, lead-ins |
| `body` | 16px | 1.5em | Regular 400 | All body copy |
| `small` | 14px | 1.4em | Regular 400 | Captions, labels, footnotes |

For dense documents, `body` may drop to 14px and `small` to 12px. On slides it may not —
16px is the floor on anything projected.

The jump from 68 to 38 is large by design: display is for a single line on a title
slide, not for running headings. If a headline needs to wrap more than twice at 68px,
use `h1` instead of shrinking `display`.

### Weights

Light 300 · Regular 400 · Medium 500 · SemiBold 600 · Bold 700

- Light 300 only at 20px and above. It vanishes at body size.
- Medium 500 for UI labels, buttons and small emphasis.
- Bold 700 for headings. Do not use 800 or 900 — Plex has them, Blink does not use them.
- Italic exists but is used sparingly, and never for emphasis in UI. Use weight instead.

### Rules

- Line length 45–75 characters. Constrain paragraph width; never let copy run full-bleed.
- Sentence case for headings. Not Title Case. Not ALL CAPS.
- The only permanent all-caps string is the tagline: `THE EVERYDAY BITCOIN WALLET`.
- Never letterspace body text. Headings may take `-0.01em` at 38px and above.
- Never justify. Left-aligned, ragged right. Centered only on title slides.
- Never use more than three sizes on a single slide.
- Numbers in tables and financial figures use tabular figures:
  `font-variant-numeric: tabular-nums`.

## Product surface — Source Sans Pro

The Blink mobile app only. Do not use it on brand surfaces; do not use IBM Plex in
the app.

| Role | Size | Line height | Weight |
|---|---|---|---|
| `h1` | 24px | 32px | 400 / 600 bold |
| `h2` | 20px | 24px | 400 / 600 bold |
| `p1` | 18px | 24px | 400 / 600 bold |
| `p2` | 16px | 24px | 400 / 600 bold |
| `p3` | 14px | 18px | 400 / 600 bold |
| `p4` | 12px | 18px | 400 / 600 bold |

Defined in `app/rne-theme/theme.ts`. Note the app's real usage includes sizes and
weights outside this scale — see `non-conforming.md`.

## Logotype — Ubuntu Bold Italic

Used **only** in the Blink logo, which already exists as finished SVG artwork.

You will never need to set type in Ubuntu. If you find yourself typing "blink" in
Ubuntu Bold Italic, stop — you are rebuilding the logo by hand, which is prohibited.
Use `assets/logo/blink-logo-horizontal.svg`.

## Retired

**DM Sans** ships in the app's font assets and is referenced nowhere. It is not a Blink
typeface. Do not use it, and do not treat its presence in the repo as permission.
