# Surface playbooks (the 19-skill catalog, distilled)

Each section below is a self-contained playbook for one design surface. Pick the one matching the user's `output` answer and the surface picker table in `SKILL.md`. Read it end-to-end before writing code for that surface.

Common rules across all playbooks:

- Single self-contained HTML file. Inline all CSS. No external CSS files. No external JS unless explicitly pinned (React/Babel — see `SKILL.md`).
- Tag landmarks with `data-od-id="<region>"` (e.g. `data-od-id="hero"`, `data-od-id="pricing"`) so the workspace can target individual sections.
- Bind the active design system or chosen direction's tokens into `:root`. Never invent palette tokens.
- Honest placeholders > fake stats. `—` or a labelled grey block beats "10× faster".
- Emit between `<artifact>` tags at the end of the turn. One sentence before, nothing after.

---

## `web-prototype` — generic single-page desktop prototype

**When:** "prototype", "mockup", "landing", "single page", "marketing page", "homepage" — and no more specific skill matches.

**Mode:** prototype · **Platform:** desktop · **Default for:** prototype mode.

**Workflow:**

1. **Read** the active DESIGN.md (if any). Map its colors to the six `:root` variables (`--bg`, `--surface`, `--fg`, `--muted`, `--border`, `--accent`); don't introduce new tokens.
2. **Plan** a 4–7 section list: nav · hero · 3–5 content sections · footer. State it before writing.
3. **Compose** the page from these section archetypes (one each, max one repeat):
   - **Nav** — wordmark, 4–6 links, primary CTA at the right, hairline border-bottom.
   - **Hero** — eyebrow + headline + 1-line deck + 2 CTAs + a single visual placeholder. No gradient.
   - **Feature row** — 3 columns, each with a short label + 1-sentence description. Numerals or icons (not emoji).
   - **Content split** — 60/40 prose + image/visual placeholder.
   - **Logo bar / Quote** — social proof.
   - **Pricing strip** — 2–3 tiers if relevant.
   - **CTA band** — single big sentence + button.
   - **Footer** — small wordmark, 3–4 link columns, legal line.
4. **Self-check:** type hierarchy unambiguous; line length 60–75ch on prose; accent at most twice; no AI-slop tropes (`references/anti-slop.md`).

---

## `saas-landing` — hero / features / pricing / CTA marketing page

**When:** "saas landing", "hero / features / pricing / CTA", a B2B SaaS-shaped marketing brief.

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Read DESIGN.md.
2. Sections, in this order: nav · hero · logo bar · 3-up feature grid · feature deep-dive (split) · stats strip · pricing (3 tiers) · testimonial · CTA band · footer.
3. The hero: one display headline (≤ 12 words), one-line deck, two buttons (primary + secondary), one product visual placeholder.
4. The pricing: three tiers, mid one as "popular" via a small accent border (not a different background), bullet feature list, one CTA per card.
5. Self-check: ≥ 7 sections present, accent count ≤ 4 across the page, no purple gradient, no left-border accent cards.

---

## `dashboard` — admin / analytics with sidebar

**When:** "dashboard", "admin", "analytics UI", "tool UI".

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Read DESIGN.md. Lean into `tech-utility` posture (mono numerics, hairline borders).
2. Layout: left sidebar nav (240px) + top bar + main grid.
3. Main grid: 4 KPI cards (top row), 1 large chart (60% width) + 1 list (40%) (middle), 1 data table (bottom).
4. Numerics in tabular-nums. Status uses tinted pills, not coloured backgrounds.
5. No hero. No marketing copy. Show the *product*, not a pitch for it.

---

## `pricing-page` — standalone pricing + comparison table

**When:** "pricing", "comparison table", a standalone pricing page.

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Sections: small nav · headline + deck · 3-tier card grid · compare table · FAQ · footer CTA.
2. Tier cards: name, price (large display), 1-line "for who" tag, 5–8 bullet features, primary CTA.
3. Compare table: rows are features, columns are tiers. Use `—` and `✓` (or hairline `−` and a filled square), not big colour blocks.
4. FAQ: 5–8 collapsible Q&As (default open on first 2).

---

## `docs-page` — 3-column documentation layout

