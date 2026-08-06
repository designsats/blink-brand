# Blink — Known Non-Conforming Material

Blink's existing surfaces contain drift. This file exists so that "I copied it from the
website" stops being a defence.

**Do not sample values from these sources.** Take values from `SKILL.md` and
`references/colors.md` only.

Audited 2026-07-25 against: the 2023 brand book PDF, `blink-mobile` (`app/rne-theme/`),
and the live blink.sv Webflow stylesheet.

## blink.sv — Untitled UI purple in production

The site's stylesheet declares a complete third-party Untitled UI palette, and it is
live, not dead code.

| Variable | Value | Uses |
|---|---|---|
| `--untitled-ui-primary600` | `#7f56d9` | 12 |
| `--untitled-ui-primary700` | `#6941c6` | 4 |
| `--untitled-ui-gray900` | `#101828` | 12 |
| `--untitled-ui-gray700` | `#344054` | 10 |
| `--untitled-ui-gray500` | `#667085` | 8 |
| *(+ 6 more gray steps)* | | |

There is also a live purple gradient: `linear-gradient(26.5deg, #6941c6, #53389e)`.

**Purple is not a Blink color.** This is residue from a Webflow template and should be
stripped and replaced with the brand orange and the neutral ramp. Never reproduce it.

## blink.sv — wrong yellow

`--blink-yellow: #ffb32c`. The correct Lightning yellow is `#ffbe0b` (Pantone 123 C).
The delta is small but the site value is not Pantone-matched and does not match the logo.

## blink.sv — unmanaged gradient angles

Five gradient angles are live: `216deg`, `31deg`, `45deg`, `48deg`, `90deg`.
Only `45deg` is correct. Also present: `linear-gradient(#f2f4f7, #fff)` and
`linear-gradient(#00000036, #08070700)`, neither of which is a brand gradient.

## blink-mobile — four blues, none of them the brand blue

| Token | Light | Dark |
|---|---|---|
| `_lightBlue` | `#3553FF` | `#3553FF` |
| `_blue` | `#3050C4` | `#3050C4` |
| `blue5` | `#4453E2` | `#F0F0F7` |

`blue5` in dark mode is `#F0F0F7` — a near-white, not a blue. Likely a bug.

The brand blue `#5D78DA` is not present in the app or on the website. It applies to
brand surfaces only; the app is unchanged for now.

## blink-mobile — inverted `white` and `black` tokens

In `app/rne-theme/colors.ts`, the dark theme defines:

```ts
white: "#000000",
black: "#FFFFFF",
```

The names are inverted relative to their values. **Never read a raw value out of
`colors.ts` and assume the token name describes it.** This is the single most likely
source of an inverted-looking output.

## blink-mobile — spacing drift

The app uses **37 distinct** spacing values. The scale is `3 · 5 · 8 · 10 · 14 · 20 · 30`.

The two largest off-scale offenders:

| Value | Occurrences | Status |
|---|---|---|
| `12` | 82 | Off-scale |
| `16` | 56 | Off-scale |

These are being absorbed over time rather than refactored in one pass. New work uses
the scale.

## blink-mobile — radii drift

The app uses **12 distinct** radii: `2, 8, 10, 12, 13, 16, 20, 22, 24, 30, 50, 100`.
The system has three: `8`, `16`, `999`. The app's `50` and `100` are pill approximations
and map to `999`.

## blink-mobile — type scale not enforced

`theme.ts` defines a clean ladder (24/20/18/16/14/12 at weights 400/600), but actual
usage includes sizes `10, 11, 13, 15, 32, 50` and weights `300, 500, 700, 800`.

## blink-mobile — stray hex literals

Hardcoded outside the theme, in `.tsx` files:
`#E4E9EE`, `#A1CFE6`, `#656565`, `#6200EE`, `#453AA4`, `#229ED9`

`#229ED9` is Telegram's brand blue and is legitimate as a third-party brand color.
`#6200EE` and `#453AA4` are Material Design purples and are not.

## blink-mobile — grey ramp naming

The grey tokens carry comments that contradict their names — `grey0` is annotated
"grey1", `grey4` is annotated "grey8-ish". Use the semantic neutral roles in
`references/colors.md` instead of the raw `greyN` tokens.

## Brand book — legacy language

The 2023 brand book states "ONLY the circle uses gradient" on its Prohibited Usage
page. This refers to the logo's internal construction — the wordmark must not carry a
gradient. It has been misread as forbidding gradient on surfaces, which would forbid
Blink's own landing page. It does not restrict surface use.

The brand book also predates the app's dark theme and contains no dark-mode guidance,
no spacing scale, no radii, and no component specs.

## Logo artwork — its gradient is not the surface gradient

`assets/logo/blink-logo-horizontal.svg` contains a **three-stop** gradient at
approximately **52°**:

