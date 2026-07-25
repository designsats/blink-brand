---
name: blink-brand
description: "Blink's brand and UI design system — the single source of truth for colors, typography, spacing, logo usage, icons and imagery. Load this BEFORE producing any Blink-branded output: presentations, decks, slides, landing pages, social cards, one-pagers, demos, prototypes, internal tools, diagrams, charts, email, print or merch. Also load it when reviewing existing material for brand compliance, when asked 'is this on-brand', when picking any color or font for Blink, or when someone mentions Blink brand, brand book, brand guidelines, design system, design tokens, or the Blink logo."
---

# Blink Brand System

Blink is the everyday Bitcoin wallet. This skill makes anything you produce look like
Blink built it.

**The one rule that matters:** never invent a value. Every color, size, space and radius
you use must come from this document. If you need something that isn't here, use the
nearest token that is — do not interpolate, do not "adjust slightly", do not add a tint.

## Decide first: which surface?

Blink deliberately runs **two type systems**. Pick the right one before you write a line.

| | Brand surfaces | Product surface |
|---|---|---|
| **What** | decks, slides, web, social, print, merch, docs, diagrams | the Blink mobile app |
| **Typeface** | **IBM Plex Sans** | **Source Sans Pro** |
| **Type scale** | 68 / 38 / 24 / 20 / 16 / 14 | 24 / 20 / 18 / 16 / 14 / 12 |
| **Primary orange** | `#f18a00` brand, `#fc5805` accent | `#fc5805` light, `#ffad0d` dark |
| **Blue** | `#5D78DA` | legacy app blues — do not copy |

Almost everything you are asked for is a **brand surface**. Use IBM Plex Sans unless you
are writing code inside the `blink-mobile` repo.

## Core tokens — memorize these

```
BRAND
  orange          #f18a00    logo, print, gradient        Pantone 144 C
  yellow          #ffbe0b    logo, gradient               Pantone 123 C
  sunset          #fb5607    gradient                     Pantone Orange 021 C
  blue            #5D78DA    brand surfaces only
  black           #000000    Venta black                  Pantone Process Black

ACCENT (UI actions: buttons, links, active states)
  accent          #fc5805    light mode
  accent          #ffad0d    dark mode

FEEDBACK
  error           #DC2626      warning  #F59E0B      success  #00A700

NEUTRAL — light mode              NEUTRAL — dark mode
  bg.default      #FFFFFF          bg.default      #1d1d1d
  bg.surface      #F2F2F4          bg.surface      #2B2B2B
  bg.raised       #E7E7E7          bg.raised       #393939
  text.primary    #1d1d1d          text.primary    #FAF9F9
  text.secondary  #3A3C51          text.secondary  #E9E8E8
  text.muted      #9292A0          text.muted      #949494
  border          #E2E2E4          border          #393939

GRADIENT
  linear-gradient(45deg, #ffbe0b, #fb5607)
  yellow bottom-left → sunset orange top-right. This exact angle, these exact stops.

SPACING   3  5  8  10  14  20  30
RADII     8 (small)   16 (large)   999 (full/pill)     — only these three
```

Full palette with usage rules, contrast pairs and dark-mode logic:
`references/colors.md`

## Typography — brand surfaces

**IBM Plex Sans.** Free, open source, from Google Fonts. Never substitute Arial,
Helvetica, Inter or a system stack.

```
display   68px / 1.0em   Bold 700       title slides, hero headlines
h1        38px / 1.15em  Bold 700       section headings
h2        24px / 1.2em   Bold 700       subsection headings
h3        20px / 1.3em   Medium 500     card titles, lead-ins
body      16px / 1.5em   Regular 400    all body copy
small     14px / 1.4em   Regular 400    captions, labels, footnotes
```

Weights available: Light 300 · Regular 400 · Medium 500 · SemiBold 600 · Bold 700.
Use Light 300 only at 20px and above — it disappears at body size.

- Body copy never below 14px. On slides, never below 16px.
- Line length 45–75 characters. Never full-bleed paragraphs.
- Sentence case for headings. Not Title Case, not ALL CAPS — except the tagline,
  which is always `THE EVERYDAY BITCOIN WALLET`.
- Never letterspace body text. Headings may take `-0.01em` at 38px and above.

Details, the product scale, and the CSS/Google Fonts snippets: `references/typography.md`

## Logo — the rules people break

Assets are in `assets/logo/`. Always use the SVGs provided; never redraw, never
re-download from elsewhere, never trace from a screenshot.

