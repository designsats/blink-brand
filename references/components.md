# Blink — Components

## Status: OPEN — to be completed in the next session

Component specifications are **not yet written**. This is a known, deliberate gap, not
an oversight.

Do not invent component rules and present them as canonical. If you build a component,
derive it from the tokens and say plainly in your output that the component spec is
provisional.

## Interim guidance

Until the specs exist, build from `SKILL.md` tokens:

| Element | Interim spec |
|---|---|
| Button, primary | `radius.full`, accent fill, **black** label, `10`/`20` padding |
| Button, secondary | `radius.full`, `1px` border, transparent fill, text-color label |
| Card | `radius.lg` (16), `bg.surface`, `20` padding |
| Input | `radius.sm` (8), `1px` border, `10`/`20` padding |
| Chip / tag | `radius.sm` (8), `5`/`10` padding, `small` type |
| Modal | `radius.lg` (16), `bg.default`, `30` padding, one shadow |

Button labels are black, not white — white on orange fails contrast. See
`references/colors.md`.

## What the next session needs to produce

**Sources to reconcile:**

1. **Figma component library** — `node-id=18365-111842` in the Blink Figma file. Many
   components carry descriptions explaining their function. This is the design intent.
   *Blocked: the Figma MCP connector was unauthorized in the session that built this
   skill. Either authorize the claude.ai Figma connector, or export the frames.*
2. **`app/components/` in `blink-mobile`** — 103 component directories. This is the
   shipped reality.
3. **blink.sv Webflow classes** — the web reality.

**Per component, document:**

- Anatomy and required/optional parts
- Sizes offered, and the token values for each
- Every state: default, hover, active, focus, disabled, loading, error
- Light and dark values
- Content rules — label length, sentence case, icon placement
- When to use it, and what to use instead
- Accessibility: hit target (44px minimum), focus ring, contrast

**Priority order** — highest leverage for decks and demos first:

1. Button (primary, secondary, tertiary, destructive, icon-only)
2. Card
3. Input and form field
4. Navigation — top bar, bottom tab bar
5. Modal and bottom sheet
6. Toast and banner
7. List row
8. Badge, chip, pill
9. Amount / currency display — Blink-specific, high value
10. QR code presentation — Blink-specific, high value

**Also still open:** tone of voice (`references/terminology.md`), and the
Dollar vs Stablesats naming question.
