# Build Plan — New Hands-On AI Science Books

Status: **PLAN ONLY** (no pipeline compute spent yet). Covers Building **Agentic**,
**Discovery**, **Neuromorphic**, and **Quantum** AI — currently TOC-only shells — to reach
full parity with *Building Vision AI* (the reference book).

## 1. Current state (per book)

| Asset | Agentic | Discovery | Neuromorphic | Quantum |
|---|---|---|---|---|
| `styles/book.css` (Vision's exact copy) | ✓ | ✓ | ✓ | ✓ |
| `scripts/book.js` | ✓ | ✓ | ✓ | ✓ |
| `book.json` (SSOT) | ✓ | ✓ | ✓ | ✓ |
| Cover + TOC house style | ✓ | ✓ | ✓ | ✓ |
| Front-matter pages (8) | about-series only | same | same | same |
| Chapter/section content | ✗ | ✗ | ✗ | ✗ |
| Illustrations / hero images | ✗ | ✗ | ✗ | ✗ |
| `pagefind/` search index | ✗ | ✗ | ✗ | ✗ |

The CSS/JS guarantee callouts and typesetting *look* right; the books are empty shells
(0 sections). Real parity = producing all content pages **in the same HTML template**.

## 2. Style parity = same template, not just same CSS

Beyond `book.css`/`book.js` (done), each book needs, in the house template:
- **Front matter (8 pages):** foreword, what-this-book-covers, who-should-read,
  look-inside-preview, how-to-use, about-authors, copyright, about-the-series.
- **Chapter/section pages:** the callout system (definition / pitfall / in-production /
  key-insight), epigraphs, worked pipelines, library-shortcut callouts, exercises & labs,
  `chapter-nav`, figure blocks — all emitted by the writing pipeline.
- **Illustrations:** hero image per part/chapter (gemini-imagegen), diagrams
  (technical-diagram-designer).
- **Build artifacts:** `pagefind/` search index (generated at build, after content exists).
- **Capstone + appendices** per book.json counts.

## 3. Writing pipeline — `book-skills` (42 agents / 23 stages)

`book-skills` (the `book-writers` pipeline) turns a chapter outline into a publication-quality,
house-style chapter. Series flow:

```
book-skills  (WRITE)  ->  html2epub (BUILD)  ->  epub2kpf (SHIP)  ->  KDP
```

Per-book inputs:
- `book.json` (✓ created) — title/subtitle/edition/authors/counts; the pipeline template reads it.
- Per-chapter outline + definition. Seed from the existing TOC (chapter titles + subtitles
  already present). Chapter-only TOCs (all 4) need a section-level breakdown per chapter — the
  pipeline's planning stage expands this, but a one-page chapter brief per chapter improves quality.

## 4. Recommended run sequence

1. **Pilot (1 chapter).** Run `book-skills` on one chapter (suggest Quantum Ch.1
   "Quantum Computing Without Physics"). Review house-style output end-to-end; lock the page
   template + confirm `book.json` wiring. Calibrate real per-chapter time/cost.
2. **One full book.** Take that book cover-to-cover: front matter → all chapters (pipeline) →
   illustrations → `html2epub` build → `pagefind` → QA.
3. **Remaining three books**, same recipe.
4. **Ship** each via `epub2kpf` when KDP-ready (assign a real Kindle ASIN → update `book.json` →
   `apply_meta.py`).

## 5. Edition / metadata single source of truth

- **`book.json`** (root, per book) is the source of truth: edition, year, ASIN, domain, authors,
  counts, copyright.
- **`scripts/apply_meta.py`** propagates `book.json` → all pages (currently the edition string;
  extensible to counts/copyright). Idempotent. To bump an edition: edit `book.json`, run the script.
- The `book-skills` template reads `book.json`, so freshly generated pages are correct by construction.
- Optional future: `book.js` runtime injection into `[data-book-edition]` placeholders for
  zero-propagation updates.

## 6. Cost / time estimate (AI-agent execution, not human)

Rough, **to be calibrated by the pilot** — not yet measured:
- **Per chapter:** ~30–90 min agent wall-clock (some stages parallel), ~$5–20 API depending on
  model tier and chapter length.
- **Per book:** Agentic 39ch, Discovery 58ch, Neuromorphic 76ch, Quantum 69ch ≈ **242 chapters total**.
  At the per-chapter range → on the order of **$1.2k–$4.8k API** and many tens of hours wall-clock
  across the four books.
- Recommendation: run the pilot, measure one chapter precisely, then decide batch size / model tier
  (Sonnet for bulk drafting, Opus for review stages) before committing to full books.

## 7. Open items before scaling
- Confirm model tier per stage (bulk vs review).
- Per-chapter briefs for the 4 chapter-only TOCs (or rely on pipeline planning stage).
- Illustration budget (gemini-imagegen) per book.
- Decide whether to also migrate the 5 existing books' footers to runtime `book.json` injection
  (current `apply_meta.py` already gives one-command propagation).
