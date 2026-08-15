# Barberia de las Estrellas

Rebuild of https://www.barberiadelasestrellas.com/ for Barberia de las Estrellas, 164 NW 20th St Suite 209, Wynwood, Miami FL 33127.

| | |
|---|---|
| Build date | 14 August 2026 |
| Repo | https://github.com/crossfiber/barberia-estrellas |
| Live | https://crossfiber.github.io/barberia-estrellas/ |
| Structure | Single `index.html`, all CSS and JS inline. External deps: Google Fonts CDN + Font Awesome 6.5.1 CDN only. |
| Reference builds consulted | P&C Mobile Repair (read in full), Big Truck A/C Shop |

## Fonts

- **Anton** (display) - https://fonts.google.com/specimen/Anton
- **Barlow** 400/500/600/700 (body) - https://fonts.google.com/specimen/Barlow
- Loaded via `https://fonts.googleapis.com/css2?family=Anton&family=Barlow:wght@400;500;600;700&display=swap` (verified live 14 Aug 2026: Anton v27, Barlow v13)

## Palette

| Token | Hex | Source |
|---|---|---|
| `--ink` | `#0F0D0B` | Warm near-black derived from the logo gold's hue at low luminance |
| `--ink-2` | `#171410` | Raised surfaces |
| `--ink-3` | `#282219` | Hairlines |
| `--bone` | `#F4F0E8` | Off-white |
| `--bone-2` | `#E9E3D7` | Second light tone |
| `--concrete` | `#8E8880` | Sampled from the shop's concrete walls |
| `--gold` | `#EFB36B` | **Sampled pixel-exact from the client's logo PNG** (the logo contains only `#000000` and `#F0B46C`). Accent, interactive only. |
| `--gold-d` | `#C9873A` | Hover derivative |

## Design direction, in one paragraph

A matchday programme rather than a barbershop brochure. Warm charcoal and concrete taken from the shop's own walls, the logo's sand-gold reserved entirely for things you can tap, and oversized condensed display type set like the back of a shirt. The signature element is the Chair Record: the real dated photograph of Nico Jaffe standing over Leo Messi in a barber chair, running as the hero, immediately followed by a hairline roster strip naming every footballer who has sat in these chairs with club and date. Deliberately avoided: the black-gold-red vintage-barber costume the whole premium category now wears, and the anonymous mid-service close-up that is the default hero in this niche.

## Assets

| File | Source | Notes |
|---|---|---|
| `assets/messi-nicojaffe.jpg` | instagram.com/p/DA2TRw4MNk8 (client's own post, Oct 2024) | 1290x1239. Hero. |
| `assets/kit-counter.jpg` | Crop of the above | 1250x639. Services sticky pane. |
| `assets/shop-wynwood.jpg` | Client's Square site CDN | 2400x351. Full-bleed band. |
| `assets/work-jerseys.jpg` | Crop of the panorama | 640x480. Signed shirt wall. |
| `assets/work-floor.jpg` | Crop of the panorama | 640x480. Chairs and capes. |
| `assets/work-trophy.jpg` | Crop of the panorama | 640x480. Trophy. |
| `assets/barber-magic.jpg` | Square Appointments staff photo | 1400x1236. |
| `assets/logo.png` | Client's Square site CDN | 500x500 RGBA. Positive only. |
| `assets/og-share.png` | Designed for this build | 1200x630 share card. |
| `assets/favicon.png`, `assets/apple-touch-icon.png` | Logo on a bone field | 512 / 180. |
| `assets/cross-logo-white.png` | Cross Designs | Footer credit. |

## Outstanding placeholders

Everything below is a labelled placeholder in the live build, not stock and not generated art.

1. `[REAL PHOTO NEEDED]` - **three barber portraits**: Lucas Farinha, Mathi, Alejandro. Square currently serves blank grey placeholders for all three, so nothing exists to extract.
2. `[REAL PHOTOS NEEDED]` - **three gallery tiles**: a before-and-after fade, a platinum colour job, and Chelo Weigandt in the chair. All three exist on @barberiaestrellas; pending client upload.
3. `[LOGO ASSET NEEDED FROM CLIENT]` - a **reversed / knockout logo for dark backgrounds**. The supplied PNG is a black wordmark with a gold ring and star, which disappears on ink. Rather than CSS-inverting it (never), the nav was built bone so the positive mark reads correctly, and the footer places it on a bone circular chip. A proper light version, ideally the original SVG, would remove that constraint. The Instagram avatar shows a light version exists.
4. **The signed Leo Messi shirt.** The Oct 2024 caption says Leo left a signed shirt at the shop. There is no photograph of it anywhere online. It is referenced twice in the copy and is the strongest untapped asset the business owns.
5. **No verified Google rating.** No consolidated rating could be confirmed from any source, so there is deliberately no rating on the page and no `aggregateRating` in the schema. See the booking-fragmentation note below.

## Third-party hotlink risks

None. Every image is served from this repo. The original Square site hotlinks `3b663b6e1075c74302bb.cdn6.editmysite.com` and `appointments-production-f.squarecdn.com`; both were downloaded and re-hosted here so the demo does not break if Square is cancelled.

## Booking links

Every CTA points at the client's existing Square booking page, `https://www.barberiadelasestrellas.com/s/appointments`. If this build replaces that domain, swap all eleven of those hrefs for the direct Square Appointments URL. They are the only external booking references in the file.

Bookings and reviews are currently split across Square plus **three separate Booksy listings**, which is almost certainly why no consolidated rating exists. Consolidating is the highest-leverage non-design fix available and is item one in the conversion roadmap.

## Verification note for the client

The page names four footballers (Messi, Chelo Weigandt, Lamine Yamal, Rodrygo Goes) and states where each was cut. Every claim traces to a dated public post on @barberiaestrellas or @nicojaffe, and the copy is explicit that Messi was a house call rather than a shop visit. Squad numbers were deliberately not invented for anyone except Messi's `10`, which the shop's own tagline already claims. Before this goes to a production domain, confirm the shop is comfortable using these likenesses commercially on its own website.

## SEO implemented

Title 55 chars, meta description 149 chars, canonical, robots, geo.region / geo.placename / geo.position / ICBM, full Open Graph set with a designed 1200x630 card and explicit width/height/alt, Twitter `summary_large_image`, `og:locale:alternate` es_US. Three JSON-LD blocks, all valid: `HairSalon` (full NAP, geo, hours, priceRange, paymentAccepted, currenciesAccepted, areaServed, knowsAbout, knowsLanguage, founder, hasMap, ten-item `hasOfferCatalog` with real prices), `Organization` with a two-entry `contactPoint` array, and a ten-question `FAQPage`. Semantic `<address>` in both the location section and the footer. One `H1`, eight `H2`. Meta, og, twitter and schema descriptions are synchronised.

## Files

```
barberia-estrellas/
├── index.html              the build
├── README.md               this file
├── design-direction.md     diagnosis, competitive research, direction declaration, section architecture
├── borrowed-patterns.md    the four patterns taken from P&C, with line ranges and how each was re-skinned
├── credentials.md          LOCAL ONLY, gitignored
├── GRAB-IG.bat             helper script for pulling the remaining Instagram assets
├── ASSETS-NEEDED.md        tiered list of the photos still needed
└── assets/
```