**When:** "docs", "documentation", "API reference".

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. 3-column grid: left nav (240px) + content (max-width 720px) + right TOC (200px).
2. Content: H1, 2-paragraph intro, 4–6 H2 sections each with prose + one code block + one callout.
3. Code blocks: use the design system's mono font, `:root --font-mono` if defined.
4. No hero. Functional > decorative.

---

## `blog-post` — editorial long-form

**When:** "blog", "blog post", "article", "essay", "case study", "newsletter".

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Read DESIGN.md. Lean into typography — long-form is 70% type, 20% image, 10% chrome.
2. Pick a real topic from the brief and write a real article — at least 600 words across 4–6 H2 sections. **No lorem ipsum.**
3. Sections, in order:
   - **Masthead** — small wordmark + 4–6 nav links, plain.
   - **Article header** — category eyebrow, headline (display token, large), deck (1–2 sentence subhead), author name + role + date.
   - **Hero image** — a 16:9 placeholder block using a DS-tinted gradient or solid fill (no external images). Add a 1-line caption underneath.
   - **Body** — alternating prose paragraphs with at least: 1 pull quote (large display type, accent rule on the left), 1 figure (image placeholder + caption), 1 list (numbered or bulleted), 1 inline blockquote.
   - **Author footer** — author avatar (initials in a circle), bio paragraph.
   - **Related** — 3 cards linking to other posts. Each card: tiny image block, title, 1-line excerpt, date.
4. Self-check: type hierarchy unambiguous; line length 60–75 chars for body prose; accent at most twice; reads like a magazine, not a marketing landing.

---

## `mobile-app` — single phone-frame screen

**When:** "mobile app", "iOS app", "Android app", "phone screen", "app UI", "app mockup", a single mobile screen.

**Mode:** prototype · **Platform:** mobile.

**Workflow:**

1. Build a pixel-accurate iPhone 15 Pro chrome around the screen: 390 × 844 viewport, Dynamic Island, status bar (time / signal / wifi / battery SVGs), home indicator. Center the device on the page on a soft showcase background.
2. Bind DS or direction tokens. Increase base font size by ~1pt for mobile readability.
3. Pick one screen archetype: feed · detail · onboarding · paywall · settings · profile.
4. Hit targets ≥ 44px. Tap zones are obvious.
5. Single screen — no nav between screens. For multi-screen, use `mobile-onboarding` or the multi-frame gallery pattern in `SKILL.md` § H.

---

## `mobile-onboarding` — three-frame mobile flow

**When:** "mobile onboarding", "splash + value-prop + sign-in", a 3-frame onboarding sequence.

**Mode:** prototype · **Platform:** mobile.

**Workflow:**

1. Three iPhone 15 Pro frames side by side on a showcase background.
2. Frame 1 — splash (logo + 1 line of mood copy). Frame 2 — value-prop (illustration placeholder + headline + 3 bullet rows). Frame 3 — sign-in (email + password + primary CTA + small "skip" link).
3. Status bar, swipe dots (3 dots, second filled on frame 2), primary CTA on each.
4. Hit targets 44px+. CTA copy is specific ("Get started", "Continue", not "Click me").

---

## `dating-web` — matchmaking dashboard

**When:** "dating app", "match dashboard", consumer matchmaking surface.

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Layout: left rail nav (icons + labels) + top ticker bar + main 3-row grid.
2. Main grid: top row of 3 KPI cards (matches today, mutual likes, conversion %); middle 30-day mutual-matches chart; bottom recent-matches list with avatars.
3. Editorial typography (serif display + system body) — set the tone away from generic SaaS.
4. Avoid pink-purple gradient. Use a single warm accent (`warm-soft` or `editorial-monocle` direction).

---

## `gamified-app` — XP / level / quest mobile

**When:** "gamified app", "quests", "XP / level", a gamified mobile prototype.

**Mode:** prototype · **Platform:** mobile.

**Workflow:**

1. Three iPhone 15 Pro frames on a dark showcase stage.
2. Frame 1 — cover (mascot or hero illustration placeholder + headline). Frame 2 — today's quests (3–5 quest rows with XP ribbons + level progress bar at top). Frame 3 — quest detail (large goal, progress meter, primary CTA "Start quest").
3. XP ribbons use a single accent + tinted background. Level bar shows next-level threshold.
4. Avoid generic emoji as quest icons — use simple SVG glyphs or numeric badges.

