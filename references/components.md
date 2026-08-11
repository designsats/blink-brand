# Blink — Components

Specified 2026-07-25 by reconciling three sources:

1. **Figma** — `Components` canvas (`37:4625`) in the Blink file `9MQuQi8ZhXVvDibWSI3C4c`,
   annotation block at `node-id=18365-111842`. Component descriptions are quoted verbatim
   below as **Intent**. This is the design intent and outranks the other two on *what a
   component is for*.
2. **`app/components/`** in `blink-mobile` — 103 directories, 14 of them under
   `app/components/atomic/` which mirrors Figma's "Atomic components" section
   one-for-one. This is the shipped reality and outranks the others on *what users see today*.
3. **blink.sv** Webflow stylesheet (`blink-sv.webflow.shared.21898ddb8.css`). This is the
   web reality and outranks nothing — see `references/non-conforming.md`.

---

## Read this before you use any value below

**The entire Figma component library is drawn in dark mode.** Every fill, label and border
in Figma is a *dark-mode* value: `#FFAD0D` is the dark accent, `#1D1D1D` is the dark
background, `#393939` is dark `bg.raised`. There is no light-mode component library in
Figma. Only the `info` component has an explicit `theme=light` variant.

Consequences you must not get wrong:

- **Do not read a Figma fill as a universal value.** `#FFAD0D` on a button is
  `accent.dark`; the light-mode equivalent is `accent.light` `#fc5805`.
- **Light-mode component values below are derived**, not measured from Figma. They are
  marked *(derived)* wherever that is the case.
- Figma shows **no hover state anywhere** — it is a mobile library. Hover is specified
  below for brand/web surfaces only and is derived.

**Where the three sources disagree, both readings are given and the conflict is flagged
`⚠ CONFLICT`. Nothing has been silently reconciled.** There are 23 flagged conflicts.

**Scale drift is pervasive.** Figma components use radii `6, 8, 10, 12, 16, 20, 22, 25`
and paddings `4, 5, 6, 7, 8, 11, 12, 13, 14, 20, 24, 28`. The system has three radii
(`8/16/999`) and seven spacings (`3/5/8/10/14/20/30`). Each component notes its
off-scale values. **For new brand surfaces use the system scale**; the drift is recorded
so you recognise it in existing screens, not so you reproduce it.

---

## 1. Button

Five distinct components, not one component with five variants. Figma keeps them separate
and so does the app.

### 1.1 button-primary — the main CTA

**Intent** (Figma `18365:111836`): *"Main CTA in 4 states: default, pressed, disabled and
loading"*

**Anatomy** — pill container → label (required) → optional leading icon. Fills its
container width. One primary button per screen.

| Property | Figma (dark) | Light (derived) |
|---|---|---|
| Fill | `#FFAD0D` `accent.dark` | `#fc5805` `accent.light` |
| Label | `#000000` | `#000000` |
| Type | Source Sans Pro **700** · 20px / 1.2em | same |
| Padding | `13px 20px` *(13 off-scale → use `14`)* | `14px 20px` |
| Radius | `25px` → `radius.full` | `radius.full` |
| Gap (icon↔label) | `10px` | `10px` |
| Width | fill container | fill container |

**States**

| State | Figma | Notes |
|---|---|---|
| default | fill `#FFAD0D`, label `#000000` | |
| hover | *not in Figma* | Brand surfaces only: darken fill 8%, no lift |
| pressed | `rgba(0,0,0,0.15)` overlay on `#FFAD0D` | a black scrim, not a colour swap |
| focus | *not in Figma* | see Accessibility below |
| disabled | fill `#FFAD0D` @ `opacity 0.5`, label `#1D1D1D` @ `0.5` | whole button dimmed |
| loading | fill `#FFAD0D`, label replaced by 20×20 spinner | label is removed, not overlaid |

⚠ **CONFLICT — loading spinner colour.** Figma fills the spinner `#FFFFFF` on `#FFAD0D`
(**1.87:1, fails**) while the label on the same button is `#000000` (11.24:1). The spinner
should be `#000000`. Figma is wrong here; do not copy it.

