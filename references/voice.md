# Blink — Voice

How Blink sounds. Every rule below is a pattern observed in live Blink copy, with the
quote that evidences it. Nothing here was invented.

## Where this comes from

Derived 2026-08-06 from the English marketing site, `blink.sv`: the home page,
`/features`, `/send-and-receive`, `/security`, `/dollar-balance`, `/merchant-tools`,
`/about`, `/api` and `/circles`.

**Scope:** marketing surfaces only. In-app strings, the blog, the FAQ and support docs
were not audited and are not covered. Do not assume these rules describe them.

The site is not uniform. It carries **two registers**, and the split is chronological —
the pages rewritten for the custodial / non-custodial split (`/send-and-receive`,
`/security`, `/dollar-balance`) are largely plain and precise; the older pages (`/api`,
`/circles`, parts of `/features`) are promotional. **The newer register is the voice.**
The older one is logged as drift in `references/non-conforming.md`.

## In one line

Blink talks in simple, human language — short sentences, the limit said out loud, and
the depth one click away for whoever wants it.

## The rules

### 1. Say the benefit, then say the limit — in the same breath

The most distinctive thing about Blink's voice. Constraints are not in a footnote, an
asterisk or the terms; they sit in the paragraph that makes the claim.

> "Dollar Balance helps reduce bitcoin price volatility, but it does not remove all risk."

> "Blink offers a Lightning wallet backed by reserve cold storage (available in select
> jurisdictions) and a non-custodial Spark wallet for self-custody."

> "Register account with phone number (note: unavailable in the US, UK and some other
> countries)"

> "When sending bitcoin to external wallets, regular network fees may apply depending on
> the type of transaction (on-chain, Lightning, or Spark)."

If a claim has a condition, the condition goes in the same sentence or the one after it.
Never write a clean claim and hide the caveat elsewhere on the page.

### 2. Short declaratives

The strongest lines are one clause.

> "Skip the volatility."

> "Let others create invoices on your behalf."

> "Blink works to keep on-chain fees low"

> "Get paid in seconds, not days"

Body paragraphs run two to four sentences. There are no long subordinate chains.

### 3. Simple, human language — write for the newcomer, link for the power user

Blink is handed to people who have never held bitcoin, and it is also run by merchants,
developers and long-time bitcoiners. Both read the same page. The way Blink resolves that
is **not** to write for the middle: the first message is written for the person who knows
nothing, and the depth sits one click behind it.

> "Lightning Address – like an email for receiving sats" · "Like an email address for
> receiving bitcoin."

The explanation comes before the term, in words the reader already owns. Then the link:

> "Learn more" · "Learn how it works" · "View detailed fee information" ·
> "What's an API?" · "You can always find the latest fee details on the FAQ"

So: plain first sentence, no jargon, no acronym unexpanded. Everything the power user
wants — the fee table, the protocol, the risk mechanics, the API docs — is a link, not a
paragraph. Never make the newcomer wade through depth to reach the point, and never make
the expert feel the page has nothing for them.

### 4. Second person, active voice, imperative for anything the reader does

> "Start receiving bitcoin in seconds, whether you register an account with your phone
> number or you start off with a trial account."

> "Use Dollar Balance to pay Lightning invoices."

> "Lock down your Blink account with biometric authentication, email one time passwords
> (OTP) and 2-Factor Authentication (TOTP)."

> "Open the merchant map to find shops and businesses near you that accept bitcoin as
> payment."

Blink is "Blink" or "we" — third person for the product, first person plural only for
the team.

> "Blink supports transactions on both the Lightning Network and the Spark protocol."

> "We continuously monitor routing, liquidity, and connectivity across both protocols to
> keep transactions fast and reliable."

### 5. Every section is eyebrow + heading

A short framing line, then the heading naming the thing. This is the site's single most
consistent structural pattern — it holds on every audited page.

| Eyebrow | Heading |
|---|---|
| One feature, two modes | Dollar Balance overview |
| High standard for security | Multi-sig cold storage |
| Prevent unauthorized access | Secure authentication |
| Know what changes by mode | Understand the risks |
| Point of sale web app | Lightning cash register |
| Blink works to keep on-chain fees low | On-chain bitcoin payments |
| Move between Balances | Transfer between Bitcoin and Dollar Balance |
| Printable QR code | Receive payments offline |

The eyebrow carries the benefit or the context; the heading carries the noun. Do not
merge them into one clever headline.

### 6. Headings name the thing, they are not slogans

> "Multi-sig cold storage" · "Lightning cash register" · "Merchant map" ·
> "On-chain bitcoin payments" · "Secure authentication" · "The origin story"

Sentence case. Feature names that are proper nouns keep their capitals — Dollar Balance,
Lightning Address, Blink Circles. A verb phrase heading is allowed when it is an
instruction to the reader: "Earn sats for learning", "Understand the risks",
"Receive payments offline".

### 7. Bullets are fragments with no terminal period

> "Fully interoperable with Lightning invoices"

> "Human readable invoice format"
> "Easy to share, simple to type"
> "Print and display at your cash register"
> "Doesn't expire, receive payment over and over"

Keep them under about eight words. Parallel construction across a list.

### 8. Procedures are numbered and the verb is bold

