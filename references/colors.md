# Blink — Color

## Brand palette

These four are the brand. They appear in the logo, in print, and on brand surfaces.

| Name | Hex | CMYK | Pantone | Use |
|---|---|---|---|---|
| Bitcoin orange | `#f18a00` | 0 / 54 / 100 / 0 | 144 C | Logo, print, gradient endpoint |
| Sunset orange | `#fb5607` | 0 / 76 / 95 / 0 | Orange 021 C | Gradient endpoint, large fills |
| Lightning yellow | `#ffbe0b` | 0 / 29 / 92 / 0 | 123 C | Gradient endpoint, highlights |
| Venta black | `#000000` | 0 / 0 / 0 / 100 | Process Black | Wordmark, print |

There is no blue and no turquoise in the palette. The brand book's colour pages show
only the oranges, black and the greys — earlier drafts listed a "Blink blue" `#5D78DA`
and a turquoise `#3de8f4`, but `#5D78DA` was only ever the editorial rule on the book's
own "new since 2023" notes, and turquoise appears nowhere. Neither is a Blink colour;
do not use them.

## The gradient

```css
background: linear-gradient(45deg, #ffbe0b, #fb5607);
```

Lightning yellow at the bottom-left, sunset orange at the top-right, on a 45° axis.
This is the only Blink gradient. It is used on the logo's circle mark and on large
brand surfaces — hero sections, title slides, cards, social backgrounds.

- Never change the angle. Never add a third stop. Never reverse it.
- Never place body copy on it. Headline-size text only, and always in Venta black.
- Never use it on small elements — below roughly 200px it reads as flat orange, so
  use a solid color instead.

> The 2023 brand book says "ONLY the circle uses gradient". That is legacy language
> from the logo's creation and refers to the logo's internal construction — the
> wordmark must not carry a gradient. It does not restrict gradient use on surfaces.

## Naming

Use the variable names from `app/rne-theme/colors.ts`. A value looked up in this file
can then be used in code without translation, and a value seen in code can be found
here. Underscore-prefixed names (`_primary1`, `_black`) are the raw palette and never
change with the theme.

## primary — the interaction ramp

Buttons, links, active states, focus rings, selected items. The ramp is **mirrored**
between themes, which is why `primary` in light equals `primary5` in dark.

| Variable | Light | Dark |
|---|---|---|
| `primary` | `#fc5805` | `#ffad0d` |
| `primary3` | `#fd800b` | `#fe990d` |
| `primary4` | `#fe990d` | `#fd800b` |
| `primary5` | `#ffad0d` | `#fc5805` |

`primary` differs from Bitcoin orange `#f18a00` on purpose. Bitcoin orange is the
identity color, used in the logo and in print; `primary` is the interaction color.
Do not substitute one for the other.

## grey0 – grey6

**The number tracks the role, not the lightness.** `grey0` is always the strongest
text and `grey5` is always the ground, which is why the hexes invert between themes
and the names do not. Never pick a grey by how light it looks; pick it by what the
element is.

| Variable | Role | Light | Dark |
|---|---|---|---|
| `grey0` | Primary text | `#3A3C51` | `#FAF9F9` |
| `grey1` | Secondary text | `#393939` | `#E9E8E8` |
| `grey2` | Muted text, placeholders | `#9292A0` | `#CCCCCC` |
| `grey3` | Disabled, hints | `#AEAEB8` | `#949494` |
| `grey4` | Borders and dividers | `#E2E2E4` | `#393939` |
| `grey5` | The ground | `#F2F2F4` | `#1d1d1d` |
| `grey6` | Raised surfaces — cards, sheets | `#E7E7E7` | `#2B2B2B` |

Dark surfaces are `#1d1d1d`, not pure black. Venta black `_black` `#000000` is reserved
for the wordmark and for print. Do not build dark backgrounds out of `#000000`.

Dark mode is **not an inversion**: the dark ground is not black and the dark accent is
a *lighter* orange than the light one. Flipping the light palette produces neither.

## Feedback

| Variable | Hex | Light bg | Dark bg |
|---|---|---|---|
| `error` | `#DC2626` | `error9` `#FEE2E2` | `error9` `#7F1D1D` |
| `warning` | `#F59E0B` | `#FFF9E5` | `#7F1D1D` |
| `_green` (success) | `#00A700` | — | — |

`warning` is never used as text — it fails contrast at every size on white.

## Contrast — the results that change a decision

Measured from the token values. The full table used to live here and in the brand book;
it was more confusing than useful, because only a handful of rows change what you do.
These are those rows.

| Combination | Ratio | Body text |
|---|---|---|
| `warning` `#F59E0B` on white | 2.15:1 | **FAIL at every size** |
| `grey2` on white | 3.07:1 | **FAIL** |
| `primary` `#fc5805` on white | 3.21:1 | **FAIL** |
| `_green` `#00A700` on white | 3.22:1 | **FAIL** |
| White on sunset orange | 3.26:1 | **FAIL** |
| Black on any orange or on the gradient | 6.4–12.6:1 | PASS |

### Rules that follow

1. **Put black on orange, not white.** Every orange surface — buttons, gradient fills,
   hero blocks — takes Venta black text. (A white logo lockup on the gradient is fine;
   a logo is not text.)
2. **Orange text on white is not accessible at body size.** Use `grey0` for body copy
   and reserve orange for headings 24px and above, or for large UI elements.
3. **`warning` is never text.** Use it as a fill or an icon color with a dark label
   beside it.
4. **`grey2` fails body contrast in light mode.** It is for 14px+ secondary labels,
   never for anything a user must read.

## Never

- Never use purple. blink.sv currently ships an Untitled UI purple kit — it is a defect,
  see `non-conforming.md`.
- Never use `#ffb32c`. It is the site's incorrect yellow; the correct one is `#ffbe0b`.
- Never sample a blue from the app. It has four, none of them a Blink colour — blue is
  not a Blink colour at all.
- Never generate tints or shades by lightening or darkening a brand color. If you need a
  lighter surface, use the neutral ramp.
- Never use a color at partial opacity to fake a tint, except for the two documented
  backdrops: `rgba(0,0,0,0.06)` on light, `rgba(255,255,255,0.06)` on dark.
