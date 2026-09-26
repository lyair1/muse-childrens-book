# Lulu Print Specs

Reference for the `muse_childrens_book` skill. Lulu renames options periodically — verify at project setup and update this file if anything moved.

## Service choice
- **Lulu is the default:** one-off hardcover printing, no minimum order, no ISBN required for personal copies.
- The **Lulu Print API** (developers.lulu.com) exists but is built for developers/businesses integrating ordering into their own sites — use the **website upload path** for one-off books.

## Trim — children's book shapes
- **Default:** 8.5 × 8.5 in square (classic picture-book shape).
- **Alternative:** 11 × 8.5 in landscape rectangle.
- (Lulu also offers 8.5 × 11 in portrait, but square/landscape suit picture books best.)

## Ink & paper — heaviest available, always
- **Ink:** Premium Color — Lulu's best color on every page, heavy ink coverage.
- **Paper:** **80# White** — the heaviest interior stock Lulu offers for books (100# coated is calendar-only). Lulu's own Book Creation Guide: *"Use Premium Color Interior printing and 80# Premium Paper when printing any book that contains photos or graphics where heavy ink coverage is used."* The coated 80# white is the photo-book/comic stock — right for full-illustration pages.
- **Rule:** at Lulu project setup, pick the heaviest paper offered for the trim. If Lulu's options page ever shows something heavier than 80# for books, take it and update this file.
- **Cover:** casewrap hardcover on heavy cover stock. Finish: matte (resists scratches, subdued look) or glossy (emphasizes imagery, better wear) — ask the parent; the first production run chose glossy.

## File requirements
- **Interior PDF:** page size = trim + **0.125 in bleed on ALL sides** (8.5×8.5 in trim → 8.75×8.75 in PDF pages).
- **Safety margin:** keep text, faces, and key action well inside the trim edge (baked text ≥0.5 in from trim).
- **Gutter:** allow extra inner margin at the binding so nothing important disappears into the curve.
- **Cover PDF:** single file, back + spine + front — use Lulu's official cover template for the exact trim + page count (spine width varies with page count and paper; 24–84 pp → 0.25 in spine). Download it from lulu.com/pricing with your exact config — the finish you pick to unlock the template doesn't change dimensions.
- **Resolution:** 300 DPI minimum (8.5 in → 2550 px per side).
- **Color:** Lulu's modern workflow auto-matches — **sRGB IEC61966–2.1** source files are fine; alternatively CMYK Coated GRACoL 2006. Don't mix color spaces across images in one book.
- **Fonts:** embedded (subset is fine); rasterized/baked-in text is fine too.
- **Page count:** even number; hardcover minimum **24 pages** (max 800).

## Cost & ordering
- Worked example (Sep 2026, 24 pp premium-color casewrap 8.5×8.5, glossy): **$16.14** book + $5.69 trackable mail shipping + $1.38 tax = **$23.21** — always confirm in Lulu's calculator at setup.
- **No ISBN/barcode** needed for personal copies — leave the barcode area empty; keep the project private.
- Always order **ONE proof copy first**; check gutters, bleed, spine alignment, and color before ordering final copies.
- Shipping: cheapest standard option unless the parent says otherwise.

## Sources
- Lulu product options page (lulu.com/products) — paper types, cover finishes.
- Lulu Book Creation Guide (assets.lulu.com/media/guides/en/lulu-book-creation-guide.pdf) — bleed, color profiles, paper guidance.
