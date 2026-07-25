# Blink — Color

## Brand palette

These five are the brand. They appear in the logo, in print, and on brand surfaces.

| Name | Hex | CMYK | Pantone | Use |
|---|---|---|---|---|
| Bitcoin orange | `#f18a00` | 0 / 54 / 100 / 0 | 144 C | Logo, print, gradient endpoint |
| Sunset orange | `#fb5607` | 0 / 76 / 95 / 0 | Orange 021 C | Gradient endpoint, large fills |
| Lightning yellow | `#ffbe0b` | 0 / 29 / 92 / 0 | 123 C | Gradient endpoint, highlights |
| Blink blue | `#5D78DA` | — | — | Brand surfaces only |
| Venta black | `#000000` | 0 / 0 / 0 / 100 | Process Black | Wordmark, print |

Turquoise `#3de8f4` (Pantone 3105 C) is a **limited accent**. Allowed in illustration
and data visualization only. Never on UI, never on type, never as a background, never
on a button.

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

## UI accent

The interactive color. Buttons, links, active states, focus rings, selected items.

| Mode | Hex |
|---|---|
| Light | `#fc5805` |
| Dark | `#ffad0d` |

This differs from Bitcoin orange `#f18a00` on purpose. Bitcoin orange is the identity
color; the accent is the interaction color. Do not substitute one for the other.

## Neutrals

| Role | Light | Dark |
|---|---|---|
| `bg.default` | `#FFFFFF` | `#1d1d1d` |
| `bg.surface` | `#F2F2F4` | `#2B2B2B` |
| `bg.raised` | `#E7E7E7` | `#393939` |
| `text.primary` | `#1d1d1d` | `#FAF9F9` |
| `text.secondary` | `#3A3C51` | `#E9E8E8` |
| `text.muted` | `#9292A0` | `#949494` |
| `border` | `#E2E2E4` | `#393939` |

Dark surfaces are `#1d1d1d`, not pure black. Venta black `#000000` is reserved for the
wordmark and for print. Do not build dark backgrounds out of `#000000`.

## Feedback

| Role | Hex | Light bg | Dark bg |
|---|---|---|---|
| Error | `#DC2626` | `#FEE2E2` | `#7F1D1D` |
| Warning | `#F59E0B` | `#FFF9E5` | `#7F1D1D` |
| Success | `#00A700` | — | — |

## Contrast — measured, not assumed

Verified WCAG 2.1 ratios. **Several obvious-looking choices fail.**

| Combination | Ratio | Body text | Large text (≥24px) |
|---|---|---|---|
| `#1d1d1d` on white | 16.86:1 | PASS | PASS |
| `#FAF9F9` on `#1d1d1d` | 16.04:1 | PASS | PASS |
| `#3A3C51` on white | 10.80:1 | PASS | PASS |
| Black on Lightning yellow | 12.62:1 | PASS | PASS |
| Black on turquoise | 14.05:1 | PASS | PASS |
| Black on Bitcoin orange | 8.38:1 | PASS | PASS |
| Black on sunset orange | 6.44:1 | PASS | PASS |
| `#949494` on `#1d1d1d` | 5.56:1 | PASS | PASS |
| Error `#DC2626` on white | 4.83:1 | PASS | PASS |
| Blink blue `#5D78DA` on white | 4.07:1 | **FAIL** | PASS |
| White on Blink blue | 4.07:1 | **FAIL** | PASS |
| White on sunset orange | 3.26:1 | **FAIL** | PASS |
| Success `#00A700` on white | 3.22:1 | **FAIL** | PASS |
| Accent `#fc5805` on white | 3.21:1 | **FAIL** | PASS |
| `#9292A0` on white | 3.07:1 | **FAIL** | PASS |
| Warning `#F59E0B` on white | 2.15:1 | **FAIL** | **FAIL** |

### Rules that follow from the table

1. **Orange text on white is not accessible at body size.** Use `#1d1d1d` for body copy
   and reserve orange for headings 24px and above, or for large UI elements.
2. **Put black on orange, not white.** White on sunset orange fails. Every orange
   surface — buttons, gradient fills, hero blocks — takes Venta black text.
   The brand book's white-on-gradient logo lockup is fine because a logo is not text.
3. **Warning `#F59E0B` is never text.** It fails at every size on white. Use it as a
   fill or an icon color with a dark label beside it.
4. **`text.muted` in light mode fails body contrast.** It is for 14px+ secondary labels
   on a case-by-case basis, never for anything a user must read.
5. **Blink blue needs 24px+** in either direction. Do not set body copy in it.

## Never

- Never use purple. blink.sv currently ships an Untitled UI purple kit — it is a defect,
  see `non-conforming.md`.
- Never use `#ffb32c`. It is the site's incorrect yellow; the correct one is `#ffbe0b`.
- Never sample a blue from the app. It has four, none of them the brand blue.
- Never generate tints or shades by lightening or darkening a brand color. If you need a
  lighter surface, use the neutral ramp.
- Never use a color at partial opacity to fake a tint, except for the two documented
  backdrops: `rgba(0,0,0,0.06)` on light, `rgba(255,255,255,0.06)` on dark.
