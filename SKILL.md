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
| **Primary orange** | `#f18a00` brand, `primary` for UI | `primary` `#fc5805` light, `#ffad0d` dark |
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

PRIMARY (UI actions: buttons, links, active states) — mirrored between themes
  primary         #fc5805 light   #ffad0d dark
  primary3        #fd800b         #fe990d
  primary4        #fe990d         #fd800b
  primary5        #ffad0d         #fc5805

FEEDBACK
  error  #DC2626    error9  #FEE2E2 light / #7F1D1D dark
  warning #F59E0B   _green (success) #00A700

GREY — the number is the role, not the lightness
                    light      dark
  grey0  text       #3A3C51    #FAF9F9
  grey1  text 2nd   #393939    #E9E8E8
  grey2  muted      #9292A0    #CCCCCC
  grey3  disabled   #AEAEB8    #949494
  grey4  border     #E2E2E4    #393939
  grey5  ground     #F2F2F4    #1d1d1d
  grey6  raised     #E7E7E7    #2B2B2B

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
- The standalone circle mark is allowed **only** as an app icon, favicon, avatar or
  social profile image — never as a logo in a layout.
- For the app icon, favicon and avatar use `blink-app-icon-dark.svg`: the gradient
  mark on a **black** tile. There is one app icon and no light variant.

**Never**
- Never recolor the wordmark. It is black `#000000` or white `#FFFFFF`, nothing else.
- Never apply a gradient to the wordmark. Only the circle carries the gradient.
- Never change the proportions, rotate, skew, or stack the mark above the wordmark.
- Never add effects — no shadow, glow, outline, bevel.
- Never place text or graphics inside the clear space.
- Never rebuild the lockup by typing "blink" in Ubuntu next to a bitcoin symbol.
- Never place the full-colour lockup on orange or on the gradient — the circle
  vanishes into the ground. Use `blink-logo-mono-white.svg` there.
- Never bake a light or coloured tile behind the app icon.
- **There is no Spanish tagline lockup.** The tagline exists in English only; do not
  translate, transliterate or re-set it in any market.

Construction diagrams, the tagline lockup and every prohibited case:
`references/logo.md`

## Layout, icons and imagery

**Spacing** — use only `3 · 5 · 8 · 10 · 14 · 20 · 30`. Compose larger gaps by
doubling the top of the scale (30 → 60 → 90). Default rhythm on a slide: 30 between
sections, 20 between blocks, 10 within a block.

**Radii** — `8` for anything small (chips, inputs, small cards), `16` for anything
large (cards, modals, panels, image crops), `999` for pills, buttons and avatars.
Nothing else. Blink buttons are pills.

**Icons** — Phosphor, **outlines only**. Blink uses three of Phosphor's six weights —
`thin · regular · bold` — the same three the Figma `Icon` set and the app's `IconWeight`
union ship. **Fill and Duotone are never Blink**, and neither is Light. Default to
Regular. Pick from the icons the wallet already has: the Figma `Icon` set, mirrored by
`phosphor-react-native` — don't pull a fresh glyph off phosphoricons.com. When the set
genuinely lacks something, draw an outline on Phosphor's grid: 256×256 box, 16px stroke,
round caps and joins, so it sits invisibly alongside the set. Never mix Phosphor with
Material, Font Awesome or emoji-as-icons. Icons take `currentColor` — they are never
multi-coloured and never carry the gradient. Safe picks and the custom-SVG exceptions:
`references/layout.md`.

**Decoration** — the gradient appears as a *surface* (a hero, a card, a sticker), never
as a decorative rule. Do not put a gradient bar, stripe or rail across the top of a
page, slide or section. Dynamic shapes belong on hero sections; subpages carry nothing.

**Imagery** — documentary photography of real people using Blink in real places.
Natural light, candid, the moment of paying or receiving. Never stock crypto clichés:
no 3D gold coins, no hooded figures, no matrix green, no rockets, no charts-with-arrows.
Product screenshots: light theme by default, full screens never partial crops, in a
neutral device frame.

Full specs including the pattern tile and screenshot sample data:
`references/layout.md` and `references/imagery.md`