| Stop | Value | Nearest documented color |
|---|---|---|
| 0 | `#FEBE13` | Lightning yellow `#ffbe0b` |
| 0.5 | `#EF8B22` | Bitcoin orange `#f18a00` |
| 1 | `#F15822` | Sunset orange `#fb5607` |

The documented surface gradient is **two stops at 45°**: `#ffbe0b → #fb5607`.

Both are correct for their purpose. The logo is fixed artwork and passes through
Bitcoin orange at its midpoint; the surface gradient is a simpler two-stop ramp.

- **Do not "correct" the logo SVG** to match the surface gradient.
- **Do not sample the logo's stops** to build a surface gradient.
- The small deltas (`#FEBE13` vs `#ffbe0b`) are artwork-level and are not palette values.
  Never use `#FEBE13`, `#EF8B22` or `#F15822` as tokens.

The wordmark in the artwork is filled `#010101`, not Venta black `#000000`. This is an
Illustrator artifact and is visually identical. Do not "fix" it, and do not use
`#010101` as a token — Venta black is `#000000`.

## blink.sv — copy drift

Audited 2026-08-06 against the live English marketing site. See `references/voice.md`
for the voice these depart from. The pages rewritten for the custodial / non-custodial
split (`/send-and-receive`, `/security`, `/dollar-balance`) are largely clean; the drift
is concentrated in the older pages.

### Exclamation marks — over-used

Marketing copy may use them; the rule is not to over-use them, and never in a heading, a
button label or next to a fee or a risk. **App copy takes none at all.** The site is well
past the line:

> "Zero fees Blink-to-Blink!" · "Intraledger (between Blink users) – no fee!" ·
> "Lightning Address – like an email for receiving sats!" · "Try it!" ·
> "Start building!" · "Version 2 coming soon!" · "And on, and on!" ·
> "Welcome newbies to grow your circles!" · "Find places to spend sats!"

### Hype language

Concentrated on `/api` and `/circles`:

> "Unlock the power of the Lightning Network quickly and reliably" ·
> "Unleash the benefits of Bitcoin & Lightning" ·
> "in just minutes!" · "Laser-focused on Bitcoin applications" ·
> "the magic of Bitcoin and Lightning" ·
> "the best money on earth (Bitcoin, of course)" *(home)* ·
> "Blink works its magic by automatically boosting your transaction's fee"
> *(`/send-and-receive`)*

### "newbies"

> "Another reason why Blink is a perfect wallet to recommend to newbies." *(`/features`)*
> "Welcome newbies to grow your circles!" *(`/circles`)*

Also `/features`: "The best first bitcoin wallet for newbies".

### Dollar Account — drift against the canonical name

**Dollar Balance** and **Bitcoin Balance** are canonical (`terminology.md`). The site
still uses "Dollar Account" on older pages, and which name appears depends on which page
you are on:

| Page | Nav label | Body usage |
|---|---|---|
| `/`, `/security`, `/send-and-receive`, `/dollar-balance` | Dollar Balance | Dollar Balance |
| `/features`, `/api`, `/circles` | Dollar Account | "dollar account", "Dollar Account" |

`/dollar-balance` already states the rule: *"In both modes, the user-facing feature name
is Dollar Balance."* `/features` still links to `/en/dollar-account` and `/api` still
says "Bitcoin to Dollar account conversions".

Every "Dollar Account" and "Bitcoin account" on the site is drift and should be
retitled. Do not copy either form, and do not write new copy that uses them.

### on-chain vs onchain on the same page

`/send-and-receive` uses both: the heading "On-chain bitcoin payments" and the meta
description "Send and receive bitcoin on Lightning, onchain, and Spark."
`terminology.md` fixes this as **on-chain**.

### "Not your keys, not your coins" vs "not your Bitcoin"

Home page FAQ: *"Not your keys, not your coins – What does it mean?"*
`/security` kicker: *"Not your keys, not your Bitcoin"*

Same aphorism, two forms, no decision recorded.

### Tagline case

Home page H1 renders the tagline sentence case — "The everyday Bitcoin wallet" — while
`terminology.md` and `SKILL.md` fix it as **The Everyday Bitcoin Wallet** (and
`THE EVERYDAY BITCOIN WALLET` in the lockup). The H1 also carries a stray double space.

### /security — duplicated body copy

"Multi-sig cold storage" and "Backup phrase managment" ship the **identical paragraph**
("Blink offers a Lightning wallet backed by reserve cold storage…"). The second section
does not describe backup phrases at all, and its heading is misspelled — "managment".

Do not lift copy from this page.

## Dead assets

- **DM Sans Bold** in `app/assets/fonts/` — referenced nowhere. Not a Blink typeface.
- **Turquoise `#3de8f4`** — specified in the brand book, used nowhere. Retained as a
  limited illustration/data-viz accent only.
