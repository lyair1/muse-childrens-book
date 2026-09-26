# Virtual Flip-Book Preview

Reference for the **virtual** delivery path (SKILL.md step 6): a web artifact that renders the book's pages as a flippable book, the same approach as the CSB repo's `BookPreview` (`hosting/common/components/BookPreview.tsx` in `childern-adult-books/csb`).

## Approach
Build a web artifact (static is enough) that renders the book's page images inside `react-pageflip`'s `HTMLFlipBook` — the exact library and setup from CSB's `BookPreview` (`hosting/common/components/BookPreview.tsx` in `childern-adult-books/csb`). Mirror its props exactly:
- `npm i react-pageflip`
- Page order: front-cover image first, then interior pages in order — **unless the interior PDF already opens on the title page.** When the title art doubles as the cover, prepending a separate cover image renders the same art twice in a row. In that case start the flip sequence with the interior pages in order and skip the standalone cover image.
- Props, copied from CSB: `showCover`, `size="stretch"`, `flippingTime={500}`, `usePortrait={false}`, `startPage={0}`, `drawShadow`, `maxShadowOpacity={0.5}`, `mobileScrollSupport`, `clickEventForward`, `useMouseEvents`, `swipeDistance={30}`, `showPageCorners`, `disableFlipByClick={false}`, `startZIndex={0}`, `autoSize={false}`.
- Lock the size: `minWidth`/`maxWidth` = `width`, `minHeight`/`maxHeight` = `height`.
- Square pages sized from the viewport: `bookWidth = bookHeight = (viewportWidth * 0.8) / 2`; force a re-render on viewport-width change via a `key` bump.
- Each page is an `<img>` with `object-fit: contain` and `width: 100%` — the art is already full-bleed, so it fills the page.

## Build notes
- Export page PNGs at ~2x for retina (e.g. ~1650 px wide for an 8.5 in page).
- The virtual book is a reading copy, not print: crop page images to trim (drop the bleed).
- Keep the artifact self-contained: bundle the images or reference hosted URLs.
- Nice extras: page counter, prev/next arrows, fullscreen toggle.
- The dedication page, title page, and "The End" page are just pages in the flip sequence — no special casing needed.
