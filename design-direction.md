# Barberia de las Estrellas - Design Direction
Build: Cross Designs / Builda v6 - 14 August 2026
Target: https://www.barberiadelasestrellas.com/ (Square Online, single page)

---

## Step 2 - Conversion diagnosis of the current site

The live site is a stock Square Online template with the brand's colours removed rather than applied. It is one page (`/` and `/s/appointments` render identical content). It contains **four images total**: the logo, one panoramic shop shot, one cropped Messi band, and one staff portrait.

**Where it loses leads**

1. **The only real asset on earth is buried in a 1290x560 letterbox band.** The shop's entire competitive moat is that Nico Jaffe is Leo Messi's barber. On the live site Messi appears as a decorative strip between the staff list and a generic CTA, cropped so hard you see a torso and half a face. There is no caption, no date, no name, no claim attached to it. A first-time visitor has no idea what they are looking at.
2. **The service menu renders as grey skeleton boxes on load.** Square's booking widget hydrates client-side. On a cold load the entire price list, which is the single highest-intent block on the page, is a stack of empty placeholder rectangles for several seconds. On a slow Miami LTE connection that is the whole first impression.
3. **The pitch is in Spanish, in 12px grey, below the fold.** "Veni a recortarte con las mismas maquinas que se corta Leo Messi" is a genuinely great line. It is set as body copy in a template's default type, under 600px of whitespace, in a section titled "SERVICE MENU."

**Also costing money**

- Zero typography. Inter, Arial and "Square Market" at template defaults. Nothing communicates barbershop, Miami, football or premium.
- The logo is nearly invisible: a black wordmark sitting on Square's white-to-grey gradient header.
- Three of four barbers have blank grey placeholder avatars in the Staff tab.
- ~600px of dead whitespace between the service menu and the next section.
- No schema markup at all, so no rich result, no service catalogue, no FAQ, no aggregate anything.
- No FAQ, no reviews, no hours in structured data, no map, no parking mention (they have free parking, which is remarkable for Wynwood and is only mentioned in their Instagram bio).
- Booking is fragmented across Square Appointments **and three separate Booksy listings**, which splits reviews and confuses returning customers.
- H1 is the word "Appointments" (the page title). The word "barbershop" does not appear in the title tag.

**Worth preserving**

- The real prices. All ten of them, published, no "call for quote."
- The Square booking flow itself works and is already integrated with their calendar and payment methods.
- The Spanish voice. It is who they are and it should get louder, not quieter.
- The line "La Barberia que elige el 10."

---

## Step 3 - Competitive visual research

| Site | Type / colour | Layout rhythm | Signature | Steal | Reject |
|---|---|---|---|---|---|
| blindbarber.com | Vintage saloon display + grotesque body. Warm dark: black, cream, amber | Centred headers, full-bleed atmospheric imagery between modular product grids | The speakeasy-behind-the-barbershop concept. Space as brand | Barbershop-as-clubhouse framing (the client has a lounge and a pool table) | E-commerce-first hierarchy; retail outranks the haircut |
| fellowbarber.com | Clean geometric sans throughout. Warm light, `#fffcf9` cream, no pushed accent | Centred modular product grids, no full-bleed drama | The wordmark itself; restraint as the statement | Multi-location "Book Now" in nav | The safest, quietest treatment in the set. Premium-DTC generic |
| personsofinterestbklyn.com | Location-first nav (Carroll Gardens / Fort Greene / Williamsburg) | Neighbourhood as primary navigation | A mural photograph as the literal hero | Street-art-as-identity. The closest analogue to Wynwood | Booking loses top billing to a shop cart |
| ruffians.co.uk | "Ruffians Blue" against black/white. Cool, sportswear-adjacent | Full-bleed campaign hero, carousel grid, varied | Copy voice, not visuals ("GET THICK, QUICK") | Proof that a barbershop can have real written personality | Cool blue + CPG carousel. Wrong temperature for Miami Latino |
| barberandco.us | Black, gold and red vintage barbershop. Handwritten "Est. 2022" | Centred modular with asymmetric image placement | Candid mid-service craft moment (comb, cape, concentration) | Leading with the craft moment rather than a posed portrait | Black-gold-red is now the genre costume for every upscale shop |
| brazebarberlounge.com (local comp) | Wix, neutral, photography-led | Uniform card grids, centred footer | "Luxury grooming meets affordability" over a low fade | Nothing structural. This is the local floor to clear | Affordability positioning |

