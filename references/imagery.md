# Blink — Imagery

## Photography

Blink's photography is documentary. Real people, using Blink, in real places — largely
El Salvador and the circular economies Blink serves.

### Always

- Real people in real situations, not models in a studio
- Natural light
- Candid, not posed — the moment of paying, receiving, showing someone the app
- Environments that read as everyday: shops, markets, beaches, streets, homes
- A phone visible and in use, where relevant
- Wide enough to show context, not just a screen

### Never

- 3D gold coins, physical bitcoin props
- Hooded figures, dark server rooms, matrix green
- Rockets, moons, bull/bear imagery, charts with arrows
- Generic stock "person smiling at phone" on a white background
- Suits, handshakes, skyscrapers
- AI-generated people

### Treatment

- No heavy filters. No duotone. No orange overlay on faces.
- Crop to `radius.lg` (16px) when placed in a card; square edges when full-bleed.
- Never place body copy directly on a photograph. Use a solid or gradient block.
- If the logo must sit on a photo, use `blink-logo-mono-white.svg` over a calm area.

## Product UI

Screenshots of the app appear constantly in decks and on the site. Treat them as a
controlled asset, not as casual screen grabs.

- **Theme:** light by default. Use dark only when the surrounding surface is dark.
- **Crop:** full screens. Never a partial crop, never a floating fragment of UI.
- **Frame:** a neutral device frame, or no frame at all. Never a stylized 3D perspective
  render, never a drop-shadowed "floating phone".
- **Scale:** never below 320px wide — below that the UI is illegible and looks broken.
- **Multiple screens:** align to a common baseline, equal spacing (`30`), same device
  frame, same theme.
- **Never** stretch, skew, rotate or perspective-transform a screenshot.
- **Never** edit UI text in a screenshot to say something the app does not say.

### Sample data

Use the brand book's established sample account so material stays consistent and no
real user data is exposed:

```
username   satoshin
balance    $245.86
Bitcoin    174,726 SAT   ~ $154.42
Dollar     $69.42
```

Never use real balances, real usernames, real Lightning addresses or real transaction
history in any material that leaves the company.

## Illustration

Blink has no illustration system yet. If illustration is genuinely required:

- Build from the pattern tile's line-icon vocabulary — same stroke weight, same
  geometric construction
- Monochrome or the brand palette only
- Turquoise `#3de8f4` is permitted here, and here is essentially the only place it is

Do not introduce a third-party illustration pack, and do not generate illustration in a
style that has no relationship to the rest of the system.