⚠ **CONFLICT — label colour in light mode.** The app sets the label to `colors.white`
([galoy-primary-button.tsx:29](app/components/atomic/galoy-primary-button/galoy-primary-button.tsx#L29)).
Because the app's dark theme **inverts the `white` token** (`white: "#000000"`, see
`references/non-conforming.md`), this resolves to:

- dark mode → `#000000` on `#ffad0d` = **11.24:1**, correct, matches Figma
- light mode → `#FFFFFF` on `#fc5805` = **3.21:1**, **fails AA for 20px text**

So the shipped light-mode primary button fails contrast, and it does so *because* of the
inverted token, not by choice. Black would give **6.54:1**. `SKILL.md` already says button
labels are black; Figma agrees; only the light-mode app disagrees. **Use black.**

⚠ **CONFLICT — font weight.** Figma `700`; app `600`
([galoy-primary-button.tsx:28](app/components/atomic/galoy-primary-button/galoy-primary-button.tsx#L28)). Use **700**.

⚠ **CONFLICT — radius.** Figma `25px` (a pill at that height). The app sets no radius and
inherits the RNE default. The web's `.button` is `30px`. All three are pill-ish but none
is `999`. **Use `radius.full`.**

⚠ **CONFLICT — height.** App `minHeight: 50`; Figma computes to `13+13+24 = 50`. These
agree — but only by coincidence, since the app never states the padding. Keep `50` as the
minimum and meet it with padding, not a fixed height.

**Content rules** — sentence case. Verb first: "Send bitcoin", not "Bitcoin sending".
One to three words; never wrap to a second line. No terminal punctuation. Never "Click
here" or "Submit".

**Use when** — the single most important action on the screen. **Instead:** more than one
equally-weighted action → `CTA-button-group`; a reversible or minor action →
button-secondary; an action inside a row → button-tertiary.

### 1.2 button-secondary — the paired alternative

**Intent** (`18365:111837`): *"Secondary CTA in 3 states: default, pressed, disabled"*

| Property | Figma (dark) | Light (derived) |
|---|---|---|
| Fill | none (transparent) | none |
| Border | **none** | none |
| Label | `#FFAD0D` 20px/700 | `#fc5805` |
| Padding | `13px 24px` *(both off-scale)* | `14px 20px` |
| Radius | `25px` → `radius.full` | `radius.full` |

**States** — default; pressed: label → `#805606`; disabled: `opacity 0.7`.

⚠ **CONFLICT — the previous interim guidance was wrong.** The superseded note in this file
said secondary = "1px border, transparent fill". **Figma and the app both ship no border.**
It is a text button. That interim line is retracted.

⚠ **CONFLICT — pressed label contrast.** `#805606` on `#1d1d1d` = **2.61:1**, fails.
Prefer `opacity 0.7` on the default label for the pressed state.

⚠ **CONFLICT — disabled opacity.** Figma `0.7`; app `0.35`
([galoy-secondary-button.tsx:60](app/components/atomic/galoy-secondary-button/galoy-secondary-button.tsx#L60)). Use **0.5**, matching primary.

**Note** — the app adds a `grey` prop that recolours the label to `colors.grey3`. Figma has
no such variant.

**Use when** — the alternative to a primary, in a pair. Never alone.

### 1.3 button-tertiary — the inline action

Two axes in Figma: `State` × `Filled`.

| | Filled=true | Filled=false |
|---|---|---|
| Fill | `#FFAD0D` | transparent |
| Label | `#000000` | `#FFAD0D` |
| Padding | `6px 20px` | `6px 14px` |
| Pressed | `rgba(0,0,0,0.15)` scrim | fill → `#1D1D1D` |
| Disabled | `opacity 0.7`, label `#1D1D1D` | `opacity 0.5` |

Type `14px / 700`, radius `20px`. Height ≈ `6+6+20 = 32px`.

⚠ **CONFLICT — radius.** Figma `20px`; app `50`
([galoy-tertiary-button.tsx:98](app/components/atomic/galoy-tertiary-button/galoy-tertiary-button.tsx#L98)). At 32px tall both read as a
pill. Use `radius.full`.

⚠ **CONFLICT — variant count.** The app has **three** modes — default (filled), `outline`
(1.5px border, label `colors.black`), `clear` (no padding, bold label). Figma has **two**
(`Filled` true/false) and **no outline variant at all**. The app's `outline` is undesigned.

⚠ **ACCESSIBILITY — fails hit target.** 32px tall, and `clear` has zero padding. Both are
below 44px. Wrap in a 44px-tall touch container.

### 1.4 icon-button

| Size | Box | Radius | Icon | 44px target |
|---|---|---|---|---|
| large | `44 × 44` | `22px` | 32 | ✅ |
| medium | `32 × 32` | `16px` | 20 | ❌ |
| icon only | `30 × 30` | `16px` | 20 | ❌ |
| small | hug + `2px` | `16px` | 16 | ❌ |

Fill `#393939` (`bg.raised` dark). Pressed `#1D1D1D`. Disabled `opacity 0.7`.
**`state=frozen`** fills `#7F1D1D` (dark `error-bg`) — used for a frozen card.

⚠ **CONFLICT — radius.** App uses `8`
([galoy-icon-button.tsx:160](app/components/atomic/galoy-icon-button/galoy-icon-button.tsx#L160)); Figma `16`.

⚠ **CONFLICT — the app has no `large` variant.** It hardcodes `32 × 32`, so the only
size that meets the 44px hit target does not exist in code.

⚠ **CONFLICT — fill.** App `colors.grey5` (`#F2F2F4` light / `#1d1d1d` dark), pressed
`grey4`. Figma `#393939`. Different ramp steps.

### 1.5 button-field — a field that acts as a button

**Intent** (`18365:111839`): *"Full length row, always with an icon aligned right"*

Not a pill. `radius 8`, fill `#1D1D1D`, label `#FFAD0D` **14px/700 left-aligned**, 16px
icon right, `padding 8px 20px`, `gap 8`, width `312`.
Pressed fill `#2B2B2B`; disabled `opacity 0.5` with label `#BDBDBD`.

⚠ **CONFLICT — padding.** App `8px 12px`
([galoy-button-field.tsx:61-62](app/components/atomic/galoy-button-field/galoy-button-field.tsx#L61-L62)); Figma `8px 20px`.

⚠ **CONFLICT — disabled opacity.** App `0.3`; Figma `0.5`.

⚠ **CONFLICT — the app has an error state Figma lacks** (`backgroundColor: colors.error9`).

**Use when** — a settings or KYC row that opens another screen. **Instead:** a row that
only displays a value → list row; a real text entry → input.

### 1.6 Slider button — deliberate friction

**Intent** (`18365:111841`): *"Breaks the pattern of a simple button to create friction and
signify unreversible step"*

Ships as `app/components/atomic/galoy-slider-button/`. **Use only for irreversible
actions** — sending a payment, revealing a seed phrase. Never as a convenience control,
and never where a normal button would do. This is the one component whose whole purpose is
to be harder to use than the alternative.

---

## 2. Card

Figma has four card-ish components — `card` (`7474:53945`), `card-wrapper`
(`7486:56132`), `card-offer` (`7486:56467`), `visa-card` (`2393:18783`) — plus
`bulletin-row`. There is **no single generic card component** in either Figma or the app.

**Baseline for new work** (from `SKILL.md`, not measured from Figma):

| Property | Light | Dark |
|---|---|---|
| Fill | `bg.surface` `#F2F2F4` | `bg.surface` `#2B2B2B` |
| Radius | `radius.lg` `16px` | same |
| Padding | `20px` | same |
| Border | none | none |
| Shadow | `0 5px 20px rgba(0,0,0,0.10)` | `0 5px 20px rgba(0,0,0,0.40)` |

⚠ **CONFLICT — the app uses `12` almost everywhere.** `wallet-overview` uses
`borderRadius: 12, padding: 12`
([wallet-overview.tsx:291-292](app/components/wallet-overview/wallet-overview.tsx#L291-L292)); Figma's `bottom-sheet` inner blocks and
`wallet-summary-2026` also use `12`. `12` is off both the radius scale and the spacing
scale, and it is the single most common off-scale value in the app (82 occurrences).
**New work uses `16`.** Do not "fix" existing screens in passing.

**Never** stack shadow + border + fill together — pick one elevation cue.

---

## 3. Input and form field

**Intent** (`18365:111846`): *"Basic input, can work as a button and open other
screens/popups/contexts or be a direct-fill input. We use colored border for success/error
states"*

**Anatomy** — container → optional leading label → text → optional trailing icon (16px).

| Property | Figma (dark) | Light (derived) |
|---|---|---|
| Fill | `#1D1D1D` | `#F2F2F4` |
| Radius | `8px` `radius.sm` | same |
| Padding | `5px 10px 5px 14px` | same |
| Gap | `12px` *(off-scale → `14`)* | `14px` |
| Text | Source Sans Pro 700 · 14px | same |
| Text colour | `#FFFFFF` | `#1d1d1d` |

**States**

| State | Treatment |
|---|---|
| default | fill only, no border |
| hover | *not in Figma* — brand surfaces: border `1px` `border` token |
| focused | fill → `#2B2B2B`. **No border, no ring.** |
| success | `1px` `#00A700` border |
| error | `1px` `#DC2626` border |
| disabled | `opacity 0.5` |
| loading | not specified |

⚠ **CONFLICT — focus is not visible enough.** Figma signals focus with a background
change of `#1D1D1D → #2B2B2B`, a **1.19:1** difference. That is invisible to most users and
fails WCAG 2.4.7 on any keyboard-navigable surface. On the app's touch surface it is
survivable; **on web and in decks, add a real focus ring** (see Accessibility).

⚠ **CONFLICT — success/error carry colour only.** A 1px colour border is the sole error
signal. Always pair it with an icon and text; never rely on the border alone.

**Content rules** — label above, sentence case, no colon. Placeholder is an *example*
(`you@example.com`), never a restatement of the label. Error text is specific and tells
the user what to do: "Enter an amount above 1 sat", not "Invalid input".

---

## 4. Navigation

### 4.1 Bottom tab bar

Figma `bottom-bar` (`622:9204`) — four types: `Default`, `2026`, `card`, `academy`.

| Property | Figma |
|---|---|
| Size | `360 × 73` |
| Fill | `#000000` |
| Top border | `1px` line, full width |
| Padding | `0 8px` |
| Item width | `78.75` (4 tabs) |
| Icon | `24 × 24` |
| Label | Source Sans Pro **600** · 12px / 1.5em |
| Active | `#FFAD0D` (11.24:1 on black) |
| Inactive | `#BDBDBD` (11.18:1 on black) |
| Icon↔label gap | `4px` |

⚠ **CONFLICT — the tab bar is pure black, not the dark background.** `#000000` vs
`bg.default` dark `#1d1d1d`. `SKILL.md` reserves `#000000` for the wordmark and print, and
`tokens.json` says explicitly *"Not pure black. #000000 is reserved for the wordmark and
print."* The tab bar breaks that rule. Both Figma `bottom-bar` and Figma `bottom-sheet` do.
**Unresolved — this needs a decision:** either the tab bar moves to `#1d1d1d`, or the
token description gets an explicit navigation-chrome exception. Do not pick one silently.

⚠ **CONFLICT — tab count.** `Default` = 4 tabs; `2026` = **5** (Home / People / Próspera /
Map / Academy) built from `icon-button size=medium` with text. Five tabs at 360px gives
72px per tab. The app ships 4.

⚠ **CONFLICT — `#BDBDBD`.** Present in Figma and as `--grey2-dark` on blink.sv, but the
app's dark `grey2` is `#CCCCCC`. Three sources, two values.

Tab height `73 − 8 = 65px` ✅ exceeds 44px.

### 4.2 Top bar / header

Figma `header` (`38:13714`), app `header-back-control` and `header-close-control`.
Anatomy: back or close control left (44×44), title centred, optional action right.
Title Source Sans Pro 600 · 18px. Fill matches screen background; no border, no shadow.
Use `icon-button size=large` for both side controls so they meet 44px.

---

## 5. Modal and bottom sheet

### 5.1 Bottom sheet — the default

Figma `bottom-sheet` (`4203:24713`), states `Default` / `default` / `empty` / `filled`.

| Property | Figma |
|---|---|
| Radius | `20px 20px 0 0` |
| Fill | `#000000` |
| Top border | `1px` `#393939` |
| Padding | `30px 20px 80px` |
| Gap | `14px` |
| Width | `360` (full bleed) |
| Pull tab | `26 × 3`, radius `2`, `#949494`, `11px` from top |

The `80px` bottom padding is home-indicator clearance, not a design choice — keep it.

⚠ **CONFLICT — radius `20`** vs system `16`. ⚠ **CONFLICT — fill `#000000`** — same issue
as the tab bar above.

### 5.2 Popup modal

Figma `popup-modal` (`5556:30904`), app `custom-modal`. Centred, `radius.lg 16`,
`bg.default`, `30px` padding, one shadow, backdrop `rgba(0,0,0,0.06)` light /
`rgba(255,255,255,0.06)` dark.

**Use a bottom sheet** for anything the user chooses from or fills in — it is the Blink
default and reachable one-handed. **Use a popup modal** only for a blocking confirmation
that must interrupt. The app has ~15 bespoke modal components
(`stablesats-modal`, `invite-modal`, `set-default-account-modal`, …); prefer composing
`custom-modal` over adding a sixteenth.

---

## 6. Toast and banner

### 6.1 info box

**Intent** (`18365:111844`): *"Not active info box"* — informational, never interactive.

Figma `info` (`6209:26293`) — three themes, and this is the **only Figma component with a
real light variant**.

| Theme | Fill | Left border `2px` | Text |
|---|---|---|---|
| dark | `#1D1D1D` | `#FFFFFF` | `#FFFFFF` |
| light | `#F2F2F4` | `#4453E2` | `#4453E2` (5.24:1 ✅) |
| notification | `#F2F2F4` | `#00A700` | `#000000` |

Radius `6px`, padding `10px 10px 10px 14px`, width `316`, text 12px/400.

⚠ **CONFLICT — radius `6px` is off-scale** and is the only `6` in the library. Use `8`.

⚠ **CONFLICT — `#4453E2` is not a Blink color.** It is the app's `blue5` light value, a
fourth app blue. Blue is not a Blink color at all, so this info box has no on-brand fill —
flag it for redesign. See `references/non-conforming.md` — "the app has four blues".

⚠ **CONFLICT — bar width.** Figma `2px`; app `3px`
([galoy-info.tsx:54](app/components/atomic/galoy-info/galoy-info.tsx#L54)). ⚠ Padding also differs: app `8px / 6px` vs Figma `10px / 14px`.

⚠ **CONFLICT — the app's bar colour is `warning` or `blue5`** ([galoy-info.tsx:57](app/components/atomic/galoy-info/galoy-info.tsx#L57)),
so it ships a warning variant Figma does not have. And `warning` `#F59E0B` is **2.15:1** on
white — fine as a 2px bar, but `tokens.json` forbids it as text. Keep it decorative.

### 6.2 error box

Figma `error-box` (`38:13637`); app `galoy-error-box`: radius `8`, padding `8px 6px`, fill
`colors.error9`. Text `#DC2626` (4.83:1 on white ✅).

### 6.3 Banners

The app ships `info-banner`, `warning-banner`, `network-status-banner`,
`unclaimed-deposit-banner`, `backup-nudge-banner` — full-bleed, no radius, above content.
Figma has `bulletin-row` (`7460:43003`) instead. ⚠ **CONFLICT — these are the same idea
under two names in two shapes**, and the app's five banners have no shared base component.

**Content rules** — one sentence. State what happened and what to do. Never stack two
banners; if two conditions are true, show the more severe.

---

## 7. List row

**Intent** (`18365:111845`): *"Universal row item for menu items, context menus"*

Figma `list-item` (`955:13601`), states `Default` / `active`.

| Property | Figma |
|---|---|
| Radius | `8px` |
| Padding | `14px 10px 14px 14px` |
| Gap | `10px` |
| Icon | `16 × 16` |
| Text block | `262px` wide |
| active | fill `#1D1D1D` + `1px` `#FFAD0D` border |

Height `14 + 16 + 14 = 44px` ✅ — exactly the hit target. **Do not reduce the vertical
padding below 14px**; that is the whole margin of safety.

### Separator

**Intent** (`18365:111835`): *"Separates items in list. We have two lengths"*

Figma `Line` (`5580:23164`), variants `long` / `short`. `1px`, `border` token.
**Long** = full bleed, separates groups. **Short** = inset to the text column (past the
icon), separates items within a group. Never both in one list.

⚠ See `references/settings_group_null_filter.md` in project memory — settings rows must
return `null` at top level or you get phantom rows *and phantom dividers*.

---

## 8. Badge and chip

### 8.1 Badge

**Intent** (`18365:111840`): *"Dynamic width"*

Figma `Badge` (`5924:15717`) — one state only. Fill `#393939`, label `#E9E8E8`
(9.44:1 ✅), radius `12px`, padding `4px 10px`, type **10px / 700**.

⚠ **CONFLICT — 10px type.** Below the product scale floor (12px) and far below the brand
floor (14px). `SKILL.md`: *"Body copy never below 14px."* **On brand surfaces render
badges at 14px.** 10px is app-only, and only for a count.

⚠ **CONFLICT — radius `12`** is off-scale. For a 22px-tall badge use `radius.full`.

Related: `notification-badge` and `unseen-tx-amount-badge` in the app; `status-pill`.

### 8.2 currencyPill — Blink-specific

**Intent** (`18365:111842`): *"Indication or switch button to switch between balance types
(Bitcoin, Dollar, Card). Also used in ghost style for currency switch (USD,EUR,CZK,...)"*

Figma `currencyPill` (`835:13974`) — five variants. Radius `10px`, type 14px/700.

| Variant | Fill | Label | Contrast | Size |
|---|---|---|---|---|
| Bitcoin | `#FFAD0D` | `#000000` | 11.24:1 ✅ | `60 × 30` |
| Dollar | `#00A700` | `#FFFFFF` | 3.22:1 ⚠ | `60 × 30` |
| Card | `#393939` | `#FFFFFF` | 11.55:1 ✅ | hug, `5px 11px` |
| All | transparent, `1px #FFAD0D` | `#FFAD0D` | 9.02:1 ✅ | hug, `5px 10px` |
| display | transparent, `1px #E9E8E8` | `#E9E8E8` 16px/700 | 13.79:1 ✅ | `52` wide, `4px 11px` |

The `display` variant is the ghost style the annotation describes — it holds a fiat ticker
(`CZK`, `USD`, `EUR`) and is the one variant that is *not* an account type.

⚠ **CONFLICT — Dollar at 3.22:1 fails AA for 14px text.** White on `#00A700` is legible
only at large sizes. Darken the green or use `#000000` (which gives 6.6:1). This is the
worst-failing pair that ships in a *labelled, meaningful* colour.

⚠ **CONFLICT — radius `10`** off-scale; at 30px tall it should be `radius.full`.

⚠ **ACCESSIBILITY — `60 × 30` fails the 44px hit target** when the pill is a switch, which
the annotation says it is. Give it a 44px touch container.

⚠ **The green Dollar pill is the only place a feedback colour is used as an identity
colour.** `#00A700` is `feedback.success` everywhere else. A green pill that means
"Dollar account" and a green bar that means "success" in the same app is a collision.
Flagged, not resolved.

> **SETTLED — Dollar Balance and Bitcoin Balance.** The user-facing names are
> **Dollar Balance** and **Bitcoin Balance**, in both modes. Figma labels the variant
> `Dollar` and the app has `stablesats-modal`, `usd-convert-to-btc-modal` and
> `dollar-balance-migration-modal` side by side — internal identifiers may stay as they
> are, but **every user-visible string reads Dollar Balance**. Stablesats names the
> mechanism, never the balance. See `references/terminology.md`.

---

## 9. Amount / currency display — Blink-specific

The highest-value and least consistent area. Four overlapping Figma components
(`wallet-overview`, `wallet-summary`, `wallet-summary-2026`, `display-currency-input`) and
nine app directories (`amount-input`, `amount-input-screen`, `currency-input`,
`currency-keyboard`, `input-payment`, `transfer-amount-input`, `receive-amount-row`,
`balance-header`, `wallet-summary`).

### 9.1 wallet-switch / wallet-summary-2026

**Intent** (`18365:111843`): *"Used to switch between Bitcoin/Dollar account in Send flow."*

Figma `wallet-summary-2026` (`6653:35703`) — `variant` (bitcoin/dollar) ×
`alignment` (left/right) × `state` (Default/disabled).

| Property | Figma |
|---|---|
| Title ("From") | Source Sans Pro 400 · 14px, `#FFFFFF` |
| Gap title↔body | `7px` *(off-scale)* |
| Body fill | `#1D1D1D`, radius `12px` |
| Body padding | `14px 0` |
| Width | `320` |

⚠ **CONFLICT — disabled is drawn two different ways in one component set.**
`alignment=right, state=disabled` changes the fill to `#0F0F0F`; `alignment=left,
state=disabled` uses `opacity 0.5` on the same `#1D1D1D`. Same state, two mechanisms, and
`#0F0F0F` is not a token in any source. Use `opacity 0.5`.

### 9.2 Rules for rendering an amount

These are conventions read out of the app and Figma; they are consistent across both and
are the safest thing in this section:

- **The primary amount is the largest thing on the screen.** Nothing competes with it.
- **Primary and secondary amounts are always both shown** — the wallet currency and the
  display currency. The secondary sits directly below, `text.secondary`, ~60% of the
  primary size.
- **A currency pill or ticker always accompanies an amount.** An amount never appears
  without its unit.
- **Sats are integers, never decimated.** Group with thin spaces: `1 234 567 sats`.
- **Fiat carries exactly two decimals**, always, including `$0.00`.
- **Sign and colour together**: received `+` in `#00A700`, sent `−` in `text.primary` —
  **not** in `error` red. Red means failure, never "money left".
- **Never abbreviate an amount** (no `1.2M sats`) anywhere the user might act on it.
- Amounts are tabular — use `font-variant-numeric: tabular-nums` so digits don't jitter
  while typing.

⚠ **CONFLICT — no single amount component exists.** Nine app directories render amounts;
none is the canonical one. The rules above hold across them, but there is nothing to point
an implementer at. **This is the biggest gap between the design system as documented and
as built.**

---

## 10. QR presentation — Blink-specific

**Intent** (`18365:111847`): *"Versions of QR codes used in app"*

Figma `QR` (`4144:24674`), four sizes; `QRs` (`11434:55671`), the carousel.

| Variant | Box | Radius | Border | Padding | Data | Centre logo |
|---|---|---|---|---|---|---|
| big | `312 × 312` | `12px` | none | `28px` | `256 × 256` | `50.4`, radius `8` |
| small | `250 × 250` | `20px` | `2px #1D1D1D` | `28px` | fill | `45`, circular |
| empty | `250 × 250` | `20px` | `2px #1D1D1D` | `28px` | placeholder text | — |
| success | `250 × 250` | `20px` | `2px #1D1D1D` | `28px` | success mark | — |

**The QR card is always `#FFFFFF`, in both themes.** Never render a QR on a dark or
tinted background, never invert it, never apply the gradient behind it — scanners fail.
The app gets this right: `backgroundColor: colors._white`
([qr-view.tsx:232](app/screens/receive-bitcoin-screen/qr-view.tsx#L232)) uses the theme-independent `_white`.

**Carousel** (`QRs`) — three slides, `ONCHAIN` / `LN` / `USDT`, positions `1`, `2`, `3`,
plus `3-initial`. The active slide is full opacity; **inactive slides sit at `opacity 0.5`**.
Container height `272`. The app matches: `borderRadius: 20`
([qr-carousel.tsx:100](app/components/qr-carousel/qr-carousel.tsx#L100)).

**Error correction** — the app uses `ecl: "L"` for on-chain and `"M"` for Lightning and
USDT ([qr-view.tsx:37-43](app/screens/receive-bitcoin-screen/qr-view.tsx#L37-L43)). A centre logo occludes the middle, so **never drop
below `M` when a logo is present**. On-chain at `L` with a logo is the one combination to
watch.

✅ **AGREEMENT — this is the best-aligned component in the library.** Figma's `28px`
padding and `20px` radius match the app exactly.

⚠ **CONFLICT — logo size.** App `logoSize: 60` ([qr-view.tsx:158](app/screens/receive-bitcoin-screen/qr-view.tsx#L158)); Figma `45`
(small) / `50.4` (big). The app's logo occludes more of the code than designed — directly
in tension with the `ecl: "L"` choice above.

⚠ **CONFLICT — two radii for one component.** `big` is `12px`, the other three are `20px`.

⚠ **CONFLICT — carousel page background.** The app sets the *page* to `colors.background`
(theme-dependent) while the QR card inside is always white. Figma shows no page fill.
Harmless today; do not let the card inherit the page colour.

**For decks and brand surfaces** — reproduce a QR at no less than `250px`, on white, with
`28px` quiet zone, `radius 20`, and a real scannable payload. Never a decorative
fake QR — someone will always try to scan it.

---

## Accessibility — applies to every component above

**Hit target — 44 × 44 CSS px minimum.** Components that meet it: `icon-button size=large`
(exactly 44), `list-item` (exactly 44), bottom-bar items (65), button-primary (50).
Components that **fail** and need a wrapper: `button-tertiary` (32), `icon-button` medium
(32) / icon-only (30) / small, `currencyPill` (30), `Badge` (22, but it is not interactive).
Spacing between adjacent targets ≥ 8px.

**Focus ring.** Figma specifies none, anywhere — it is a touch library. On **any**
keyboard-reachable surface (web, decks, internal tools) every interactive component takes:

```css
outline: 2px solid var(--accent);
outline-offset: 2px;
border-radius: inherit;
```

Never `outline: none` without a replacement. Note blink.sv already does this correctly on
`.nav-link` (`outline: 2px solid #0050bd`) — though `#0050bd` is not a Blink colour.

**Contrast — measured, not estimated.** Full table in `references/colors.md`. The failures
that matter here:

| Pair | Ratio | Verdict |
|---|---|---|
| `#FFFFFF` on `#fc5805` — app light primary button | **3.21:1** | ❌ fails AA |
| `#000000` on `#fc5805` — corrected | 6.54:1 | ✅ AA |
| `#000000` on `#ffad0d` — dark primary button | 11.24:1 | ✅ AAA |
| `#FFFFFF` on `#ffad0d` — Figma loading spinner | **1.87:1** | ❌ fails |
| `#805606` on `#1d1d1d` — secondary pressed | **2.61:1** | ❌ fails |
| `#FFFFFF` on `#00A700` — Dollar pill | **3.22:1** | ⚠ large text only |
| `#9292A0` on `#FFFFFF` — text.muted light | 3.07:1 | ⚠ secondary labels only |
| `#949494` on `#1d1d1d` — text.muted dark | 5.56:1 | ✅ AA |
| `#F59E0B` on `#FFFFFF` — warning as text | **2.15:1** | ❌ never as text |
| `#4453E2` on `#F2F2F4` — info light | 5.24:1 | ✅ AA |
| `#BDBDBD` on `#000000` — inactive tab | 11.18:1 | ✅ AAA |

**Never signal state with colour alone.** Input error/success are colour-only in Figma —
add an icon and a message. The QR carousel's active slide is opacity-only — add a position
indicator.

**Motion** — respect `prefers-reduced-motion`. The loading spinner and
`success-animation` must degrade to a static state.

---

## Summary of conflicts

| # | Component | Conflict |
|---|---|---|
| 1 | button-primary | Light-mode label ships white → 3.21:1, fails AA (inverted `white` token) |
| 2 | button-primary | Figma loading spinner `#FFFFFF` on orange → 1.87:1 |
| 3 | button-primary | Weight 700 (Figma) vs 600 (app) |
| 4 | button-primary | Radius 25 / RNE default / 30 (web) — none is `999` |
| 5 | button-secondary | Prior interim guidance said "1px border" — retracted; no border |
| 6 | button-secondary | Pressed label `#805606` → 2.61:1 |
| 7 | button-secondary | Disabled 0.7 (Figma) vs 0.35 (app) |
| 8 | button-tertiary | Radius 20 (Figma) vs 50 (app) |
| 9 | button-tertiary | App `outline` variant does not exist in Figma |
| 10 | icon-button | Radius 16 (Figma) vs 8 (app); no `large` (44px) variant in app |
| 11 | button-field | Padding 20 (Figma) vs 12 (app); disabled 0.5 vs 0.3; app-only error state |
| 12 | input | Focus = 1.19:1 fill change; no ring |
| 13 | bottom-bar | Pure `#000000` contradicts the `bg.default` token rule — **needs a decision** |
| 14 | bottom-bar | 4 tabs vs 5 in the `2026` variant |
| 15 | bottom-bar | `#BDBDBD` (Figma, web) vs `#CCCCCC` (app dark `grey2`) |
| 16 | bottom-sheet | Radius 20 vs system 16; fill `#000000` |
| 17 | info | Radius 6 (only `6` in the library); bar 2px vs 3px; padding differs |
| 18 | info | `#4453E2` is a fourth app blue; blue is not a Blink color |
| 19 | banners | `bulletin-row` (Figma) vs five unrelated app banners |
| 20 | Badge | 10px type, below every documented floor; radius 12 |
| 21 | currencyPill | Dollar white-on-green 3.22:1; green doubles as `feedback.success` |
| 22 | wallet-summary-2026 | Disabled drawn two ways in one set; `#0F0F0F` is not a token |
| 23 | QR | Logo 60 (app) vs 45/50.4 (Figma), against `ecl: "L"` on-chain |

---

## Still open — do not invent answers

- **Voice for in-app strings.** `references/voice.md` is derived from marketing copy on
  blink.sv and explicitly does not cover app strings. Until the app is audited, apply
  the marketing rules — short declaratives, second person, the limit attached to the
  claim — and do not assume they are the app's own register. **No app string carries an
  exclamation mark.**
- **Pure black in navigation chrome.** The tab bar and bottom sheet are `#000000` against
  a token that reserves `#000000` for the wordmark and print. Needs a ruling. See §4.1.
- **No canonical amount component.** Nine implementations, no base. See §9.2.
- **Light-mode component library.** Does not exist in Figma. Every light value in this
  document is derived and should be confirmed against a real light-mode design pass.
