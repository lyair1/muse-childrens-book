---
name: "muse_childrens_book"
description: "Make a custom illustrated children's picture book starring the user's own kid and family, end to end: parent interview, character bible from photos, approved story, consistent illustrations, print-ready PDF, then the parent chooses a virtual flip-book web artifact or a Lulu-printed hard copy."
---

# Muse Children's Book

Turn a parent's idea into a custom-illustrated children's picture book starring their own child and family — delivered either as a **virtual flip-book web artifact** or as a **Lulu-printed hardcover** (or both). Covers the whole arc: discovery → story → illustrations → print-ready PDF → delivery choice → virtual preview and/or print order.

## Workflow

### 1. Discovery — interview the parent
Ask in small batches (2–4 questions at a time), never one giant form. Collect:
- **The star:** child's name, age, appearance notes, and what they call each parent — get family words exactly right (e.g. "Dada" vs. "Daddy" — never assume).
- **The cast:** parents, siblings, pets — names, species, appearance notes. Never invent names — confirm every name with the parent or from the photos.
- **Reference photos:** clear photos of each character; save to `~/workspace/<project>/references/`.
- **Story mode:** (a) fun family adventure, or (b) gentle behavioral story — the parent names a real issue and the story helps the child work through it.
- **Logistics:** length (default 24 pages — Lulu's hardcover minimum — up to 32), trim — default square **8.5×8.5 in**, alternative landscape **11×8.5 in**. Paper: the **heaviest stock Lulu offers** (see "Lulu print specs" below).
- **Dedication (optional):** exact wording, and placement (after the title page or before the back cover).
- One-word answers are final decisions — don't re-ask. Save firm facts to memory as they land.

### 2. Character bible
From the photos, write a fixed description per character (age, hair, eyes, skin tone, signature clothing; species, size, markings for pets). Paste it verbatim into every illustration prompt so characters stay consistent. Save as `characters.md` in the project folder.

### 3. Story + full book plan (approval gate)
Build the complete page plan: front cover, title page, dedication placement, every spread (1–3 short lines per page, age-appropriate), closing page, "The End", back cover + blurb (draft it yourself, get it approved). For behavioral stories follow the shame-free arc below. Present the whole plan and iterate until the parent explicitly approves. No final art before approval.

### 4. Illustrations
One illustration per page plus cover/title/back art, all in one consistent style — **agree the style with the parent first** (offer 2–3 directions; the first production run's bold-cartoon pass was rejected as "not great" and soft pastel watercolor won).
- Offer **full-bleed art with the text baked into the illustration** vs. a framed layout — the first run's parent strongly preferred baked-in hand lettering ("This looks pretty good").
- Aspect ratio must match the trim (square trim → 1:1); 300 DPI at final size (8.5 in → 2550 px per side).
- **Anatomy-check every page zoomed in:** hands and limbs near doors, walls, and overlaps. On the first run the parent caught a character's hand passing through a doorway that had survived a first pass — fix with a surgical regeneration of that page, preserving the text exactly.
- Keep faces and key action away from trim edges; keep baked text ≥0.5 in from trim.
- Save finals to `~/workspace/<project>/art/`.

### 5. Print-ready PDF (always build it — both delivery paths need it)
- Reproducible Python script (Pillow/reportlab) in the project folder.
- **Interior:** page size = trim + 0.125 in bleed on all sides (8.5×8.5 in trim → 8.75×8.75 in, 630×630 pt); 300 PPI; sRGB; flattened; no security.
- **Cover:** one-page wraparound (back + spine + front) built on **Lulu's official template** for the exact trim + page count — download it from lulu.com/pricing with your config (the finish you pick to unlock the template doesn't change dimensions). Spine width comes from Lulu's table (24–84 pp → 0.25 in — small; keep a spine title only if the parent insists and Lulu accepts it).
- Even page count; hardcover minimum 24 pages. No ISBN/barcode for personal copies; keep the project private.

### 6. Delivery choice (ask the parent — the last step)
Ask whether they want a **virtual flip-book**, a **printed hard copy from Lulu**, or **both**. Use a bounded choice widget; "both" is allowed.
- **Virtual →** build a web artifact per "Virtual flip-book preview" below.
- **Print →** drive lulu.com in the browser: create the print project, upload interior + cover PDFs, run Lulu's preflight preview, check spine/bleed/margins. Order **ONE proof copy first**; final copies only after the parent approves the physical proof. Payment goes through the user's wallet (Stripe Link) with explicit purchase approval — follow Purchasing Flow. Cheapest standard shipping unless the parent says otherwise.

### 7. Wrap-up
Record in memory: title, delivery format(s), service, trim, paper, order numbers/delivery estimates, and the family facts learned.

## Output Contract
Under `~/workspace/<project>/`: `references/`, `characters.md`, `manuscript.md`, `art/`, build script(s), `interior.pdf`, `cover.pdf` — plus a published web artifact, a Lulu proof order, or both.

## Operating Rules
1. Never invent family facts — names, appearances, words, and story details come from the parent or their photos.
2. Behavioral stories are gentle and shame-free; the child always ends succeeding.
3. Heaviest paper stock; never downgrade to save a few dollars unasked.
4. No final art before story approval. No print order before proof approval. Every purchase needs explicit approval (Purchasing Flow).
5. One-word decisions are final. Corrections are facts — accept them plainly; don't defend or re-verify.

---

## Story patterns

### Page plan template (32-page book)
- **Cover** (separate file): front illustration + title + "starring \<child\>"
- **p1:** Title page — the story's name, big and clean
- **p2:** Dedication (optional) — the parent's personal message
- **pp3–30:** Story spreads (14 spreads), 1–3 short lines per page
- **p31:** Closing celebration page
- **p32:** "The End" page with a small illustration
- **Back cover** (separate file): illustration + short blurb

For 24 pages: pp3–22 story (10 spreads), p23 closing, p24 end page.

### Behavioral story arc (shame-free, always)
1. **Name the feeling** — "The little hero felt frustrated…"
2. **Show the impulse and its gentle consequence** — what happened, without lecturing.
3. **A trusted character models the better choice** — parent, grandparent, or pet shows the way.
4. **The child tries it, succeeds, gets celebrated.**
5. The child is always the hero. The *behavior* is the thing being outgrown — the child is never "bad."

### Issue → seed ideas
- **Biting** → "Teeth Are for Apples": teeth are for food, not friends. When frustrated: stomp feet, hug a pillow, ask for help.
- **Bedwetting** → "The Dry-Night Club": bodies are still learning; pull-ups are tools, not failures.
- **Hitting** → "Hands Are for High-Fives."
- **Not sharing** → "The Great Turn-Taking Adventure."
- **New-sibling jealousy** → "The Best Big Helper."
- **Fear of the dark** → "The Night-Light Brigade."
- **Picky eating** → "One Brave Bite."

### Text density
- **Ages 1–3:** 1–2 short lines per page, strong read-aloud rhythm, repeat a refrain.
- **Ages 4–6:** 2–4 lines per page.

### Illustration consistency
- Character bible pasted **verbatim** into every prompt, plus one fixed style descriptor (e.g. "soft watercolor storybook illustration, warm light") so every page looks like the same book.

---

## Lulu print specs

Lulu renames options periodically — verify at project setup and update this file if anything moved.

### Service choice
- **Lulu is the default:** one-off hardcover printing, no minimum order, no ISBN required for personal copies.
- The **Lulu Print API** (developers.lulu.com) exists but is built for developers/businesses integrating ordering into their own sites — use the **website upload path** for one-off books.

### Trim — children's book shapes
- **Default:** 8.5 × 8.5 in square (classic picture-book shape).
- **Alternative:** 11 × 8.5 in landscape rectangle.
- (Lulu also offers 8.5 × 11 in portrait, but square/landscape suit picture books best.)

### Ink & paper — heaviest available, always
- **Ink:** Premium Color — Lulu's best color on every page, heavy ink coverage.
- **Paper:** **80# White** — the heaviest interior stock Lulu offers for books (100# coated is calendar-only). Lulu's own Book Creation Guide: *"Use Premium Color Interior printing and 80# Premium Paper when printing any book that contains photos or graphics where heavy ink coverage is used."* The coated 80# white is the photo-book/comic stock — right for full-illustration pages.
- **Rule:** at Lulu project setup, pick the heaviest paper offered for the trim. If Lulu's options page ever shows something heavier than 80# for books, take it and update this file.
- **Cover:** casewrap hardcover on heavy cover stock. Finish: matte (resists scratches, subdued look) or glossy (emphasizes imagery, better wear) — ask the parent; the first production run chose glossy.

### File requirements
- **Interior PDF:** page size = trim + **0.125 in bleed on ALL sides** (8.5×8.5 in trim → 8.75×8.75 in PDF pages).
- **Safety margin:** keep text, faces, and key action well inside the trim edge (baked text ≥0.5 in from trim).
- **Gutter:** allow extra inner margin at the binding so nothing important disappears into the curve.
- **Cover PDF:** single file, back + spine + front — use Lulu's official cover template for the exact trim + page count (spine width varies with page count and paper; 24–84 pp → 0.25 in spine). Download it from lulu.com/pricing with your exact config — the finish you pick to unlock the template doesn't change dimensions.
- **Resolution:** 300 DPI minimum (8.5 in → 2550 px per side).
- **Color:** Lulu's modern workflow auto-matches — **sRGB IEC61966-2.1** source files are fine; alternatively CMYK Coated GRACoL 2006. Don't mix color spaces across images in one book.
- **Fonts:** embedded (subset is fine); rasterized/baked-in text is fine too.
- **Page count:** even number; hardcover minimum **24 pages** (max 800).

### Cost & ordering
- Worked example (Sep 2026, 24 pp premium-color casewrap 8.5×8.5, glossy): **$16.14** book + $5.69 trackable mail shipping + $1.38 tax = **$23.21** — always confirm in Lulu's calculator at setup.
- **No ISBN/barcode** needed for personal copies — leave the barcode area empty; keep the project private.
- Always order **ONE proof copy first**; check gutters, bleed, spine alignment, and color before ordering final copies.
- Shipping: cheapest standard option unless the parent says otherwise.

### Sources
- Lulu product options page (lulu.com/products) — paper types, cover finishes.
- Lulu Book Creation Guide (assets.lulu.com/media/guides/en/lulu-book-creation-guide.pdf) — bleed, color profiles, paper guidance.

---

## Virtual flip-book preview

Build a web artifact (static is enough) that renders the book's page images inside `react-pageflip`'s `HTMLFlipBook` — the exact library and setup from CSB's `BookPreview` (`hosting/common/components/BookPreview.tsx` in `childern-adult-books/csb`). Mirror its props exactly:
- `npm i react-pageflip`
- Page order: front-cover image first, then interior pages in order — **unless the interior PDF already opens on the title page.** When the title art doubles as the cover, prepending a separate cover image renders the same art twice in a row. In that case start the flip sequence with the interior pages in order and skip the standalone cover image.
- Props, copied from CSB: `showCover`, `size="stretch"`, `flippingTime={500}`, `usePortrait={false}`, `startPage={0}`, `drawShadow`, `maxShadowOpacity={0.5}`, `mobileScrollSupport`, `clickEventForward`, `useMouseEvents`, `swipeDistance={30}`, `showPageCorners`, `disableFlipByClick={false}`, `startZIndex={0}`, `autoSize={false}`.
- Lock the size: `minWidth`/`maxWidth` = `width`, `minHeight`/`maxHeight` = `height`.
- Square pages sized from the viewport: `bookWidth = bookHeight = (viewportWidth * 0.8) / 2`; force a re-render on viewport-width change via a `key` bump.
- Each page is an `<img>` with `object-fit: contain` and `width: 100%` — the art is already full-bleed, so it fills the page.

### Build notes
- Export page images at ~2x for retina (e.g. ~1650 px wide for an 8.5 in page). JPEG quality ~85 keeps a 24-page book around ~11 MB.
- The virtual book is a reading copy, not print: crop page images to trim (drop the bleed).
- Keep the artifact self-contained: bundle the images or reference hosted URLs.
- Nice extras: page counter, prev/next arrows, fullscreen toggle.
- The dedication page, title page, and "The End" page are just pages in the flip sequence — no special casing needed.

---

## Field notes — first production run

The diary of the first book made with this skill: a 24-page hardcover (September 2026). Every lesson below came from something the parent said or something that went wrong.

### Style direction
- The first production pass (bold storybook cartoon, framed text layout) was rejected: *"not great in terms of illustration and how the text is on the image."*
- Offered three style directions; the parent picked **soft pastel watercolor** (the old CSB factory look).
- Then offered full-bleed pages with **text baked into the artwork** vs. a framed layout — parent chose baked-in: *"This looks pretty good."* Interior approved the same day.
- Lesson: never commit to a style without showing directions first, and always offer baked-in lettering as an option — it reads far more "real book" than framed text.

### Baked text
- Hand-lettered navy serif, generated as part of each watercolor page. Spelling verified on every page.
- Parent confirmed ordinary hyphens are fine — don't "fix" them into em-dashes unasked.
- Keep baked text ≥0.5 in from the trim edge. An auto-scan flagged art details near edges; visual check confirmed the text itself was clear — trust eyes over scanners for watercolor.

### The doorway fix
- The parent flagged one page: a character's hand appeared to pass through the door/wall.
- Fixed with a **surgical regeneration** of that one page: hand fully in front of the doorway, natural anatomy, text preserved exactly. Original kept as a backup.
- Lesson: zoom into every page and check hands/limbs wherever they overlap doors, walls, furniture, or other characters. And show the parent the pages — they catch what you miss.

### Print specs (verified against the real files)
- 24 single pages — exactly Lulu's hardcover minimum. 630×630 pt = 8.75×8.75 in (8.5 trim + 0.125 bleed).
- 300 PPI (2625×2625 px pages), sRGB, flattened, no fonts (all rasterized), no security, ~14 MB.
- Note: the 2625 px pages were upscaled from 1600×1600 art — fine for this run, but generate at native 300-DPI size when you can.
- No blank opening page: Lulu says blank pages are optional, and a picture book opens on its title page.

### Cover from Lulu's template
- Downloaded the official cover template from lulu.com/pricing using the real config (8.5×8.5, 24 pp, casewrap, Premium Color, 80# white). Lulu required picking a finish to enable the template — picked Matte for the download; **finish doesn't change template dimensions**, and the parent later chose Glossy.
- Template for 24 pp: **0.25 in spine** (Lulu's table: 24–84 pp → 0.25 in), 0.625 in wrap area. Canvas 19×10.25 in (1368×738 pt).
- The 0.25 in spine makes the title tiny. The parent explicitly wanted the title on the spine anyway — kept it, and flagged it for the proof check. Lesson: warn the parent when the spine is minimal, keep it only on explicit request.
- Front: title art full-bleed. Back: new square watercolor + blurb typeset in navy serif. No ISBN/barcode (personal copy).

### Ordering (the worked example)
- Project created on lulu.com as a **private** "Print Your Book" project — no ISBN, no retail distribution.
- Ordered **ONE proof copy**: $16.14 book + $5.69 trackable mail shipping + $1.38 tax = **$23.21**.
- Parent's shipping rule: *"don't pay extra for shipping"* — cheapest standard shipping, always, unless they say otherwise.
- Delivery estimate was 12–14 business days — later than the pre-checkout estimate. Always read the checkout's real estimate back to the parent before they approve payment.
- Payment: Stripe Link; the parent picked the card from a bounded choice of their saved methods. Lulu login was captured once via the Secure Vault and reused.
- After the physical proof is approved, final copies can be ordered — never before.

### Getting family details right
- Capture exactly what the child calls each parent during discovery — never assume ("Dada" vs. "Daddy", etc.). A correction here is a fact: accept it once, never again.
- Never invent pet names; confirm every name from the photos or the parent. An early draft used the wrong name for a family dog — corrected once, never again.
- Capture the dedication verbatim, and place it exactly where the parent wants it.

### How the parent communicates
- One-word answers ("Yep", "Automatic", "Glossy") are final decisions — act on them, don't re-ask.
- *"Ok do it for me! Do the lulu thing"* means: handle the whole order, bring back only the final total for approval.
- Corrections are stated as plain facts — accept them, fix, move on. Never defend the prior version or offer to re-verify what they just established.