---

## `email-marketing` — single-column HTML email

**When:** "email marketing", "HTML email", "product launch email".

**Mode:** prototype · **Platform:** email.

**Workflow:**

1. Centered single-column 600px-wide table-fallback layout (use `<table>` for outer wrappers; modern CSS Grid only inside cells).
2. Sections: masthead (wordmark + 1-line nav), hero image placeholder, headline lockup (eyebrow + display headline + deck), 1 primary CTA button, 4-cell specs grid, footer with unsubscribe + address.
3. Inline all styles on each element (gmail strips `<style>` blocks). Use system font stacks only.
4. Test mentally: would this render acceptably in plain-text fallback?

---

## `magazine-poster` — editorial / print poster

**When:** "magazine poster", "editorial poster", "print poster", a single-canvas editorial composition.

**Mode:** prototype · **Platform:** print/canvas.

**Workflow:**

1. Fixed canvas: A2 (1654×2339 @ 200dpi) or 1080×1620 (Instagram-friendly portrait). State the choice up front.
2. Composition: one oversized serif display headline + one image placeholder (full-bleed or framed) + one short body block + 2–3 metadata lines (date, issue, author).
3. Lean into `editorial-monocle` or `brutalist-experimental` direction. No gradients. No SVG humans.
4. Use `text-wrap: balance` on the headline. Hyphenation off.

---

## `social-carousel` — three 1080×1080 cards

**When:** "social carousel", "Instagram carousel", "1080×1080".

**Mode:** prototype · **Platform:** social.

**Workflow:**

