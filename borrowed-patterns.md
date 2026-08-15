# Borrowed patterns

Reference read in full: **P&C Mobile Repair** - `C:\Users\accc0\Downloads\Agency\Clients\P&C\pandc-mobile-repair\index.html` (571 lines) plus its `assets/styles.css` (41,876 bytes). Routed here because it is the newest build and the project's mobile quality bar, and because this client's priority for the rebuild was explicitly mobile optimisation. Secondary sanity-check against **Big Truck A/C Shop** (single-location specialty trade, single-file structure).

Four patterns borrowed. All four are engineering or UX mechanics. **No colour, no signature element, no headline copy, and no visual identity was taken from either reference.**

---

## 1. Drawer mechanics and body scroll lock

**Source:** P&C `index.html` L83-106 (markup), `assets/styles.css` L64-83 (surface), `index.html` L481-491 (JS)

```css
.nav-drawer{position:fixed;top:0;right:0;width:330px;max-width:88vw;height:100dvh;background:var(--black);
  z-index:1001;transform:translateX(100%);transition:transform .32s cubic-bezier(.2,.8,.2,1);
  display:flex;flex-direction:column;padding-top:env(safe-area-inset-top)}
.drawer-footer{padding:16px 18px calc(18px + env(safe-area-inset-bottom));...}
body.drawer-open{overflow:hidden}
body.drawer-open .mobile-actions{visibility:hidden}
```

**Here:** `index.html` CSS L~200-225, markup L~640-665, JS L~1075-1090. Same `100dvh`, same safe-area padding top and bottom, same `body.drawer-open{overflow:hidden}` lock, same trigger-exclusivity rule (`body.drawer-open .mobile-actions{visibility:hidden}`), same overlay + Escape + link-click close set.

**Re-skinned:** P&C's drawer is a bone-on-black list in Zilla Slab with a 3px gold left-bar sliding in on hover. This one is a **football team sheet**: each link carries a gold squad number (`01` through `08`) skewed `-8deg` to match the client's italic logo, links are set in Anton uppercase rather than a slab serif, rows are separated by hairlines instead of hover bars, the header reads "EL PLANTEL," and the footer stacks a white phone pill, the Book CTA and the opening hours. Colour system is entirely this brand's ink and sand-gold.

---

## 2. Anchor scroll with hash stripping, plus `scroll-padding-top` and `scrollRestoration`

**Source:** P&C `index.html` L478-480, L493-503; `styles.css` L20-21

```js
if ('scrollRestoration' in history) { history.scrollRestoration = 'auto'; }
if (window.location.hash) { history.replaceState(null, '', window.location.pathname); }
document.querySelectorAll('a[href^="#"]').forEach(function(link){
  link.addEventListener('click',function(e){
    var target=document.querySelector(link.getAttribute('href')); if(!target)return;
    e.preventDefault();
    target.scrollIntoView({behavior:'smooth',block:'start'});
    history.replaceState(null,'',window.location.pathname);
  });
});
```
```css
html{scroll-padding-top:calc(var(--nav-h) + 20px)}
@media(max-width:768px){html{scroll-padding-top:calc(var(--nav-h-sm) + 16px)}}
```

**Here:** identical, with `--nav-h:82px` / `--nav-h-sm:66px` in place of P&C's 84/70. Purely mechanical; nothing visual transferred.

---

## 3. Single-open accordion on a `max-height` transition, one mechanism per group

**Source:** P&C `index.html` L505-517

```js
document.querySelectorAll('.acc-head').forEach(function(btn){
  btn.addEventListener('click',function(){
    var item=btn.parentElement, body=item.querySelector('.acc-body'), isOpen=item.classList.contains('open');
    document.querySelectorAll('.acc-item').forEach(function(i){
      i.classList.remove('open');
      i.querySelector('.acc-head').setAttribute('aria-expanded','false');
      i.querySelector('.acc-body').style.maxHeight=null;
    });
    if(!isOpen){item.classList.add('open');btn.setAttribute('aria-expanded','true');body.style.maxHeight=body.scrollHeight+'px';}
  });
});
```

**Here:** used verbatim for the ten-question FAQ, and **extended** into a second, mobile-only instance for the price ledger: `.ledger-group` headers become buttons under 768px, Cortes opens by default, and a `matchMedia('(max-width:768px)')` listener tears the whole thing down on resize to desktop so no stale `max-height` survives a rotation. Same mechanism, same `.36s` easing, `max-height` only, never mixed with `display:none` on a sibling.

**Re-skinned:** P&C uses a bone-on-white FAQ list with a gold plus. Here the FAQ inherits the shop's ink-on-bone hairline rules, and the ledger variant additionally shows a gold Anton price range (`$75 to $250`) in each collapsed header so price transparency survives the compression.

---

## 4. Peeking scroll-snap filmstrip with hidden scrollbars

**Source:** P&C `styles.css` L234-244

```css
.car-track{display:flex;gap:18px;overflow-x:auto;scroll-snap-type:x mandatory;scroll-padding-left:32px;
  padding:6px 32px 16px;scrollbar-width:none;-webkit-overflow-scrolling:touch}
.qcard{flex:0 0 360px;scroll-snap-align:start;...}
@media(max-width:600px){.qcard{flex:0 0 84%;max-width:340px}}
```

**Here:** two instances. The **Chair Record** roster strip (four footballers, `flex:0 0 25%` desktop, `0 0 74%` mobile so the next name peeks) and the **Los Trabajos** gallery, which is a uniform 3x2 grid on desktop and collapses to a `flex:0 0 76%` filmstrip under 768px.

**Re-skinned:** P&C's version is a set of bordered white testimonial cards with a gold top rule and a drop shadow. This one has **no card surface at all** - it is the soft-editorial language: hairline vertical dividers between roster entries, Anton names, gold club labels, no box, no shadow, no radius. The gallery filmstrip carries images only.

---

## Explicitly NOT borrowed

- P&C's palette (`--accent` safety orange, `--black`, `--bone`) - this build samples `#EFB36B` pixel-exact from the client's own logo and derives its darks from that hue.
- P&C's fonts (Zilla Slab + Hanken Grotesk) - Anton + Barlow here, chosen against the Energy / Bold-and-Creative categories and against the client's own italic condensed wordmark.
- P&C's signature hero (the four-quadrant credentials block beside a headline) - this hero is a single full-bleed celebrity photograph with a squad-number tag.
- P&C's headline voice, section names, stats-bar approach, timeline section, rate-sheet form, and multi-city SEO architecture.
- Big Truck's square editorial bands, Hepta Slab or steel blue.

The sibling test: place this page beside P&C Mobile Repair and no stranger would guess the same template produced them. Different nav polarity (bone vs black), different type class (condensed display vs slab), different section geometry (no card boxes at all vs bordered cards throughout), different money-section form (split-screen duplex vs a rate sheet).
