# Blink — Terminology

Language drift is as visible as color drift. Use these spellings exactly.

## Product and brand

| Always | Never |
|---|---|
| Blink | blink, BLINK, BLiNK |
| The Everyday Bitcoin Wallet | the everyday bitcoin wallet, Everyday Bitcoin Wallet |
| Blink Wallet *(only when disambiguating)* | The Blink App, Blink app |
| Stablesats | StableSats, stablesats, Stable Sats |
| Dollar Balance | Dollar Account, dollar account, USD account, Stablesats balance |
| Bitcoin Balance | Bitcoin account, bitcoin account, BTC account, sats balance |

## Bitcoin and Lightning

| Always | Never |
|---|---|
| **Bitcoin** — the network, protocol, ecosystem | bitcoin network |
| **bitcoin** — the money, the unit | Bitcoins, BTC coins |
| **Lightning** / the Lightning Network | lightning, LN, the lightning network |
| **sats** | Sats, SATS, satoshi's, sat's |
| **satoshi** / **sats** (singular / plural) | satoshis' |
| Lightning address | lightning address, LN address |
| on-chain | onchain, on chain |
| self-custodial | selfcustodial, self custodial |

Rule of thumb: **Bitcoin** capitalized when you could substitute "the internet";
**bitcoin** lowercase when you could substitute "dollars".

## Product vocabulary

| Always | Never |
|---|---|
| account *(the reader's holdings in Blink)* | wallet |
| balance | funds, holdings |
| send / receive | transfer out / transfer in |
| scan | QR scan, scan QR |
| merchant map | map of merchants, Blink map |
| Bitcoin 101 | bitcoin 101, BTC 101 |

## account, not wallet

The reader's holdings in Blink are an **account**. Blink runs a custodial and a
non-custodial side and the same word has to work for both, so the naming does not change
between them.

This does not touch the brand or the product category:

| Correct | Why |
|---|---|
| "Your account is protected by multi-sig cold storage" | the reader's holdings |
| *The Everyday Bitcoin Wallet* | the tagline, fixed, never reworded |
| "Blink is a Lightning wallet" | naming a category of product |
| "the non-custodial Spark wallet" | naming a category of product |
| ~~"Top up your wallet"~~ → "Top up your account" | the reader's holdings |

## Dollar Balance and Bitcoin Balance — settled

**Dollar Balance** and **Bitcoin Balance** are the canonical user-facing names for the
two balances. They apply everywhere, in both Custodial and Non-Custodial Mode.

**Stablesats** — one capital S, one word, always spelled this way — is not a synonym. It
names the *mechanism* that powers Dollar Balance in Custodial Mode — the same way Spark names a protocol, not a balance. Use it only when
you are explaining how the balance works, never as the name of the thing the user holds.

> Custodial Mode: Dollar Balance is powered by Stablesats. ✅
> Send from your Stablesats. ❌ — say "Send from your Dollar Balance".

Do not write **Dollar Account** or **Bitcoin account**. Both are live on blink.sv and in
the app, and both are now drift — see `references/non-conforming.md`.

## Writing mechanics

- Second person. "You can send sats to anyone."
- Active voice. "Blink converts your balance", not "your balance is converted".
- Numerals for all quantities: "3 steps", not "three steps".
- Currency: `$245.86`, `174,726 SAT` — thousands separated, SAT uppercase when used as
  a unit label after a figure.
- No exclamation marks in app copy, ever. On marketing and social they are allowed but
  should not be over-used — see `references/voice.md`.
- Define jargon on first use, or don't use it.
- Sentence case for headings and buttons. "Send bitcoin", not "Send Bitcoin".

## Tone of voice

Defined in `references/voice.md`, derived from live blink.sv marketing copy.

In short: state what the product does, in short sentences, with the number attached and
the limit said out loud. No exclamation marks, no hype verbs, no claim without a figure.

Scope is marketing surfaces only — in-app strings, the blog and the FAQ were not
audited and are not covered.
