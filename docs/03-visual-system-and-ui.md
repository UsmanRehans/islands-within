# Visual System and UI Direction

## Creative concept

**Handcrafted cartography at dawn.** The interface resembles a private atlas assembled from watercolor paper, ink lines, translucent currents, and small found objects. It should feel mature, tactile, and quietly magical—never childish or overly nautical.

## Palette

| Role | Color | Hex |
|---|---|---|
| Deep ink / primary text | Ink navy | `#17324D` |
| Ocean / primary action | Tidal teal | `#397B7A` |
| Soft water accent | Sea glass | `#9BC7BD` |
| Main background | Parchment | `#F6F0E4` |
| Warm highlight | Coral | `#E8876A` |
| Meaning highlight | Sun gold | `#E9B95B` |
| Reflective accent | Plum | `#68475F` |
| Dark ocean | Midnight tide | `#10293C` |

Use navy or dark teal for text on parchment. Validate all text/background pairs at WCAG AA. Include patterns or labels in addition to color.

## Typography

- Display: a warm humanist/editorial serif such as Fraunces, Newsreader, or Source Serif 4.
- UI and body: Inter, Source Sans 3, or system UI.
- Arabic: not used in v1. When verified quotations are added, Noto Naskh Arabic with generous line height and correct right-to-left layout.
- Keep body text at 16px minimum and reflection text areas at 18px where possible.

## Layout

- Landing: full-bleed illustrated ocean with a narrow editorial text column.
- Exercise desktop: 70% living canvas, 30% contextual panel.
- Exercise mobile: canvas first, tools in a draggable bottom sheet.
- Reflection: calm reading column, 680–760px wide.
- Completion: printable atlas spread with map left and selected meaning/reflection right.

## Signature UI elements

- **The course:** the progress indicator — a hand-inked dotted route with small
  waypoint marks, the active one glowing softly. **Not tiny islands.** "Island" already
  carries two meanings in this product; a third would confuse both the UI and the code.
- **Shells:** draggable paper tokens in the Meaning Maker. A shell is one named item,
  with its quality set beneath as a subtitle (`Mum · steady`). Merged shells are the
  same object, larger and more layered. Nothing else in the product is a shell.
- **The current:** flowing lines join shells as they merge, streams converging toward
  one pool. This is the branching structure — never call it a tree.
- **Reflection tide marker:** indicates progress without percentages or pressure.
- **Privacy pebble:** a small persistent indicator reading “On this device.”
- **Quiet celebration:** still water, widening light ring, no confetti or achievement badges.

## Island builder behaviors

- Click/tap water to add an island.
- Drag to position; handles resize and rotate.
- Double-click or Enter opens island details.
- Connections can be bridge, boat route, dotted current, radio/signal, or custom text.
- Every visual action has a keyboard/list-mode equivalent.
- Provide undo/redo and a visible autosave state.
- Do not interpret distance, size, color, or connections.

## Motion

- Ambient ocean: nearly imperceptible parallax and grain drift, 12–20 second loops.
- UI transitions: 180–450ms with soft ease-out.
- Meaning merge: 700–1000ms, interruptible.
- Reduced motion: replace all travel animations with crossfades or instant state changes.

## Iconography

Use simple hand-inked line icons with slightly imperfect pressure: shell, compass point, pencil, bridge, small boat, dotted signal, eye, lock/pebble, seed, home, hands, star, and pause. Avoid literal therapy symbols, brains, medical crosses, tropical clip art, and emoji as primary icons.

## Responsive notes

- At 360px, preserve 44x44px touch targets and never obscure the selected object with the tool sheet.
- Long island names should wrap or truncate with accessible full text.
- The map must remain usable at 200% zoom.
- PDF/print output should work in color and grayscale.

## Avoid

Generic wellness gradients, glassmorphism, floating blobs, stock meditation photos, cartoon palm trees, pirate-map clichés, gamification, forced positivity, personality-result cards, excessive rounded rectangles, and AI-generated interpretations.
