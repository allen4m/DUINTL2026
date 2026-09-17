# Handoff: international.drury.edu — Home page redesign (direction 3a)

## Overview
Redesign of the home page of `international.drury.edu` (Drury University, Office of International
Admission) for a refined, modern, academia-friendly UX. The page is story-led: it leads with the
institution's promise, then a named international student's own words, then the three-credential
academic claim, campus, and a clear next-steps block.

The site is Astro v5, statically generated, published under six locales:
`/en/ /es/ /ja/ /pt/ /vi/ /zh/`. Every string and every layout decision in this handoff must
survive translation into all six.

## About the Design Files
The file in this bundle is a **design reference created in HTML** — a prototype showing intended
structure and hierarchy, not production code to copy. The task is to **recreate the chosen design
in the existing Astro codebase**, using its established components, layout primitives, and
styling approach. Do not port the prototype's markup or its sketch-style CSS.

## Fidelity
**Low-fidelity.** These are wireframes. Grey bars stand in for real copy, hatched rectangles for
photography, and the handwriting-style font (Caveat) is a wireframe convention only — it is **not**
a type choice and must not ship. Use them for layout, order, and hierarchy; apply Drury's real
brand system (typography, crimson, spacing) for styling. Crimson `#8c1d2c` in the wireframes is a
placeholder for Drury's official brand crimson — pull the exact value from the brand system.

## The chosen direction: 3a
Turn 3, option **3a** in `Drury International Wireframes.dc.html`.

It is option 2a's page structure with the hero line from option 2b. Two heroes were compared:
- **3a (chosen)** — headline in a text hero above the photo; the student quote becomes the photo caption.
- **3b (not chosen)** — headline and quote both inside one full-bleed photo hero.

3a was chosen because the institutional promise and the individual voice are two separate claims
and each needs its own room; because a text hero survives all six locales without headline text
colliding with a face; and because it does not depend on sourcing a portrait with clean negative
space in exactly the right place. 3b's treatment of the quote (a 2px crimson left rule with a
small-caps attribution below) should be reused for pull quotes **further down** the page.

## Screens / Views

### Home — `/{locale}/`
**Purpose:** a prospective international student (early research or ready to apply), a parent, an
overseas agent, or an admitted student arrives and must (a) believe Drury is academically credible,
(b) see real people and a real place, and (c) find their next action.

**Section order, top to bottom:**

1. **Header** — logo left; primary nav (Home, Admission, Student Support, Academics, Campus Life);
   language switcher; `Apply Now` button. Same nav as today; no IA change.

2. **Text hero** — on the page background, no photo.
   - Eyebrow: `DRURY UNIVERSITY · SPRINGFIELD, MISSOURI` — mono or letter-spaced small caps, ~0.08em tracking, crimson.
   - Headline: **"Fifty-one countries. One campus that knows your name."** Largest type on the page,
     tight leading (~1.13), measure capped around 12–14 words per line at desktop. This is new copy
     written for this redesign; Marketing should approve it, and the "fifty-one" figure must stay in
     sync with the countries stat below (spell it out in English, follow local convention in other locales).
   - Buttons: primary `Begin Your Application` → `https://apply.drury.edu/apply/`;
     secondary `Requirements` → `/{locale}/admission/#requirements`.

3. **Full-bleed portrait with caption overlay** — a single student portrait, roughly 16:10 at desktop,
   caption block bottom-left over the image.
   - Credential string, all caps, letter-spaced, crimson: e.g. `ARCHITECTURE | SUSTAINABILITY | INT'L IMMERSION`.
     This pattern is lifted directly from the viewbook's "Make it Yours" spread.
   - Quote, ~2/3 the headline size: e.g. *"I came from Vietnam to build spaces that hold a community together."*
   - Attribution, small caps: `ANH VI · VIETNAM · CLASS OF '25`, followed by an inline `Read her story →` link.
   - **Contrast requirement:** caption text sits on photography, so it needs a solid legibility
     treatment — a scrim, a gradient, or a solid caption panel. Do not rely on alpha-reduced text.
     Target 4.5:1 for the quote and attribution.
   - Anh Vi's story and credentials come from the viewbook (page 5). Get her permission before
     reusing the quote, and confirm the quote wording with Marketing — the line above is a paraphrase
     written for the wireframe, not her verbatim words.

4. **Stat band** — four equal cells, hairline dividers between, on a subtle off-white ground.
   `51` countries · `13:1` faculty ratio · `3` credentials · `1873` founded.
   Figure large in brand crimson, label small and muted beneath. Collapses to 2×2 on mobile.

5. **"Make it Yours"** — student profile cards, two per row at desktop.
   Each card: photo, credential string (caps, crimson), `NAME, COUNTRY`, two lines of summary.
   Section footer link: `All student stories →`. Needs a story index page to link to; if that page
   does not exist yet, flag it — this direction depends on having 4–6 real profiles.