**What the category shares:** persistent Book CTA routed to Squire/Zenoti/Square; editorial-warm photography as the trust signal; two or three colours maximum with exactly one accent; location treated as a credibility signal; the physical space photographed as often as the people. Notably, the category is clean of AI-slop tropes (no stat dashboards, no particles) because these sites are built by barbers and creatives, not marketers.

**Where the whitespace is:** not one site in the set uses verifiable celebrity proof as the hero. They lead with a product, a building, or an anonymous mid-service close-up. Nobody treats the shop as a football-culture clubhouse. Nobody runs a Spanish-first voice. And nobody sells a content deliverable as part of the service, which is exactly what the Star VIP package is.

---

## Step 4 - Design Direction Declaration

> The page is built as a **matchday programme**, not a barbershop brochure: warm charcoal and concrete sampled from the shop's own walls, the logo's sand-gold as the only interactive colour, and oversized condensed display type set like the back of a shirt. The ONE signature element is **The Chair Record** - the real, dated photograph of Nico Jaffe standing over Leo Messi in a barber chair, running full-bleed in the hero and immediately followed by a hairline roster strip naming every footballer who has actually sat in this shop's chairs, with club and date, each traceable to a public post. Deliberately avoided: the black-gold-red vintage-barber costume that every premium shop in the category now wears, and the anonymous mid-service close-up hero that is the category default.

### Design language declaration (per builda-design-language-menu.md)

- **Shape language: Soft editorial.** No card boxes anywhere. Hairline rules, 2px radii, oversized display type, freestanding full-bleed images. Detailed with a **squad-number motif**: `01 02 03` group markers, `10` on the hero photo, `180` behind the Star VIP band, all in Anton skewed `-8deg` to echo the logo's italic wordmark.
- **Money-section form: Split-screen duplex.** Sticky media pane on the left carrying the barber-kit photograph and the "same kit, same $50" argument; the full ten-service price ledger scrolling on the right.
- Neither dimension collides with a taken pair. Panel/inset + Ledger rows is Poppa Wahoo / Captain Key Largo. Ticket + Boarding-pass stack is FKFA. Big Truck holds square editorial bands + Hepta Slab + steel blue.

### Palette (every value traced to an asset)

| Token | Hex | Source |
|---|---|---|
| `--ink` | `#0F0D0B` | Warm near-black derived from the logo gold's hue at low luminance. Not a generic `#1A1A1E`. |
| `--ink-2` | `#171410` | Raised surface, same hue family |
| `--ink-3` | `#282219` | Hairlines and borders |
| `--bone` | `#F4F0E8` | Off-white. Never pure white on dark. |
| `--bone-2` | `#E9E3D7` | Second light tone for background rotation |
| `--concrete` | `#8E8880` | Sampled from the shop's concrete walls and floor in `shop-interior.jpg` |
| `--gold` | `#EFB36B` | **Sampled pixel-exact from `logo.png`.** The logo is two colours only: `#000000` and `#F0B46C`. ACCENT - interactive elements only. |
| `--gold-d` | `#C9873A` | Hover / pressed derivative |

60/30/10 holds: bone and ink neutrals carry the page, ink-2 and concrete support, gold appears only on buttons, links, phone numbers, prices and the accordion affordances. The gold is a warm sand-apricot, not brass, which keeps it off the black-and-gold cliché.

### Typography

- **Anton** (display, 400) - the closest face on Google Fonts to real football-shirt lettering, and the closest to the client's own logo wordmark, which is a heavy condensed italic grotesque. Used uppercase for H1/H2/H3, prices, squad numbers and drawer links. The `-8deg` skew on numerals reproduces the logo's italic without synthesising a fake oblique on body text.
- **Barlow** (body, 400/500/600/700) - squarish grotesque with a signage lineage, legible at 16px, pairs with condensed display without competing.
- Two families. No trailing period on the H1 (condensed display faces render standalone dots badly).
- Verified live: `https://fonts.googleapis.com/css2?family=Anton&family=Barlow:wght@400;500;600;700&display=swap` returns Anton v27 and Barlow v13.

