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
- **Exercise desktop: the canvas is full-bleed.** No persistent side panel and no tool
  palette. Controls appear at the object being manipulated; the only fixed chrome is
  undo/redo, the save indicator, the course, and continue — small, at the edges.
- **Exercise mobile: the canvas is the screen.** Contextual actions appear at the
  selected object. A sheet may rise for text entry, and must never cover the selection.
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

## Island builder behaviours — direct manipulation only

**Noun first, then verb, and the verb appears where the noun is.** There is no mode to
enter and no tool to arm before acting.

- Click open water — an island appears there.
- Click an island — selected. Handles sit *on it*; contextual actions ring the island
  itself, never a panel across the screen.
- Type while an island is selected — an item is added.
- Drag from island to island — a connection draws itself. Click it to cycle type:
  bridge, boat route, dotted current, signal, or custom.
- Drag an edge to resize, a corner to rotate, open water to pan; scroll or pinch to zoom.
- Undo/redo and a visible autosave state are always available.
- Do not interpret distance, size, colour, or connections.

Keyboard and screen-reader users get **list mode** — a complete parallel path, not a
half-accessible canvas. That is precisely why the canvas is free to be pure.

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
- An unnamed island shows its **handle** (`Second island`) in placeholder styling —
  italic, `ink-soft`, reduced opacity — so it never reads as content the user wrote.
  The canvas may also show a separate invitation to name it; the handle is what
  assistive technology and exports read.
- The map must remain usable at 200% zoom.
- PDF/print output should work in color and grayscale.

## Avoid

Generic wellness gradients, glassmorphism, floating blobs, stock meditation photos, cartoon palm trees, pirate-map clichés, gamification, forced positivity, personality-result cards, excessive rounded rectangles, and AI-generated interpretations.