6. **"Set Yourself Apart"** — inverted section, near-black ground.
   Heading, then the line "Every student graduates with three credentials in 124 hours," then three
   bordered cells: **Major**, **Certificate**, **Your choice**. Footer link `80+ programs of study →`
   → `/{locale}/drury-fusion/`. Copy is from the viewbook (page 3); it replaces the current site's
   softer "Drury Fusion" paragraph.
   This is the only dark section on the page — it carries the academic-credibility weight.

7. **"Come Home to Campus"** — photo cluster: one large image (2fr) plus two stacked smaller ones
   (1fr), then two lines of body copy. Springfield/campus content per the viewbook (page 2).

8. **"Your Next Steps"** — off-white ground. Four items, each prefixed with a `›` glyph
   (the viewbook's bullet). Then primary `Apply Now` and secondary `Ask a question`
   (`mailto:iadmissions@drury.edu`, or the existing contact route).
   Suggested items, to be confirmed: check requirements · apply · scholarships & costs ·
   I-20 and visa interview.

9. **Footer** — dark, unchanged from the current site (contact block, WhatsApp, mailing address,
   four link columns, social row).

## Interactions & Behavior
No new interaction patterns are introduced. Everything is a link or a button.
- Language switcher: existing behavior; keep the locale prefix on every internal link.
- Student cards and the portrait caption link to individual story pages.
- Hover states: whatever the existing codebase uses. Keep focus rings visible — this audience is
  keyboard- and screen-reader-diverse and the current site already has a skip link to preserve.
- Reduced motion: nothing on this page should require animation. If any is added, respect
  `prefers-reduced-motion`.
- Responsive: single column under ~768px; stat band 4 → 2×2; profile cards 2 → 1;
  campus cluster stacks; hero headline steps down but stays the largest type on the page.

## State Management
None. This is a static page. The only stateful concern is locale, already handled by Astro routing.

## Design Tokens
Wireframe values, for structure only — replace colors and type with the Drury brand system:

- Crimson (placeholder for brand crimson): `#8c1d2c`
- Near-black (inverted section, footer): `#1a1a1a`
- Page background: `#f0eee9` · subtle section ground: `#faf9f6`
- Hairline / border: `#e3e1dc` · muted text: `#7a746d` · secondary text: `#57524c`
- Placeholder bar fills: `#dcd8d1`, `#cfcbc4`
- Radius: 3–4px on cards and buttons (wireframe used near-square corners deliberately)
- Section padding: ~18px vertical at wireframe scale — read as generous, roughly 64–96px at desktop
- Type: **do not use Caveat.** Wireframe font only.

## Assets
- Existing site images: `DruryHome.webp`, `Druryfusion.webp`, `Academics.webp`, `CTA.webp`,
  `fav/office-logo.webp`, `fav/office-logo-white.webp`.
- The full image set from the **2026 Admission Viewbook** is available from the user
  (~19 files, including `Anh.jpeg` and `mikayla.jpg` — the two named students from the viewbook —
  plus campus, aerial, lab, stairwell, and graduation photography, and an apply QR code SVG).
  Request those files. Photography is a mix of existing and new; every hatched rectangle in the
  wireframe is a real photo slot, and the portrait hero in particular needs a strong portrait.
- No new icons. The `›` and `→` glyphs are text characters, matching the viewbook.

## Staff profile pages
Two staff profile pages share one template: `Drury International Allen Long.dc.html` (Director of
International Admission) and `Drury International Kunti Bentley.dc.html` (Director of Student
Support Services). Build them as one component with different content.

Shared structure: hero with a large rectangular portrait (left) beside name, title, a bordered
contact rectangle of eyebrow-plus-value cells, and a single primary button; lead paragraphs; a
two-column labeled list (duties or services); a dark "get in touch" band; cross-links.

Kunti's portrait is a placeholder. **It must match Allen's portrait treatment** — eye level,
subject filling the frame, same aspect and crop, so the two pages read as one series. Allen's
current image is a low-resolution square avatar hot-linked from the live site and needs replacing
with a high-resolution file at the same time.

## Source material
- Live site content and IA: `https://international.drury.edu/en/`
- `2026 Admission Viewbook - FINAL.pdf` — the redesign deliberately borrows its voice:
  two-word imperative headlines ("Come Home to Campus", "Set Yourself Apart", "Make it Yours",
  "Own the Traditions", "Find Your Forever Friends", "Your Next Steps"), `›` bullets, oversized
  figures, and ALL-CAPS student names with pipe-separated credential strings.
  Keep new copy in that register.

## Files
- `3a-chosen-direction.png` — screenshot of the chosen direction, full page.
- `3b-alternate-hero.png` — screenshot of the rejected hero alternative, for context.
- `Drury International Wireframes.dc.html` — all wireframe turns. **Direction 3a is the one to
  build**; it is in the section headed `3`, the first option. Earlier turns (1a–1d, 2a–2c, 3b) are
  rejected explorations, retained only as context for why 3a looks the way it does.
