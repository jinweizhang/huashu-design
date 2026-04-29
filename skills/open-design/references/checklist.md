# Self-check P0 / P1 / P2 (run before emitting `<artifact>`)

This is the gate at RULE 3 step 7. Read it after writing the artifact, before scoring the 5-dim critique. Every **P0** must pass — if any fails, fix it before moving on. P1 issues are strong-recommend fixes. P2 issues are nice-to-have polish.

---

## P0 — must pass (blocks emit)

### P0-1 · The artifact is a single self-contained HTML document
- Wrapped in `<artifact identifier="..." type="text/html" title="...">…</artifact>`.
- One `<!doctype html>` through `</html>`.
- All CSS inline. No external CSS files.
- No external JS unless explicitly pinned (only React + Babel + ReactDOM at the documented versions).
- `</artifact>` is the **last** thing in your turn. No narration after.

### P0-2 · Tokens come from DESIGN.md or a chosen direction (not invented)
- The six color tokens (`--bg`, `--surface`, `--fg`, `--muted`, `--border`, `--accent`) are bound in `:root`.
- Their values match the active design system OR the direction the user picked (verbatim from `references/directions.md`).
- No hex values invented from memory. If you extended the palette, you used `oklch()` to derive harmonious values.

### P0-3 · No filler / no fake stats
- Zero lorem ipsum.
- Zero "Feature One / Feature Two / Feature Three" placeholder copy.
- Zero invented metrics ("10× faster", "99.9% uptime", "trusted by Fortune 500") without a source from the brief.
- Where a real value isn't known, an honest placeholder is used (`—`, a labelled grey block, "[client name]").

### P0-4 · No hard AI-slop tropes
- No aggressive purple / violet gradient backgrounds.
- No generic emoji feature icons (✨ 🚀 🎯 …).
- No rounded card with a left coloured border accent.
- No hand-drawn SVG humans / faces.
- Inter / Roboto / Arial are not used as a *display* face (body is fine).

### P0-5 · The output matches the surface
- Brief is a deck → output uses the deck framework (1920×1080 canvas, `.slide` sections, framework chrome). Not a scrolling web page.
- Brief is a mobile app → output renders inside a phone frame (iPhone 15 Pro, Dynamic Island, 390×844). Not a wide desktop layout.
- Brief is a dashboard → output is a sidebar + grid, with tabular numerics and hairline borders. Not a marketing hero.
- Brief is editorial / blog → output is single-column long-form, max-width ~720px. Not a feature grid.

### P0-6 · Deck-specific (only if the brief is a deck)
- The framework's first `<style>` block, `.deck-shell` / `.deck-stage` / `.slide` chrome, `@media print`, and the trailing `<script>` are **unmodified** vs `references/deck-framework.md`.
- The first slide has `class="slide active"`, the rest have `class="slide"` (no `active`).
- No custom `fit()`, `transform: scale()`, or keydown handler in per-deck code.
- Counter element IDs (`#deck-cur`, `#deck-total`, `#deck-prev`, `#deck-next`) are present and unchanged.

---

## P1 — strong recommend (fix unless you have a reason)

### P1-1 · Hierarchy is unambiguous
- One obvious focal point per screen / slide / page.
- H1 / display headlines clearly outrank H2 / section dividers — no two type sizes within 4px of each other competing.
- Pull quotes (when present) don't compete with the H1.

### P1-2 · Accent budget
- `--accent` is used at most twice per screen (e.g. eyebrow + primary CTA, or pull-quote rule + one link).
- Accent never appears as a background fill of a content-bearing block.

### P1-3 · Typography
- Display + body are different families (the only exception is `tech-utility`, which is intentionally one family).
- Body line length is 60–75 characters on prose blocks.
- Body line-height ≥ 1.5 on prose, ≥ 1.3 on UI.
- Tabular nums (`font-variant-numeric: tabular-nums`) on any column of numbers.

### P1-4 · Real content
- All copy is specific to the brief — names, products, dates, numbers.
- Where the user gave a brand, the brand name appears verbatim (no "Acme Inc.").
- Decision logs / tables / lists have at least 3 real entries, not 1 + "...".

### P1-5 · Mobile (if applicable)
- Hit targets ≥ 44 × 44 px.
- Text not smaller than 14 px (most body) / 12 px (metadata).
- Status bar SVGs (signal, wifi, battery) drawn pixel-aligned, not blurry.
- Home indicator on Face-ID iPhones (no home button).

### P1-6 · Slides (if applicable)
- Headlines ≥ 56 px.
- Body ≥ 28 px.
- Theme rhythm: no 3+ consecutive slides of the same theme (cover, big-stat, two-up, quote, table, ending should rotate).
- Slide labels follow `data-screen-label="NN Name"` and are 1-indexed.

---

## P2 — polish (fix if time)

### P2-1 · Modern CSS power moves
- `text-wrap: pretty` on prose, `text-wrap: balance` on display headlines.
- CSS Grid (not float / inline-block) for layout.
- `color-mix()` or `oklch()` for derived colors instead of new hex.

### P2-2 · One decisive flourish
- Exactly one orchestrated load animation, OR one striking pull quote, OR one piece of real photography — not three competing flourishes.
- That flourish is *intentional* — it shows up in your prose summary as a design choice.

### P2-3 · Tweaks panel (prototypes only)
- 3–5 design knobs exposed.
- Defaults wrapped in `/*EDITMODE-BEGIN*/ … /*EDITMODE-END*/` markers.
- State persists to localStorage.

### P2-4 · Dark mode (if requested)
- `prefers-color-scheme: dark` toggle ships with the file.
- All six tokens have dark equivalents in OKLch — no `filter: invert(1)` shortcuts.

### P2-5 · Reduced motion
- Any CSS animation respects `prefers-reduced-motion: reduce` (use `@media (prefers-reduced-motion: reduce) { * { animation: none !important; transition: none !important; } }`).

---

## How to use this checklist

1. After writing the artifact, scan the file once and answer each P0 yes/no.
2. Any P0 = no → fix it. Re-scan.
3. Any P1 = no → fix unless you can articulate why this artifact is the exception (in which case, mention it briefly in your one-sentence pre-amble before the artifact).
4. Hit P2 if you have time and the brief allows.
5. **Then** run the 5-dim critique (RULE 3 step 8). Then emit.
