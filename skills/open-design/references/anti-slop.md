# Anti-AI-slop blacklist + content philosophy

The rules in this file describe the visual + copy patterns that mark output as "obviously made by an AI without taste". Read this before shipping any artifact. Anything on the **hard blacklist** is a P0 fail (see `checklist.md` § P0-4). Anything on the **soft list** is a P1 — fix unless the brief specifically asks for it.

---

## Hard blacklist (P0 — never ship with these)

### Visual
- **Aggressive purple / violet gradient backgrounds.** A blurred radial gradient from indigo to magenta is the single most "AI-generated" pattern. Use a flat surface, a hairline gradient `oklch()` shift, or nothing.
- **Generic emoji as feature icons.** ✨ 🚀 🎯 💡 ⚡ in a row of feature cards. Use simple geometric SVGs, monogram letters, numbered badges, or no icons at all.
- **Rounded card with a left coloured border accent.** The "Bootstrap alert" feature card. If you need a card, use a hairline border + ample padding; if you need to call attention, use the accent on a small glyph or eyebrow inside.
- **Hand-drawn SVG humans / faces / scenery.** AI-generated stick figures or "diverse team" illustrations. Use real photography placeholders (labelled grey blocks: "[Hero photograph — 16:9]") or pure typography.
- **A gradient on every background.** If three sections all have gradients, you've smeared the whole page. One gradient maximum, ideally none.
- **An icon next to every heading.** Headings carry their own weight via type. An icon at every H2 is decorative noise.
- **Drop shadows on every card.** Elevation should be earned. Modals, dropdowns, tooltips — yes. Content cards — no, use hairline borders.

### Typography
- **Inter / Roboto / Arial as a *display* face.** They are body fonts. As display they communicate "default", which means generic. Use a serif (`Iowan Old Style`, `Newsreader`, `Charter`) or a confident geometric sans (`SF Pro Display`, `IBM Plex Sans`) for display.
- **Mixing 4+ font families.** Two is correct (display + body). Three is the absolute limit (display + body + mono). Four is chaos.
- **Right-aligning long-form prose.** Body text is left-aligned. Always.

### Copy
- **Filler placeholder.** "Feature One / Feature Two / Feature Three", "Lorem ipsum dolor sit amet", "Your tagline here".
- **Invented metrics.** "10× faster", "99.9% uptime", "Trusted by Fortune 500", "1M+ users", "Save 40% on your bills" — without a source from the brief. **Honest placeholders > fake stats.**
- **Generic tagline-ese.** "Empower your team to ship faster", "The all-in-one platform for X", "Beautifully designed, thoughtfully crafted". Specificity beats fluency.
- **"Click here" / "Learn more" CTAs.** Be specific: "Read the Q3 update", "Try the demo", "Book a 30-min call".

---

## Soft list (P1 — fix unless the brief asks for it)

### Visual
- **Centered single-column landing pages.** Default web-design instinct, especially for "AI" products. Asymmetric layouts (60/40, 70/30, off-center heroes) feel designed.
- **Glassmorphism / frosted blur on hero panels.** Date-stamped 2021. Use it sparingly — modal backdrops, sticky nav — never a primary hero treatment.
- **Neumorphism / soft 3D buttons.** Date-stamped 2020. Stick to flat surfaces with hairline borders.
- **Tilt-card interactions.** Hover-tilt effects on feature cards or testimonials. Once novel, now AI-template.
- **Confetti / particle background animations.** A red flag for "made in 30 minutes with a template". One decisive motion beats fifteen.
- **Avatar grids of stock photos** for "team" or "testimonials". Use real names + real photos OR initial-circle monograms with real names.

### Typography
- **All-caps headlines for H1/H2.** Reserve all-caps for kickers, eyebrows, navigation labels, and short utility lines (≤ 4 words).
- **`text-shadow` on display type.** Use weight + color + size to create hierarchy, not 1980s shadow effects.
- **Italics for emphasis at every paragraph.** Sparingly. The eye stops noticing after the third paragraph.

### Copy
- **Acronym soup product names.** "Welcome to OPEN-AI-DESIGN" instead of "Welcome to Open Design". Use the brief's actual product name, not an inflated initialism.
- **Quoting numbers without context.** "$2.3M raised" is meaningful; "1,847 happy customers" is not. If the number isn't the point, leave it out.
- **Three-bullet feature blocks where each bullet is the same shape.** "Easy to use · Fast to set up · Built for teams" — these say nothing. Make each bullet specific to a different facet of the product.

---

## Content philosophy

### Honest placeholders > fake stats

When you don't have a real value, leave a short honest placeholder:

- `—` (em-dash) for a missing number.
- `[Client name]` / `[Quote from launch interview]` for missing copy.
- A labelled grey block (`<div class="placeholder">[Product hero image — 16:9]</div>`) for a missing image.

The user can fill these in themselves. They cannot un-trust a fabricated metric.

### Vocalize the system up front

Before building, state in one sentence what visual system you're using ("warm cream background, single rust accent at oklch(58% 0.15 35), Newsreader display + system body, hairline borders, no shadows"). This gives the user a chance to redirect cheaply — three seconds of reading vs five minutes of waiting for the wrong direction.

### Variations, not "the answer"

When the brief is exploratory, default to 2–3 differentiated directions on the same page — different colour temperature, different type personality, different rhythm. Side-by-side beats sequential.

### Junior pass first

Show something visible early, even if it is a wireframe with grey blocks. Wrap it in `<artifact>`, label it "Wireframe v1 — early thinking, not final design", and let the user redirect. The cost of a wrong direction is one chat round, not one finished deck.

### One decisive flourish

A single orchestrated move — one orchestrated load animation, one striking pull quote, one piece of real photography, one moment of asymmetry — separates work from a sketch. Three competing flourishes turn it back into noise. *One thousand no's for every yes.*

### Embody the specialist

Pick the persona before writing CSS:

- **Slide deck** → slide designer. Fixed canvas, scale-to-fit, one idea per slide.
- **Mobile app** → interaction designer. Real frame, real hit targets, real screens.
- **Landing / marketing** → brand designer. One hero, three sections, real copy, one decisive flourish.
- **Dashboard / tool UI** → systems designer. Information density is the feature.
- **Editorial / blog** → magazine designer. Type carries 70% of the work.
- **Document template** → editor. Hierarchy, scan-ability, decision log.

The same six divs render differently when the persona is correct.

---

## Quick audit (run this in your head before emitting)

1. If I removed every gradient and every emoji, does the design still hold? *(If no: too dependent on visual crutches.)*
2. Is there one obvious focal point per screen? *(If no: hierarchy is broken.)*
3. Is every number, name, and date in the file specific to *this* brief? *(If no: filler crept in.)*
4. Did I commit to one direction or hedge between two? *(If hedged: the user wanted a designer, not a sampler.)*
5. Is there exactly one decisive flourish? *(Zero: too safe. Two+: too noisy.)*
