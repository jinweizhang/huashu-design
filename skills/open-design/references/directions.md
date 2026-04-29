# Direction library — bind into `:root` when the user picks one

Five curated visual directions, distilled from `huashu-design`'s "5 schools × 20 philosophies" idea. Each ships a CSS-ready palette in OKLch and font stacks. When the user selects one in the direction-form, replace the seed template's `:root` block with that direction's palette and font stacks **verbatim** — do not improvise. Posture cues describe how that direction *behaves* (border weight, radius, accent budget); honour them in the layout choices.

The picker form options below match these ids exactly. Adding a new direction means adding one section here; the picker auto-includes it.

---

## Editorial — Monocle / FT magazine  `(id: editorial-monocle)`

**Mood:** Print-magazine feel. Generous whitespace, large serif headlines, restrained palette of off-white paper + ink + a single warm accent. Confident, quietly intelligent.

**References:** Monocle, The Financial Times Weekend, NYT Magazine, It's Nice That.

**Palette (drop into `:root`):**

```css
:root {
  --bg:      oklch(97% 0.012 80);
  --surface: oklch(99% 0.005 80);
  --fg:      oklch(20% 0.02 60);
  --muted:   oklch(48% 0.015 60);
  --border:  oklch(89% 0.012 80);
  --accent:  oklch(58% 0.16 35);

  --font-display: 'Iowan Old Style', 'Charter', Georgia, serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif;
}
```

**Posture:**
- serif display, sans body, mono for metadata only
- no shadows, no rounded cards — borders + whitespace do the work
- one decisive image, cropped only at the bottom
- kicker / eyebrow in mono uppercase, one accent color, used at most twice

---

## Modern minimal — Linear / Vercel  `(id: modern-minimal)`

**Mood:** Quiet, precise, software-native. System fonts, near-greyscale palette, a single saturated accent. The chrome disappears so content is the only thing that registers.

**References:** Linear, Vercel, Notion 2024, Stripe docs.

**Palette (drop into `:root`):**

```css
:root {
  --bg:      oklch(99% 0.002 240);
  --surface: oklch(100% 0 0);
  --fg:      oklch(18% 0.012 250);
  --muted:   oklch(54% 0.012 250);
  --border:  oklch(92% 0.005 250);
  --accent:  oklch(58% 0.18 255);

  --font-display: -apple-system, BlinkMacSystemFont, 'SF Pro Display', system-ui, sans-serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'SF Pro Text', system-ui, sans-serif;
}
```

**Posture:**
- tight letter-spacing on display sizes (-0.02em)
- hairline borders only, no shadows except dropdowns/modals
- mono numerics with `font-variant-numeric: tabular-nums`
- sticky frosted nav, content-led layouts (no hero illustrations)
- one accent: links + primary CTA, nothing else

---

## Warm & soft — Stripe pre-2020 / Headspace  `(id: warm-soft)`

**Mood:** Cream backgrounds, soft accent, gentle radii. Reads like a thoughtful product magazine — friendly without being cute. Good for fintech, wellness, indie SaaS.

**References:** Stripe pre-2020, Headspace, Substack, Mercury.

**Palette (drop into `:root`):**

```css
:root {
  --bg:      oklch(97% 0.018 70);
  --surface: oklch(99% 0.008 70);
  --fg:      oklch(22% 0.02 50);
  --muted:   oklch(50% 0.018 50);
  --border:  oklch(90% 0.014 70);
  --accent:  oklch(64% 0.13 28);

  --font-display: 'Tiempos Headline', 'Newsreader', 'Iowan Old Style', Georgia, serif;
  --font-body:    'Söhne', -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
}
```

**Posture:**
- serif display, soft sans body
- gentle radii (12–16px), no hard 0px corners on content cards
- single accent used for primary CTA + one editorial flourish (a quote mark, a stat)
- soft inner glow on hero cards rather than drop shadows
- avoid icons; use real screenshots / photographs / illustrations

---

## Tech / utility — Datadog / GitHub  `(id: tech-utility)`

**Mood:** Data-dense, monospace-friendly, dark or light + grid. Made for engineers and operators who want information per square inch, not vibes.

**References:** Datadog, GitHub, Cloudflare dashboard, Sentry.

**Palette (drop into `:root`):**

```css
:root {
  --bg:      oklch(98% 0.005 250);
  --surface: oklch(100% 0 0);
  --fg:      oklch(22% 0.02 240);
  --muted:   oklch(50% 0.018 240);
  --border:  oklch(90% 0.008 240);
  --accent:  oklch(58% 0.16 145);

  --font-display: -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', system-ui, sans-serif;
  --font-body:    -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', system-ui, sans-serif;
  --font-mono:    'JetBrains Mono', 'IBM Plex Mono', ui-monospace, Menlo, monospace;
}
```

**Posture:**
- sans display + sans body (one family) is OK here — utility trumps editorial
- tabular numerics everywhere, mono for code / IDs / hashes
- dense tables with hairline borders, no row striping
- inline status pills (success / warn / danger) with restrained tinted backgrounds
- avoid: hero images, oversized headlines, marketing copy — show the product instead

---

## Brutalist / experimental — Are.na / Yale  `(id: brutalist-experimental)`

**Mood:** Loud type. Visible grid. System sans + a single oversized serif. Deliberate ugliness as confidence. Great for art, indie, agency, manifesto pages.

**References:** Are.na, Yale Center for British Art, mschf, Read.cv.

**Palette (drop into `:root`):**

```css
:root {
  --bg:      oklch(96% 0.004 100);
  --surface: oklch(100% 0 0);
  --fg:      oklch(15% 0.02 100);
  --muted:   oklch(40% 0.02 100);
  --border:  oklch(15% 0.02 100);
  --accent:  oklch(60% 0.22 25);

  --font-display: 'Times New Roman', 'Iowan Old Style', Georgia, serif;
  --font-body:    ui-monospace, 'IBM Plex Mono', 'JetBrains Mono', Menlo, monospace;
}
```

**Posture:**
- display = serif at extreme sizes (clamp(80px, 12vw, 200px))
- body = monospace — yes, monospace as body, deliberately
- borders are full-strength fg (1.5–2px), not muted greys
- asymmetric layouts: one column 70%, the other 30%
- almost no border-radius (0–2px). No shadows. No gradients.
- underline links, no hover decoration — let the typography carry it

---

## Direction picker form (emit verbatim on RULE 2 Branch A)

```
<question-form id="direction" title="Pick a visual direction">
{
  "description": "No brand to match — pick a visual direction. Each one ships with a real palette, font stack, and layout posture. You can override the accent below.",
  "questions": [
    {
      "id": "direction",
      "label": "Direction",
      "type": "direction-cards",
      "required": true,
      "options": ["editorial-monocle", "modern-minimal", "warm-soft", "tech-utility", "brutalist-experimental"]
    },
    {
      "id": "accent_override",
      "label": "Accent override (optional)",
      "type": "text",
      "placeholder": "e.g. \"use moss green instead of cobalt\", \"no orange — too brand-y for us\""
    }
  ]
}
</question-form>
```

When the user picks an option, look up its id above and bind the palette + fonts verbatim. If they fill `accent_override`, replace `--accent` with the requested value (resolve named colors to OKLch — e.g. "moss green" → `oklch(55% 0.12 145)`).
