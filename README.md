# Barberia de las Estrellas

Rebuild of https://www.barberiadelasestrellas.com/ for Barberia de las Estrellas, 164 NW 20th St Suite 209, Wynwood, Miami FL 33127.

| | |
|---|---|
| Live | https://crossfiber.github.io/barberia-estrellas/ |
| Build | v3, 15 August 2026 |
| Structure | Single `index.html`, all CSS and JS inline. One external dependency: Google Fonts. |
| Languages | Spanish default, English toggle. 179 string pairs. |

## Positioning

The page leads with the craft, not the clientele. **"Una hora de silla. Cero apuro."** The pitch is haircut quality and unhurried chair time, priced in public.

The word "discretion" does not appear anywhere on the page, and neither does any promise about photos. v2 said it out loud, which reads defensive and makes the reader wonder what there is to hide. v3 lets professionalism be shown instead: on-time appointments, an hour per head, ten published prices, a full crew in the hero, and a guest gallery whose lede says the quiet part plainly:

> Futbolistas, peleadores y gente que vive delante de una camara. Vienen por el mismo corte que hacemos todo el dia, no por otro.

An earlier draft led with "Leo Messi's Barber Cuts Hair in Wynwood." It was dropped: it made the shop a footnote to its customers, and it buried the actual product.

## v3 changes

- Hero centrepiece is now `hero-crew.jpg`, the whole team in the shop. It answers "who cuts my hair" before the page asks for a booking.
- The eyebrow carries the street address with **Suite 209** centred on its own line beneath it.
- One flip-style language button replaces the ES/EN pair, so the brand wordmark keeps its room in the nav.
- **Layout parity is enforced, not hoped for.** Every heading, lede, caption, card label, button and note was measured in both languages at 390, 768, 1024 and 1440 px with the real Anton and Barlow webfonts loaded. Copy was shortened on whichever side wrapped first until the delta was zero at every breakpoint. Nine mismatches found, nine fixed.
- Drawer sizes to its content instead of the viewport, opens with the logo lockup, and puts the phone pill and Reservar directly under Contacto.
- `kit-counter.jpg` recropped to 3:2 so Nico Jaffe and Messi are both in frame.
- FAQ swaps the photo-permission question for published payment methods.

## Bilingual

Every string carries `data-es` and `data-en`, swapped via `innerHTML`; form placeholders use `data-es-ph` / `data-en-ph`. The toggle sits in the nav beside the phone number, persists to `localStorage`, sets `document.documentElement.lang`, and re-measures any open accordion so `max-height` stays correct when text length changes. `og:locale` is `es_US` with `en_US` alternate. FAQPage schema is `inLanguage: es`.

## Design system

| Token | Value | Source |
|---|---|---|
| `--ink` | `#0F0D0B` | Warm near-black derived from the logo gold's hue |
| `--bone` | `#F4F0E8` | Off-white |
| `--concrete` | `#8E8880` | Sampled from the shop's concrete walls |
| `--gold` | `#EFB36B` | **Pixel-sampled from the client's logo.** Accent, interactive only. |

**Anton** (display) and **Barlow** (body). No boxes: structure is carried by hairlines, 2px grid gutters and full-bleed image blocks. `border-radius: 0` globally, so neither cards nor pills. No icon library, no emoji: two inline SVG symbols (phone, close), CSS-drawn accordion indicators, text social links.

## Assets

Real photography only. Nothing is stock, generated, or a recreated logo.

| File | What it is |
|---|---|
| `hero-crew.jpg` | Hero. The full crew in the shop, with a guest. |
| `cut-taper.jpg` | Taper fade with curls, in the work grid. |
| `ba-before.jpg`, `ba-after.jpg` | Same client, same visit. The craft proof. |
| `messi-nicojaffe.jpg` | Leo Messi, Inter Miami CF. |
| `guest-yamal.jpg` | Lamine Yamal, FC Barcelona. |
| `guest-02.jpg`, `guest-03.jpg` | Guests, names pending client confirmation. |
| `work-jersey10.jpg` | The shop's number 10 shirt against the logo wall. |
| `kit-counter.jpg` | 3:2 crop of the Messi shot for the price section. |
| `barber-magic.jpg` | Magic, the only barber portrait that exists. |
| `logo.png` | Client's mark. Positive only, never inverted. |
| `favicon.png`, `apple-touch-icon.png` | Gold star redrawn from the logo. |
| `og-share.png` | Designed 1200x630 share card. |

Unreferenced leftovers from v1, safe to delete: `shop-wynwood.jpg`, `work-floor.jpg`, `work-trophy.jpg`, `work-jerseys.jpg`.

## Outstanding

1. **Names for `guest-02` and `guest-03`** - captioned `[NOMBRE]`. Deliberately not guessed.
2. Barber portraits for Lucas Farinha, Mathi and Alejandro - labelled placeholders.
3. Three cut tiles: skin fade, platinum colour, line design - labelled placeholders.
4. A knockout logo for dark backgrounds. The supplied PNG is a black wordmark, so the nav was built bone rather than CSS-inverting it.
5. No verified Google rating exists, so there is none on the page and no `aggregateRating` in the schema. Bookings are split across Square plus three Booksy listings, which is the likely cause.

## Notes for whoever picks this up

**`aspect-ratio` on an `<img>` loses to the HTML `height` attribute unless CSS also sets `height: auto`.** Without it every image rendered at full intrinsic height: the mobile hero was 930px instead of 232px. Adding `height: auto` to the global `img` rule cut the mobile page from 11,908px to 9,841px.

Booking CTAs point at the client's Square page, `https://www.barberiadelasestrellas.com/s/appointments`. If this build takes over that domain, swap them for the direct Square Appointments URL.

The page names four footballers. Every claim traces to a dated public post on @barberiaestrellas or @nicojaffe, and the copy is explicit that Messi was a house call rather than a shop visit. Confirm the shop is comfortable using these likenesses commercially before pointing a production domain here.

## SEO

Title 55 chars, description 149. Canonical, robots, geo tags, full Open Graph with a designed card, Twitter `summary_large_image`. Three JSON-LD blocks, all valid: `HairSalon` (full NAP, geo, hours, ten-item `hasOfferCatalog` with real prices, `knowsLanguage`), `Organization` with a two-entry `contactPoint` array, and a ten-question `FAQPage`. One H1, semantic `<address>`, meta/og/twitter descriptions synchronised.