> 1. Tap **Send**
> 2. **Scan** or **paste** the invoice or address
> 3. Review and **confirm**

Three steps where possible. The bolded word is the thing the reader taps.

### 9. Name the place and the people

Blink's copy is specific about where it comes from and who it serves. It does not
abstract this into "communities worldwide" alone.

> "Blink (formerly Bitcoin Beach Wallet) launched in 2020 in El Zonte."

> "In 2020, Galoy founder Nicolas Burtey learned about efforts in Bitcoin Beach to build
> a circular Bitcoin economy. He reached out to Mike Peterson and team to work together
> on a Lightning wallet he was building."

> "Core based in Latin America, supported by a global development team."

> "Born in El Zonte" · "Made with ♥ in Próspera"

Real partners are named and linked — Bitcoin Beach, Bitcoin Ekasi, MOTIV NGO, BTC Shule.
Third-party praise is quoted verbatim with the handle attached, never paraphrased into a
testimonial.

## Register by surface

| Surface | Register |
|---|---|
| Wallet feature pages | Plain. Rules 1–8 in full. |
| Security, risk, custody, fees | Plainest. Rule 1 is mandatory. State the limit before the reader asks. |
| Merchant pages | Practical and outcome-first — "Get paid in seconds, not days". Assume no Bitcoin knowledge. |
| API / developer pages | Same rules. Add specifics: protocol names, figures, uptime. Do not add hype to compensate for a technical audience. |
| About / origin | Narrative and warm. Names people, dates and places. The one place a sentence may run long. |

## Always

- Attach the limit to the claim, in the same breath
- One clause per sentence where the sentence can carry it
- Write the first message for someone who knows nothing, and put the depth behind a
  "Learn more" link for the power user
- Second person for the reader, "Blink" for the product, "we" for the team
- Eyebrow line above every section heading
- Sentence case headings; proper-noun feature names keep their capitals — including
  **Dollar Balance** and **Bitcoin Balance**
- Bullet fragments, no terminal period, parallel construction
- Name the place, the partner and the person
- Define an acronym on first use — "email one time passwords (OTP)"

## Naming

These are fixed. They are not stylistic choices and they do not vary by surface.

| Say | Not |
|---|---|
| **account** — the reader's holdings in Blink | wallet |
| **Bitcoin Balance** · **Dollar Balance** | Bitcoin account, Dollar Account, USD account |
| **Stablesats** | StableSats, stablesats, Stable Sats |

**account, not wallet.** Blink runs a custodial and a non-custodial side, and the same
word has to work for both — so the reader's holdings are an *account* everywhere. This
does not touch the brand: the tagline stays *The Everyday Bitcoin Wallet*, and "Lightning
wallet" or "non-custodial Spark wallet" remain correct when naming a category of product
rather than the reader's own money.

**Stablesats** carries one capital S, in the middle of nothing. It names the mechanism
behind Dollar Balance in Custodial Mode — never the balance the reader holds.

Full word list: `references/terminology.md`

## Exclamation marks

The rule differs by surface.

| Surface | Rule |
|---|---|
| **App copy** | **Never.** No exclamation mark ships in an app string. |
| **Marketing and social** | Allowed, but do not over-use. One in a page, not one per section. |

The site currently over-uses them — nine on `/features` and `/circles` alone, including
in headings ("Zero fees Blink-to-Blink!") and buttons ("Try it!"). A heading or a button
label is the wrong place. Keep them for the rare line where the enthusiasm is real, and
never to make a fee, a spec or a risk sound exciting.

## Never

- **Never an exclamation mark in app copy.** See above.
- **No hype verbs.** Not "unlock", "unleash", "supercharge", "revolutionize", "empower".
- **No magic.** Blink does not "work its magic" and Bitcoin is not "magic internet money"
  in Blink's own voice — that phrasing appears only inside quoted third-party posts.
- **No "just".** "In just minutes" is drift. State the time or cut it.
- **No superlatives without a figure.** "The lowest possible fees" needs the fee table
  next to it, which is how `/features` in fact does it.
- **No "newbies".** Say "people new to Bitcoin". Blink's audience is often being handed
  the app by someone else; the word makes the reader the joke.
- **No insider shorthand in body copy** — not "HODLing", "orange pill", "stacking sats" —
  unless the page is explicitly teaching the term.
- **No depth in the first sentence.** Protocol names, mechanics and fee schedules go
  behind the link, not in the opening line.
- **No fear.** Blink does not sell against inflation, banks or collapse. It sells a
  payment that works.
- **No promise Blink cannot keep in every jurisdiction.** If it varies by mode or region,
  say which.

## Open questions

- **Spanish.** The site ships an ES locale that was not audited. Whether these rules hold
  in translation — particularly rule 2, which is hard to preserve in Spanish — is
  unresolved. Do not assume a literal translation is on-voice.
- **In-app strings.** Not audited. The app's own register may be tighter than this.
- **Blog.** Not audited, and headline style there is visibly different
  ("We Are Launching Non-Custodial Accounts for Blink Wallet — The Facts and The Full
  Story" is Title Case, which contradicts rule 6).
- **Tagline case.** `terminology.md` fixes the tagline as *The Everyday Bitcoin Wallet*;
  the home page H1 sets it as "The everyday Bitcoin wallet". Unresolved.
