# Virtual Flip-Book Preview

Reference for the **virtual** delivery path (SKILL.md step 6): a web artifact that renders the book's pages as a flippable book, the same approach as the CSB repo's `BookPreview` (`hosting/common/components/BookPreview.tsx` in `childern-adult-books/csb`).

## Approach
Build a web artifact (static is enough) that renders the book's page images inside `react-pageflip`'s `HTMLFlipBook`:
- `npm i react-pageflip`
- Page order: front-cover image first, then interior pages in order. (Export PNGs from `interior.pdf`; use the cover front art for the cover page.)
- Props that worked in CSB: `showCover`, `flippingTime={500}`, `usePortrait={false}`, `startPage={0}`, `drawShadow`, `maxShadowOpacity={0.5}`, `mobileScrollSupport`, `clickEventForArrows`, `useMouseEvents`, `swipeDistance={30}`, `showPageCorners`.
- Size responsively: derive page width/height from the viewport (CSB used roughly half the smaller viewport dimension per page) and force a re-render on resize via a `key` bump.
- Each page is an `<img>` with `object-fit: contain` — the art is already full-bleed, so it fills the page.

## Build notes
- Export page PNGs at ~2x for retina (e.g. ~1650 px wide for an 8.5 in page).
- The virtual book is a reading copy, not print: crop page images to trim (drop the bleed).
- Keep the artifact self-contained: bundle the images or reference hosted URLs.
- Nice extras: page counter, prev/next arrows, fullscreen toggle.
- The dedication page, title page, and "The End" page are just pages in the flip sequence — no special casing needed.
