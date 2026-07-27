# Blink — Stickers and merch

Physical production. Every rule here exists because a specific job came back wrong.

## Stickers

The one place the mark travels alone at scale, and the one place the die-cut shape does
design work.

| Shape | Size | Artwork |
|---|---|---|
| Circle | 50mm | The mark alone, cut to the circle. The default sticker |
| Circle, gradient | 50mm | `blink-logo-mono-white.svg` on the gradient |
| Rounded square | 55mm at radius 16 | Mark on black, or the lockup |
| Horizontal | 75 × 25mm | The lockup, clear space `x` inside the cut |

**Minimums:** never below 40mm for the mark, 60mm for the lockup. The circle's stroke
closes up on vinyl well before it does on screen.

**The cut line is an element.** It sits outside the safe zone, which means the clear
space is built into the sticker rather than trimmed away. A lockup running to the edge
of the die is a reprint.

**Production**
- Supply vector with the cut path on its own layer named `CutContour`.
- 3mm bleed on anything that is not white — the gradient especially.
- Matte vinyl for the black and gradient stickers; gloss blows out the circle.
- Confirm the gradient on a printed proof. Four-colour process shifts it warm.

## Garments

One mark, one size, one position per garment. A front print and a back print are two
placements of the same mark, not two different marks.

| Item | Placement | Size |
|---|---|---|
| T-shirt | Centre chest | 200mm |
| T-shirt | Left chest | 80mm |
| Hoodie / tee | Centre back | 260mm |
| Cap | Front panel | 50mm, mark only |

- **Embroidery** — minimum 60mm wide. Below that the circle's stroke closes up. Prefer
  the mono lockup.
- **Screen print** — the gradient needs at least a four-colour process. On a two-colour
  job use `blink-logo-mono-white.svg`.
- Never place the lockup across a seam, zip or pocket edge.
- Always supply the vector. Never send a PNG lifted from a deck to a printer.

## Curved surfaces — cups

Wrapping the lockup around a cup distorts it: curvature is a proportion change. Keep the
artwork inside the flat ~40% of the wrap, or use the mark alone. Never run the lockup
across the handle seam.

## Printed QR codes

Always **black on white**. Never inverted, never on the gradient, never tinted.
Reproduce at no less than 250px equivalent with a 28px quiet zone. If a logo sits in the
centre, error correction never drops below `M`.

**Never print a decorative QR.** Someone will always try to scan it. Every code that
appears in Blink material resolves to something real.
