# Graphic Assets

## The split: generate atmosphere, author interface

Not everything here should come from an image model.

**Generate** — #1, #2, #3, #7, #8, #9, #10. Static, decorative, never manipulated by
the user.

**Hand-author as SVG — do not generate** — #4 island silhouettes, #5 connection
symbols, #6 shell tokens. Their prompts are kept below as *art direction* for whoever
draws them.

The rule: **interactive means parameterized, and parameterized means vector.** Each of
those three gets resized, rotated, recoloured, or has text set inside it at arbitrary
scale. A raster cutout cannot take a terrain colour, cannot hold a word centred as the
shape grows, and will fringe on parchment. Image models are also genuinely unreliable
at true transparency and at "twelve separated silhouettes at consistent scale" — you
would burn generations and redraw them anyway.

The clincher is in the production notes below: an SVG fallback is already required for
exactly these three. If the fallback must exist, **the SVG is the asset** and the
raster is the thing you would delete.

## Everything is top-down. There is no horizon.

Tested 2026-08-11. The first round of prompts said "cinematic," "elevated angle,"
"seascape," and "sunrise at the horizon" — **every island-bearing asset came back as
alpine mountains** with contour hatching. Not bad luck: those words force a vista, and
"island + watercolour illustration" is a trained cluster that means volcanic peaks.

It also exposed a real incoherence in the brief. The canvas is top-down cartography —
you click water to add an island, you draw bridges across a map plane. A three-quarter
vista promises a different world than the product delivers.

**Ruling: the archipelago is always seen from directly overhead.** Dawn is a quality of
*light* — warm raking light, soft shadows under torn paper edges — never a sky.

This makes the hero stronger, not weaker. Top-down, the landing image stops being
decoration and becomes a **demonstration**: it shows the thing the user is about to
make.

### Prompt rules that came out of the test

1. Open with **"Viewed from directly overhead, flat top-down map."**
2. Ban the vista explicitly: *no horizon, no sky, no mountains, no peaks, no summits,
   no relief, no hills, no elevation, no perspective, no vanishing point.*