### Section architecture and structural variation

| # | Section | Structure | Differs from neighbours by |
|---|---|---|---|
| 1 | Hero | Asymmetric 2-col, text left / full-bleed photo right, no heading kicker | - |
| 2 | Chair Record | Horizontal scroll-snap roster strip, **overlaps the hero bottom by 52px** | Overlap element; no heading; filmstrip not grid |
| 3 | El 10 | **Leads with a pull quote, no centred heading.** Then 2-col prose + icon list | Quote-lead vs card grid |
| 4 | Bleed band | **Container break #1** - shop panorama edge to edge with a gradient caption | Full viewport width |
| 5 | La Carta | **Split-screen duplex**: sticky media pane + grouped price ledger. Asymmetric H2-left/lede-right header (the ONE asymmetric header) | Ledger rows, not cards |
| 6 | Star VIP | **Container break #2** - full-bleed gold poster band interrupting the dark section | Inverted colour, poster form |
| 7 | El Equipo | Numbered team-sheet rows (`01`-`04`), photo + name + nationality + book | Rows not cards; 2-up grid on mobile |
| 8 | Los Trabajos | Uniform 3x2 image grid; scroll-snap filmstrip on mobile | Image-led, no prose column |
| 9 | Wynwood | Asymmetric address/hours left, map right, today's row auto-highlighted | Data table |
| 10 | FAQ | Left intro / right accordion, ten questions | Accordion |
| 11 | Contact | Centred header, form + info card | Form |
| 12 | Footer | 4-col, brand chip, in-page sitemap | - |

Small-caps kickers: exactly **three** (La Carta, El Equipo, Preguntas). Sections not opening with a centred heading: **four** (hero, roster, El 10, Star VIP). Container breaks: **two**. Overlap elements: **one**.

### Blacklist temptations on this build, and how each was avoided

- **#3 The SaaS Stats Bar.** Enormous pull here: "179 posts, 8,614 followers, 4 footballers, 4 barbers" is begging to be four big monospace numbers in a row. Instead the trust element is the Chair Record - named people with clubs and dates - and the counts are written into a sentence in the Los Trabajos lede.
- **#6 The Generic Hero Headline.** The first draft was "The Wynwood Chair Leo Messi Sits In." It is a better sentence and it is false: the captions say Nico travels to Messi's house. Rewritten to "Leo Messi's Barber Cuts Hair in Wynwood," which is true, still has the name, and adds the city.
- **#8 Fabricated Credibility.** No Google rating exists that could be verified from any source, so there is no rating on the page and no `aggregateRating` in the schema. Squad numbers for Yamal, Rodrygo and Weigandt were deliberately omitted rather than guessed. Only Messi's `10` appears, because the shop's own tagline already claims it.
- **#16 The Orphan Featured Card.** First pass had a `span 2` hero tile in the Los Trabajos grid. Replaced with a uniform 3x2.
- **#13 The White-Out Logo.** The logo is a black wordmark with a gold ring and star. The nav was built **bone rather than dark** specifically so the positive logo reads correctly, and the footer places it on a bone circular chip. Nothing is inverted or filtered.
- **#1 The Section Header Metronome.** Three kickers, four sections that do not open with a heading at all.

### Mobile design decisions (independent of desktop)

- Hero element order set with `display:contents` + `order`: eyebrow, H1, photo, **CTAs**, lede, note. Both CTAs land above the fold on a 390x844 device.
- Price groups collapse to accordions below 768px with **Cortes open by default**, and each collapsed header still shows its price range (`$75 to $250`) so nothing is hidden behind a tap.
- Los Trabajos becomes a peeking scroll-snap filmstrip rather than three stacked rows.
- Team sheet compresses to 2-up cards, never 1-up.
- Drawer is a right-slide surface skinned as a team sheet: `01`-`08` gold squad numbers, Anton links, phone pill and Book CTA in the footer, opening hours underneath.
- `100dvh`, `env(safe-area-inset-*)`, `scroll-padding-top`, hash-stripping anchors, body scroll lock, `scrollRestoration = 'auto'` all applied.
