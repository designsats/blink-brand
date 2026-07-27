# Blink Brand — Claude Skill

Makes Claude produce on-brand Blink material: decks, landing pages, social cards,
one-pagers, demos, diagrams and internal tools.

## Install

Clone this repo into your Claude skills directory:

```bash
# macOS / Linux
mkdir -p ~/.claude/skills
git clone https://github.com/designsats/blink-brand.git ~/.claude/skills/blink-brand
```

Restart Claude Code (or start a new session). That's it.

To check it loaded, type `/blink-brand` — or just ask for something Blink-branded and
Claude will pick it up automatically.

## Use

You don't need to know the system. Ask normally:

- "Make me a 6-slide deck on our Q3 numbers"
- "Build a landing page for the merchant program"
- "Design three social cards announcing Lightning addresses"
- "Is this deck on-brand?" *(paste or attach it)*
- "What's our orange?"

Claude loads the rules itself and will tell you when something you asked for conflicts
with the brand.

## What's inside

```
SKILL.md                    the core rules — always loaded
blink-brand.html            the brand book, one self-contained page
references/
  colors.md                 palette, gradient, dark mode, measured contrast
  typography.md             both type systems and when to use each
  logo.md                   assets, clear space, every prohibited use
  layout.md                 spacing, radii, grid, icons, pattern tile
  imagery.md                photography and product-screenshot rules
  merch.md                  stickers and physical production
  terminology.md            controlled word list
  non-conforming.md         known drift — do not copy from these sources
  components.md             buttons, inputs, cards, nav — Figma vs shipped app
assets/
  tokens.json               machine-readable source of truth
  logo/                     the approved SVGs, incl. print and seasonal
templates/
  deck.html                 16:9 slide deck, light/dark
  social.html               square, story and wide cards
  onepager.html             memo / report, light/dark
```

Templates are plain HTML. Open in a browser, then print to PDF or screenshot.
They need no build step and no internet beyond the Google Fonts link.

## The brand book

`blink-brand.html` is the human-readable brand book — every page A4, fonts and images
embedded, no network calls. Open it in a browser and print to PDF.

It is generated, not hand-written, and each page is a fixed box that content silently
overflows. Before republishing it, open it with `?audit` appended to the URL: a `<pre>`
at the top reports every page that overflows, or `AUDIT CLEAN`.

## Known gaps

- **Tone of voice is TBD.** Claude will write plainly and won't invent a voice.
- **Dollar vs Stablesats naming is unresolved.**
- **Light-mode primary button fails contrast** — see `references/components.md`.

## Keeping it current

`assets/tokens.json` is the source of truth. If a value changes, change it there first,
then update `SKILL.md` and the relevant reference file to match.

Questions or corrections: Andrej (design).