**Always**
- Use the horizontal lockup (`blink-logo-horizontal.svg`) as the default.
- Keep clear space of at least `x` on every side, where `x` = the height of the
  circle mark. Nothing enters that zone.
- Minimum size 50px wide for the horizontal lockup.
- On dark backgrounds use `-on-dark.svg`; on photography or busy backgrounds use
  `blink-logo-mono-white.svg`.
- The standalone circle mark (`blink-mark.svg`) is allowed **only** as an app icon,
  favicon, avatar or social profile image — never as a logo in a layout.

**Never**
- Never recolor the wordmark. It is black `#000000` or white `#FFFFFF`, nothing else.
- Never apply a gradient to the wordmark. Only the circle carries the gradient.
- Never change the proportions, rotate, skew, or stack the mark above the wordmark.
- Never add effects — no shadow, glow, outline, bevel.
- Never place text or graphics inside the clear space.
- Never rebuild the lockup by typing "blink" in Ubuntu next to a bitcoin symbol.

Construction diagrams, the tagline lockup and every prohibited case:
`references/logo.md`

## Layout, icons and imagery

**Spacing** — use only `3 · 5 · 8 · 10 · 14 · 20 · 30`. Compose larger gaps by
doubling the top of the scale (30 → 60 → 90). Default rhythm on a slide: 30 between
sections, 20 between blocks, 10 within a block.

**Radii** — `8` for anything small (chips, inputs, small cards), `16` for anything
large (cards, modals, panels, image crops), `999` for pills, buttons and avatars.
Nothing else. Blink buttons are pills.

**Icons** — Phosphor, Regular weight. Bold only for emphasis at small sizes. When an
icon you need doesn't exist in Phosphor, draw it on Phosphor's grid: 256×256 box,
16px stroke, round caps and joins, so it sits invisibly alongside the set.
Never mix Phosphor with Material, Font Awesome or emoji-as-icons.

**Imagery** — documentary photography of real people using Blink in real places.
Natural light, candid, the moment of paying or receiving. Never stock crypto clichés:
no 3D gold coins, no hooded figures, no matrix green, no rockets, no charts-with-arrows.
Product screenshots: light theme by default, full screens never partial crops, in a
neutral device frame.

Full specs including the pattern tile and screenshot sample data:
`references/layout.md` and `references/imagery.md`

## Language

Say **Blink** — never "blink" or "BLINK". Say **sats** lowercase. **Bitcoin** capitalized
for the network and protocol, **bitcoin** lowercase for the money. **Lightning**
capitalized. The tagline is **The Everyday Bitcoin Wallet** and is never reworded.

Full always/never word list: `references/terminology.md`

**Tone of voice is not yet defined (TBD).** Until it is, write plainly: concrete, second
person, active voice, no hype, no exclamation marks, no undefined jargon. Do not invent
a brand voice or claim one exists.

## Templates

Start from these rather than building from scratch:

- `templates/deck.html` — 16:9 slide deck, all slide types, light/dark/colored
- `templates/social.html` — square, story and wide social cards
- `templates/onepager.html` — document / memo / report

Each is self-contained HTML with the tokens inlined. Open in a browser, print to PDF,
or screenshot for slides.

## Known non-conforming material

Blink's existing surfaces contain drift. **Do not copy from them** — if you are looking
at an existing deck, the live website, or app code for reference, check this list first:

- **blink.sv ships an Untitled UI purple palette** (`#7f56d9`, `#6941c6`) and a purple
  gradient. Purple is not a Blink color. Never reproduce it.
- **blink.sv uses `#ffb32c`** as its yellow. The correct yellow is `#ffbe0b`.
- **blink.sv uses five gradient angles.** Only 45° is correct.
- **The app has four blues.** None is the brand blue. Do not sample blue from the app.
- **The app's dark theme inverts `white` and `black` token names** — in dark mode its
  `white` token is `#000000`. Never read raw values out of `colors.ts` without checking.

Full inventory with counts and locations: `references/non-conforming.md`

## Components

**Not yet documented — open, to be completed in the next session.** The Blink component
library (buttons, cards, inputs, modals, nav, toasts, badges) lives in Figma and in
`app/components/` in the `blink-mobile` repo, and has not yet been specified here.

Until it is: build components from the tokens above — pill buttons, `16` radius cards,
`8` radius inputs, `20` internal padding — and say clearly in your output that component
specs are provisional. Do not invent component rules and present them as canonical.

See `references/components.md` for the current status and what's needed.