1. Three 1080×1080 panels arranged horizontally on a dark page background.
2. Each panel: full-bleed cinematic background (gradient OR placeholder solid OR DS-tinted), display headline that connects across the series (e.g. "Type." → "Hit enter." → "Ship."), brand mark in a corner, subtle loop affordance arrow on panel 3.
3. Display sizes ≥ 80px (it'll be viewed on phone).
4. One accent across all three. Theme rhythm: don't repeat the same composition twice.

---

## `motion-frames` — single-frame motion-design hero

**When:** "motion frame", "looping CSS animation hero".

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. One full-bleed hero composition with looping CSS keyframes (no JS).
2. Three motion elements: e.g. rotating display-type ring, animated globe (CSS-drawn, not SVG humans), ticking timer (`steps()` animation on a digit).
3. All motion is `animation-iteration-count: infinite` and respects `prefers-reduced-motion: reduce` (set `animation: none`).
4. Hand-off ready: comment which keyframes correspond to which motion track.

---

## `sprite-animation` — pixel / 8-bit explainer slide

**When:** "sprite animation", "pixel / 8-bit explainer".

**Mode:** prototype · **Platform:** desktop / slide.

**Workflow:**

1. Full-bleed cream stage. One animated pixel mascot (CSS-drawn from a grid of `box-shadow` pixels OR a sprite-sheet `background-position` keyframe).
2. Kinetic Japanese display type or oversized monospaced display headline alongside.
3. Looping CSS keyframes — no JS animation.
4. Pixel-perfect: `image-rendering: pixelated` on any raster, integer transforms only.

---

## `digital-eguide` — two-spread digital e-guide

**When:** "digital eguide", "lesson spread", "creator e-guide".

**Mode:** template · **Platform:** desktop / tablet.

**Workflow:**

1. Two horizontally-arranged page spreads (each ~ 8.5×11 portrait).
2. Spread 1 — cover: title (display, large), author byline, TOC teaser (3–5 lesson titles).
3. Spread 2 — lesson spread: lesson number eyebrow, headline, 1 pull quote, body prose (2 columns), step list (numbered, 3–5 steps).
4. Creator / lifestyle tone: `warm-soft` or `editorial-monocle`. Generous margins.

---

## `wireframe-sketch` — lo-fi wireframe

**When:** "wireframe", "lo-fi", "sketch", an explicitly low-fidelity exploratory pass.

**Mode:** prototype · **Platform:** any.

**Workflow:**

1. Greyscale only — no accent. Type stays the DS body font.
2. Replace images with labelled grey blocks (`<div class="block">[Hero image — 16:9]</div>`).
3. Hand-drawn feel: dashed 1.5px borders, 2–4px radii. No shadows.
4. Header explicitly says "Wireframe v1 — early thinking, not final design."
5. Use this as the **junior-pass first** vehicle (`SKILL.md` § E).

---

## `tweaks` — single page with a floating Tweaks panel

**When:** "design variants", "tweaks", side-by-side variations on one page.

**Mode:** prototype · **Platform:** desktop.

**Workflow:**

1. Build the base prototype as usual (any of the prototype playbooks above).
2. Add a small floating Tweaks panel (top-right, 280px wide, frosted-glass background) exposing 3–5 design knobs:
   - Primary color (color picker)
   - Type scale (slider 0.85–1.2)
   - Dark mode (toggle)
   - Layout variant (radio: compact / standard / spacious)
3. Wrap the defaults in marker comments for persistence:
   ```js
   const TWEAK_DEFAULTS = /*EDITMODE-BEGIN*/{
     "primaryColor": "#D97757",
     "fontSize": 16,
     "darkMode": false,
     "layout": "standard"
   }/*EDITMODE-END*/;
   ```
4. Persist Tweaks state in localStorage. Apply via CSS variables on `:root`.
5. The panel collapses to a small floating button when not in use.

---

## `simple-deck` — minimal horizontal-swipe deck

**When:** "deck" / "slides" with a minimal aesthetic, OR no specific deck system requested.

**Mode:** deck · **Platform:** fixed canvas.

**Workflow:**

1. Copy the deck framework HTML from [`deck-framework.md`](deck-framework.md) **verbatim**.
2. Fill the `<section class="slide">` slots only. Do NOT modify the framework's scaling JS, keyboard handler, counter, or print stylesheet.
3. Slide types (rotate to avoid 3+ same-theme in a row): cover · agenda · big-stat · two-up · table · quote · ending.
4. Theme tokens in the SECOND `<style>` block (per-deck styles) — never edit the first `<style>` (framework styles).
5. Headlines ≥ 56px. Body ≥ 28px. Slide counter visible.
6. Use `data-screen-label="01 Title"` on each slide.

---

## `guizang-ppt` — magazine-style web PPT (deck default for editorial briefs)

**When:** "deck" / "slides" with a magazine / editorial aesthetic, pitch decks, design-forward presentations.

**Mode:** deck · **Platform:** fixed canvas · **Default for:** deck mode (when bundled).

**Workflow:**

1. Same framework copy from [`deck-framework.md`](deck-framework.md) — start there.
2. Magazine layouts: full-bleed photo + title-card, two-column editorial spreads, oversized pull quotes, big-stat slides with one giant number + one paragraph of context, table-of-contents slides with eyebrow + ordered list.
3. WebGL hero background on the cover (a single subtle gradient blob via canvas) — gracefully degrade if WebGL unavailable.
4. Lean serif display + sans body. Treat the deck like a printed magazine: every slide should feel like a spread, not a screen.
5. Theme rhythm enforced: alternate big-stat / two-up / quote / image-slide types.

---

## `pm-spec` — PM specification document

**When:** "PM spec", "product spec", "PRD".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Single-column document layout, max-width 760px, generous line-height.
2. Sections: title block (project name + status badge + author + date) · TL;DR (3 sentences) · context · goals (numbered list) · non-goals · proposed solution · open questions · decision log table · appendix.
3. Status badge: `Draft` / `Review` / `Approved` (tinted pill, not a coloured background).
4. Decision log: 3-column table (Date · Decision · Owner). Real entries, not placeholders.

---

## `weekly-update` — team weekly with progress / blockers / next

**When:** "weekly update", "team weekly".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: team name + week-of date + author.
2. Three sections in this order: **Progress** (3–5 bullets, each with owner) · **Blockers** (numbered, with severity tag) · **Next week** (3–5 bullets).
3. Optional: a tiny KPI strip at the top (3–4 numbers with delta arrows).
4. Narrative tone, not bureaucratic. Keep it under one printed page.

---

## `team-okrs` — OKR scoresheet

**When:** "OKRs", "team OKRs", "scoresheet".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: team + quarter.
2. 3–5 Objectives, each with 3 Key Results.
3. Each KR row: KR text · target · current · % progress (with a tinted progress bar) · owner.
4. Color the progress bar in the accent at most; muted grey for the rail.

---

## `kanban-board` — board snapshot

**When:** "kanban", "board snapshot".

**Mode:** template · **Platform:** desktop.

**Workflow:**

1. 4-column grid: Backlog · In progress · Review · Done.
2. Each card: title (1 line), 1-line description, owner avatar (initials), 0–3 tags, due date.
3. WIP count in each column header (e.g. "In progress · 4").
4. Hairline borders between columns. Cards with subtle surface backgrounds, no shadows.

---

## `meeting-notes` — decision log

**When:** "meeting notes", "decision log".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: meeting title + date + attendees (initials).
2. Sections: **Agenda** (numbered) · **Discussion** (one bullet per agenda item, with sub-bullets) · **Decisions** (table: Decision · Owner · Date) · **Action items** (table: Action · Owner · Due).
3. Decisions and action items always in tables — they're scannable.

---

## `eng-runbook` — incident / engineering runbook

**When:** "runbook", "incident runbook", "engineering runbook".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: incident or system name + severity badge + on-call.
2. Sections: **Symptoms** (bullet list, observable signals) · **Diagnosis** (numbered steps with checkboxes) · **Mitigation** (numbered steps with mono-formatted shell commands) · **Postmortem template** (linked at bottom).
3. Mono font for commands. Severity badge tint matches accent.
4. No marketing tone. This is a tool.

---

## `finance-report` — exec finance summary

**When:** "finance report", "exec finance summary".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: company + period.
2. Executive summary paragraph (3 sentences).
3. KPI strip: revenue · net income · cash · runway (mono numerics, deltas vs prior period).
4. 2-column body: P&L summary table (left) + cash-flow chart placeholder (right).
5. Appendix: notes table.

---

## `hr-onboarding` — role onboarding plan

**When:** "HR onboarding", "role onboarding".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Title block: role + start date + buddy.
2. Sections: **Week 1** (4–6 items with owner) · **Week 2** (4–6 items) · **Day 30** (3 outcomes) · **Day 60** (3 outcomes) · **Day 90** (3 outcomes).
3. Each item is checkable (`□`). Tone is welcoming, not corporate.
4. Optional intro paragraph from the manager.

---

## `invoice` — single-page invoice

**When:** "invoice", "single-page invoice".

**Mode:** template · **Platform:** desktop / print.

**Workflow:**

1. Header: from (company + address) · to (client + address) · invoice number · issue date · due date.
2. Line-items table: Description · Qty · Rate · Amount. Tabular numerics.
3. Totals stack (right-aligned): Subtotal · Tax · Total.
4. Footer: payment instructions + thank-you line.
5. Print-friendly: A4-safe margins, no background colours.

---

## `critique` — design critique / 5-dimensional review

**When:** "design review", "design critique", "5-dim review".

**Mode:** review · **Platform:** any.

**Workflow:**

1. Read the artifact under review (HTML file, screenshot, URL).
2. Score across 5 dimensions on a 1–10 scale (note: the live critique inside RULE 3 step 8 uses 1–5; the standalone review surface uses 1–10 for finer resolution):
   - **Philosophy consistency** — does it commit to a single visual posture?
   - **Visual hierarchy** — is there one obvious focal point per screen?
   - **Detail execution** — type, spacing, alignment, contrast, micro-interactions.
   - **Functionality** — does the design match its job?
   - **Innovation** — is there one decisive flourish, or is it generic?
3. Render the score as a radar chart (CSS or SVG, no chart libs).
4. Output three lists: **Keep** (what's working) · **Fix** (P0 / P1 issues with concrete suggestions) · **Quick wins** (5-minute upgrades).
5. Tone: collegial, specific, actionable. No hedging ("could be better"); say what to do.

---

## When in doubt

If the brief doesn't cleanly match any of the 19 surfaces above, default to `web-prototype` and adapt. If the brief is for a *deck-shaped* output (slides, presentation, pitch), default to `simple-deck` (or `guizang-ppt` if the user wants editorial / magazine).