Sticker sizes and cut lines, garment placements, embroidery minimums and printed QR
rules: `references/merch.md`

## Language

Say **Blink** — never "blink" or "BLINK". Say **sats** lowercase. **Bitcoin** capitalized
for the network and protocol, **bitcoin** lowercase for the money. **Lightning**
capitalized. The tagline is **The Everyday Bitcoin Wallet** and is never reworded.

Full always/never word list: `references/terminology.md`

**Voice.** Blink talks in simple, human language, in short sentences, with the limit
said out loud.

- **Attach the limit to the claim, in the same breath.** "Dollar Balance helps reduce
  bitcoin price volatility, but it does not remove all risk." Never a clean claim with
  the caveat hidden elsewhere on the page.
- **Write the first message for someone who knows nothing** — plain words, no unexpanded
  jargon. Put the depth the power user wants behind a **"Learn more"** link, not in the
  paragraph.
- Short declaratives. Second person for the reader, "Blink" for the product, "we" for
  the team. Imperative for anything the reader does.
- **Eyebrow + heading** on every section — a short framing line, then the heading naming
  the thing. Never merge them into one clever headline.
- **Never an exclamation mark in app copy.** On marketing and social they are allowed
  but must not be over-used — never in a heading, a button, or beside a fee or a risk.
- No hype verbs — not "unlock", "unleash", "empower". No "magic", no "just", no
  "newbies", no fear-selling.
- **Say account, not wallet**, for the reader's holdings — one word that works across
  the custodial and non-custodial sides. The tagline is unaffected.
- **Dollar Balance** and **Bitcoin Balance** are the canonical names, in both modes.
  Never "Dollar Account" or "Bitcoin account". **Stablesats** — one capital S — names
  the mechanism behind Dollar Balance in Custodial Mode, never the balance itself.

Derived from live blink.sv copy with the evidence for each rule, plus register by
surface and the open questions: `references/voice.md`

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
- **blink.sv over-uses exclamation marks and hype** — "Unleash the benefits", "Blink
  works its magic", "Try it!". Not the voice. See `references/voice.md`.
- **blink.sv still says "Dollar Account" on older pages.** The canonical names are
  **Dollar Balance** and **Bitcoin Balance**.
- **The app has four blues.** None is the brand blue. Do not sample blue from the app.
- **The app's dark theme inverts `white` and `black` token names** — in dark mode its
  `white` token is `#000000`. Never read raw values out of `colors.ts` without checking.

Full inventory with counts and locations: `references/non-conforming.md`

## Components

Specified in `references/components.md` — ten components reconciled across the Figma
library, `app/components/`, and blink.sv, with **23 flagged conflicts**. Read it before
building any Blink UI.

The three things that catch people out:

- **The entire Figma component library is drawn in dark mode.** Every fill in Figma is a
  dark-mode value. `#FFAD0D` is `primary` in dark, not "the orange". Light-mode component
  values are derived, not designed — there is no light-mode library.
- **Button labels are black, in both themes.** The app's light-mode primary button ships
  white-on-orange at **3.21:1** and fails AA. It does that because the app's dark theme
  inverts the `white` token, not by choice. Black gives 6.54:1.
- **Buttons are pills, inputs are `8`, cards are `16`.** Figma's actual radii run
  `6, 10, 12, 20, 22, 25`; the app adds `50` and `100`. Use the three-value scale.

Quick reference:

| Element | Spec |
|---|---|
| Button, primary | `radius.full`, `primary` fill, **black** label, 700/20px, `14`/`20` padding |
| Button, secondary | `radius.full`, **no border**, transparent, `primary` label |
| Card | `radius.lg` (16), `grey6`, `20` padding |
| Input | `radius.sm` (8), no border at rest, coloured border for error/success |
| Chip / pill | `radius.full`, `5`/`10` padding, 14px |
| Bottom sheet | `radius.lg` top corners only, pull tab `26×3` |
| QR | always on **white**, `28` quiet zone, `radius.lg`, error correction ≥ `M` with a logo |

Still open there: pure black in navigation chrome, and the absence of a canonical amount
component.
