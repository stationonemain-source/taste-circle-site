# tastecircle.org — design contract (2026-10-17)

One page. The product is a feed of real plates posted by real people in Norman, so the page
is that feed, with the words kept out of its way.

## 1. Brand facts (not negotiable)
- Name: **TasteCircle** (one word in the app and App Store; "Taste Circle, LLC" in legal copy only).
- Mark: `assets/img/mark-navy.png` / `mark-white.png`, extracted from the App Store icon. Used as an `<img>`
  or a CSS mask, never redrawn, never recoloured outside navy/cream/white.
- Every claim on the page comes from the app's own code, the App Store listing, or plates.json. No invented
  metrics, no testimonials, no review quotes.

## 2. Colour (sampled from the real app, 1.2)
```
:root{
  --cream:#F7EFE3;   /* page */
  --cream-2:#EFE4D2; /* cards, hairlines on cream */
  --navy:#121c33;    /* text, dark band */
  --navy-2:#1a2745;  /* cards on navy */
  --peri:#9DB6FF;    /* accent: Your Spot band, focus ring, one link colour */
  --amber:#D99A3A;   /* only ever the word Crumbs and the crumb dot */
  --ink-2:#4a5068;   /* secondary text on cream */
  --ink-3:rgba(18,28,51,.62);
}
```
Neutrals (cream + navy) carry 90% of the page. Periwinkle appears as a surface once (Your Spot) and as
focus/hover elsewhere. Amber appears once. No gradients anywhere.

## 3. Type
- Display: **Fredoka** (self-hosted variable woff2, 300-700, `font-stretch:94%`). Weights used: 600 for h1/h2,
  500 for h3 and the wordmark. Tracking -0.02em at 32px and above.
- Body: **Poppins** 400 / 500 / 600 (self-hosted). The app's body face.
- Scale (px): 13 · 14.5 · 16 · 18 · 22 · 28 · 36 · 48(desktop h1). Line-height 1.55 body, 1.08 display.
- Never: Inter, Roboto, Montserrat, Space Grotesk, Nunito, Figtree, system-ui as display, Google Fonts links.

## 4. Layout
- Mobile first (390). Content column 100% - 32px gutters; desktop column 1160px max, 1440 audited.
- Hero = headline + one App Store CTA, then the feed: real plates in a 2-column (phone) / 5-column (desktop) grid,
  each captioned exactly as the app would: dish, then `username · place`.
- Section rhythm alternates density: feed (dense) → how it works (airy zig-zag with real screens) →
  games (navy band, text only) → Tables (two real screens) → Crumbs + Nutrition (one quiet row) →
  Your Spot (periwinkle band) → FAQ (native details) → footer.
- Radii: 14px images and cards, 999px pills. Hairlines `1px solid var(--cream-2)` on cream, `rgba(255,255,255,.12)` on navy.
- No parallax, no scroll-jacking, no autoplaying motion. Reduced-motion respected (there is almost no motion to reduce).

## 5. Imagery
- Only the 20 real plates (`assets/plates/pNN-{s,l}.webp`, 240 / 720 square) and the real app screens in
  `assets/app/`. `-s` on phones via `<picture media>`, `-l` from 641px up. Every `<img>` carries width/height.
- Not used on purpose: `punch.webp` and `balance.webp`, because they show a redeem catalogue and "crumbs to spend",
  which the page must not promise.
- No stock photography, no generated imagery, no illustrations drawn in code.

## 6. Voice
- Plain, specific, second person. Norman place names beat adjectives. Sentence case everywhere, including buttons.
- Banned: Discover/Share/Connect taglines, "Trusted by", "seamless", "elevate", emoji in headings, em-dashes on the page.
- Each section heading says what the thing is (Tables, Daily games, Your Spot), not what it feels like.

## 7. Components
- Header: mark + wordmark left, one "Get the app" pill right. Sticky, cream, hairline bottom. 60px.
- CTA: the official App Store badge SVG. Secondary CTA (restaurants): a navy pill with text.
- Plate card: square image, 14px radius, caption below (14.5px/600 dish; 13px/400 who · place).
- Screen frame: the real screenshot with a 14px radius and a 1px navy-10% border; no fake device bezel.
- FAQ: native `<details>`; summary with a plus that rotates to a cross.
- Footer: wordmark, Privacy · Support · Terms · Instagram · App Store, then the Station credit line.

## 8. Accessibility floor
- Contrast: navy on cream 13:1; cream on navy 13:1; navy on periwinkle 7.6:1; ink-2 on cream 7:1.
- Visible focus (`2px solid var(--peri)` on cream, `var(--cream)` on navy), skip link, alt text that names the dish
  and place, headings in order, no text in images except the real screens.

## 9. What would make it slop (check before every screenshot)
Three equal icon columns · gradient blobs · stat band · fake reviews · scroll cue · section numbers as decoration ·
a phone mock-up with made-up content · "Download now" twice · any font that is not Fredoka/Poppins.
