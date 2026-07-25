# Blink — Layout, Spacing, Shape and Icons

## Spacing scale

```
3   5   8   10   14   20   30
```

These seven values only. For larger gaps, multiply the top of the scale:
`30 → 60 → 90 → 120`.

The ratio is roughly ×1.45, so steps stay visually distinct. Do not interpolate —
there is no 12, no 16, no 24.

### Applying it

| Context | Value |
|---|---|
| Inside a chip, tag or badge | `5` vertical, `10` horizontal |
| Inside an input or button | `10` vertical, `20` horizontal |
| Between label and field | `5` |
| Between related items in a list | `10` |
| Inside a card | `20` |
| Between cards | `20` |
| Between blocks in a section | `30` |
| Between sections | `60` |
| Slide margin (16:9, 1920×1080) | `90` |

Default slide rhythm: `60` between sections, `30` between blocks, `10` within a block.

## Radii

Three values. Nothing else.

| Token | Value | Use |
|---|---|---|
| `radius.sm` | `8px` | Chips, tags, inputs, small cards, code blocks, image thumbnails |
| `radius.lg` | `16px` | Cards, modals, panels, image crops, hero blocks |
| `radius.full` | `999px` | Buttons, pills, avatars, toggles, progress bars |

**Blink buttons are pills.** Always `radius.full`, never `8` or `16`.

Nested corners: when placing an `8` element inside a `16` container, keep both — do not
try to compute a mathematically nested radius.

## Elevation

Blink is a flat brand. Prefer borders and surface color changes over shadows.

When a shadow is genuinely needed (modals, popovers, floating buttons):

```css
/* light */ box-shadow: 0 5px 20px rgba(0,0,0,0.10);
/* dark  */ box-shadow: 0 5px 20px rgba(0,0,0,0.40);
```

One shadow. No layered shadow stacks, no colored shadows, no glow.

## Grid

- Slides: 16:9, 1920×1080, 12 columns, `20` gutter, `90` margin.
- Web: 12 columns, max content width 1200px, `20` gutter.
- Documents: single column, max 75 characters of text.

## Icons

**Phosphor Icons**, Regular weight. Open source (MIT), available as a web font, SVG
set, React package and Figma library.

- Regular weight by default. **Bold** only for emphasis at 16px and below.
- Size icons on the type they sit beside: 16px icon with 14–16px text, 20px with
  20px text, 24px with 24px+.
- Icon color matches the text it labels. An icon is not an opportunity for accent color.
- Never mix icon sets. No Material, no Font Awesome, no Heroicons, no emoji as icons.

### Custom icons

When Phosphor genuinely lacks what you need, draw it to Phosphor's spec so it sits
invisibly alongside the set:

- 256 × 256 viewBox
- 16px stroke weight (Regular) — equals 1.5px at 24px display size
- Round caps, round joins
- Stroke, not fill, unless the Phosphor equivalent is filled
- Align to the same optical bounds — Phosphor glyphs sit in roughly a 224px optical box

Custom icons go in the brand asset library, not inline in one deck.

### Legacy icon sets

The app also contains `react-native-vector-icons` and a local `icons-redesign` SVG set,
and the brand book has a decorative line-icon pattern. These are **legacy**. Do not
extend them and do not use them on brand surfaces.

## Pattern tile

The scattered line-icon pattern (bitcoin, lightning, pin, phone, key, QR, chart) is a
decorative background for dark surfaces.

- Dark surfaces only, at low contrast — the pattern should be felt, not read.
- Never behind body copy. Title slides, section dividers and covers only.
- Never recolor it to a brand color. It stays a subtle grey on `#1d1d1d`.
- Never scale it so large that individual icons become focal points.