3. **Lead with material, then a sparse subject.** The best asset (#8) worked because
   the scene was nearly empty and the paper and ink did the work. Dense prompts drift.
4. Say **"flat layered cut-paper... soft torn edges... casting a faint shadow."**
   Without "flat" and "shadow," cut-paper loses to watercolour every time.
5. For anything sitting *behind* UI, ask for near-blankness outright: *"extremely pale,
   mostly empty parchment, nothing dark, nothing that would obscure text on top."*
   "Low contrast" alone is not enough — it produced a gorgeous, unusable illustration.
6. For the keepsake frame: *not aged, not sepia, not stained, not a treasure map, no
   seashells, no rope, no anchors.* It drifts to pirate-map pastiche otherwise.

### Tooling note

Recraft V4.1, `model_type: standard`, `resolution: 2k`, with the brand hexes passed in
`colors` — that palette lock is the strongest consistency lever available.

**Its `colors` array fails above six entries.** Documented as ten; seven or more
returns a silent submission failure. Pick the six that matter for each asset.

---

Generate each asset separately. Ask for high resolution, no text, no logos, no watermark, and generous empty space where UI or copy will sit. Keep one consistent art direction across all outputs: **mature handcrafted cartography at dawn, layered cut paper, delicate watercolor grain, fine ink contour lines, restrained colors, editorial rather than childish**.

## 1. Landing hero seascape

**Use:** Desktop hero background, 16:9.

> Wide cinematic dawn ocean viewed from a gentle elevated angle, an original archipelago of abstract layered paper islands floating in translucent blue-green water, delicate ink contour lines, subtle watercolor blooms and paper fibers, thin luminous currents suggesting connection and distance, warm coral and muted gold sunrise at the horizon, deep ink navy shadows, quiet reflective mood, sophisticated editorial illustration, mature and minimal, large calm negative space on the left for headline and buttons, visual detail concentrated toward the lower right, no people, no buildings, no text, no letters, no logo, no watermark, no cartoon tropical imagery, 16:9, high resolution

## 2. Mobile hero variation

**Use:** Mobile landing page, 9:16.

> Vertical dawn seascape in the same handcrafted paper-cartography style, one central irregular island and several smaller distant islands, translucent tidal currents, watercolor grain, ink contours, parchment and sea-glass palette with small coral and gold highlights, mature editorial illustration, calm negative space in the upper third for headline, detail in lower half, no text, no logo, no watermark, 9:16, high resolution

## 3. Seamless ocean texture

**Use:** Canvas background.

> Seamless tileable surface texture of calm abstract ocean seen from above, pale sea-glass and tidal teal watercolor washes on fibrous paper, extremely subtle current lines and fine grain, low contrast so interface objects remain readable, no islands, no animals, no text, no hard focal point, seamless edges, square 2048 by 2048

## 4. Island shape asset sheet — ✍️ AUTHOR AS SVG

**Use:** Island silhouette library. Users resize, rotate, and recolour these, so they
must be vector paths. Treat the prompt below as art direction, or generate one sheet
purely as a tracing reference.

> Asset sheet containing twelve clearly separated irregular island silhouettes viewed directly from above, varied sizes and personalities, layered cut-paper edges, gentle watercolor terrain, delicate ink contour lines, no palm trees and no buildings, sophisticated abstract cartography, each island isolated with ample spacing, transparent background, consistent top-down lighting, no labels, no text, high resolution square

## 5. Connection symbol asset sheet — ✍️ AUTHOR AS SVG

**Use:** Bridges, routes, communication controls — and the waypoint marks for **the
course**. These stretch between arbitrary points and recolour on state, so they must be
vector. Art direction below.

> Cohesive asset sheet of hand-inked top-down connection symbols: a small footbridge, dotted boat route, tiny simple boat, radio-wave arcs, stepping stones, winding current, thread line, and open passage, restrained ink navy with muted coral and gold accents, tactile paper texture, adult editorial style, each symbol isolated and clearly separated, transparent background, no text, no watermark, square high resolution

## 6. Shell token asset sheet — ✍️ AUTHOR AS SVG

**Use:** Meaning Maker shells. Each holds user text at unpredictable length and grows
as it merges, so it must be a scalable shape with a real text slot. Art direction
below. Draw enough variants that a shelf of them looks hand-made, not repeated.

> Collection of sixteen elegant abstract shell and smooth pebble shapes designed as blank word tokens, front-facing or top-down, layered cream paper with fine ink outlines, subtle sea-glass, coral, plum, and gold edge accents, generous blank center in every token for interface text, mature natural-history editorial style, consistent scale, isolated objects, transparent background, no lettering, no watermark, high resolution square

## 7. The current — backdrop

**Use:** Meaning Maker stage backdrop.

> Abstract visual metaphor for ideas gradually converging, many faint tidal streams beginning at the outer edges and joining into one calm luminous pool at center, handmade watercolor on parchment with delicate ink lines and subtle cut-paper depth, deep teal, sea glass, muted gold, and plum, quiet and sophisticated, symmetrical enough to support a branching UI but still organic, no islands, no words, no icons, no text, no watermark, wide 3:2 composition

## 8. Reflection Cove divider

**Use:** Section divider / empty state.

> Minimal intimate shoreline cove at first light, viewed from above, one curved parchment-colored shore meeting translucent teal water, a single smooth pebble and a fine line left by the receding tide, contemplative empty space, watercolor paper grain, editorial book illustration, no text, no people, no logo, wide 3:1 banner

## 9. Completion keepsake frame

**Use:** PDF/print border.

> Elegant printable atlas-page frame on warm parchment, fine hand-inked border inspired by coastlines and tidal marks, tiny abstract compass point, sparse shell and current motifs, sophisticated and restrained, large completely blank central area, dark ink with subtle muted gold accents, no readable letters or numbers, no text, no watermark, portrait A4 proportions, high resolution, print safe

## 10. Social preview image

**Use:** Open Graph card, 1200x630.

> Sophisticated editorial illustration of a central handcrafted paper island surrounded by smaller islands at dawn, fine luminous lines connecting some islands while others remain open, watercolor ocean, parchment paper fibers, ink navy, tidal teal, coral and muted gold, composition weighted to the right with generous clean space on the left for title added later, no text generated inside image, no logo, no watermark, 1200 by 630

## Consistency / negative prompt

Append when the image tool supports negative prompts:

> childish, cartoon, pirate map, tropical vacation, photorealistic, glossy 3D, video game UI, neon, oversaturated, generic corporate gradient, stock wellness imagery, palm trees, treasure chest, compass rose with letters, readable text, typography, logo, watermark, clutter, low contrast focal areas behind UI

## Production notes

- Add all actual type in the website, never bake words into generated art.
- Generated art is background only. If a user can move it, resize it, recolour it, or
  put words inside it, it is interface — author it as SVG.
- Keep a CSS fallback so the site remains usable if generated artwork fails to load.
- Compress hero art to AVIF/WebP and provide responsive sizes.
- Decorative images use empty alt text; meaningful composed maps need descriptive alt text generated from user-entered labels, not visual inference.
