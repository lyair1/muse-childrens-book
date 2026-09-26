---
name: "muse_childrens_book"
description: "Make a custom illustrated children's picture book starring the user's own kid and family, end to end: parent interview, character bible from photos, approved story, consistent illustrations, print-ready PDF, then the parent chooses a virtual flip-book web artifact or a Lulu-printed hard copy."
---

# Muse Children's Book

## Purpose
Turn a parent's idea into a custom-illustrated children's picture book starring their own child and family — delivered either as a **virtual flip-book web artifact** or as a **Lulu-printed hardcover** (or both). Covers the whole arc: discovery → story → illustrations → print-ready PDF → delivery choice → virtual preview and/or print order.

## Workflow

### 1. Discovery — interview the parent
Ask in small batches (2–4 questions at a time), never one giant form. Collect:
- **The star:** child's name, age, appearance notes, and what they call each parent — get family words exactly right (e.g. "Dada" vs. "Daddy" — never assume).
- **The cast:** parents, siblings, pets — names, species, appearance notes. Never invent names — confirm every name with the parent or from the photos.
- **Reference photos:** clear photos of each character; save to `~/workspace/<project>/references/`.
- **Story mode:** (a) fun family adventure, or (b) gentle behavioral story — the parent names a real issue and the story helps the child work through it.
- **Logistics:** length (default 24 pages — Lulu's hardcover minimum — up to 32), trim — default square **8.5×8.5 in**, alternative landscape **11×8.5 in**. Paper: the **heaviest stock Lulu offers** (see `references/lulu-print-specs.md`).
- **Dedication (optional):** exact wording, and placement (after the title page or before the back cover).
- One-word answers are final decisions — don't re-ask. Save firm facts to memory as they land.

### 2. Character bible
From the photos, write a fixed description per character (age, hair, eyes, skin tone, signature clothing; species, size, markings for pets). Paste it verbatim into every illustration prompt so characters stay consistent. Save as `characters.md` in the project folder.

### 3. Story + full book plan (approval gate)
Build the complete page plan: front cover, title page, dedication placement, every spread (1–3 short lines per page, age-appropriate), closing page, "The End", back cover + blurb (draft it yourself, get it approved). For behavioral stories follow the shame-free arc in `references/story-patterns.md`. Present the whole plan and iterate until the parent explicitly approves. No final art before approval.

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
- Full specs: `references/lulu-print-specs.md`. Everything learned in the first production run: `references/field-notes.md`.

### 6. Delivery choice (ask the parent — the last step)
Ask whether they want a **virtual flip-book**, a **printed hard copy from Lulu**, or **both**. Use a bounded choice widget; "both" is allowed.
- **Virtual →** build a web artifact: page images rendered with a book-like JS page-flip (`react-pageflip`'s `HTMLFlipBook`, the same approach as the CSB repo's `BookPreview`). Recipe: `references/virtual-preview.md`.
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
6. Keep this file lean; bulky detail lives in `references/`.
