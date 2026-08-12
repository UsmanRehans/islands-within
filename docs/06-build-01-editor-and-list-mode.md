# Build 01 — the editor and list mode

The first build. Read `../CLAUDE.md` first; it holds the thesis, the vocabulary, and
the settled decisions this brief implements. `../DESIGN_TOKENS.md` is the visual ground
truth. `05-quality-accessibility-and-safety.md` is the gate.

---

## What this build is

The island editor, finished, **together with its complete text equivalent**. This
covers stages 2 and 3 — Home Island and The Islands Around Me — and nothing else.

Two surfaces, one document. A user can switch between them at any moment and lose
nothing.

## Why these two together, and not in sequence

Because parity built afterwards is parity faked.

Build seven stages of canvas, then add list mode under deadline, and what you get is a
thin form that technically satisfies the checklist and that nobody would choose to use.
Every project that has ever bolted accessibility on at the end has produced exactly
that. The failure is structural, not moral.

Build them together and something better becomes available: **both surfaces issue the
same operations, so parity stops being a checklist and becomes an architectural
property.** You cannot add a canvas feature that list mode lacks, because features
aren't added to surfaces — they're added to the operation set, and both surfaces render
it.

This is the same shape as the map renderer decision (one renderer, two framings). The
project keeps producing it. Follow it.

---

## The operation set

Every change to the archipelago is one of these. The canvas dispatches them from
gestures; list mode dispatches them from fields and buttons. Undo/redo operates on this
list and nothing else.

```
createIsland(position?)          renameIsland(islandId, name)
moveIsland(islandId, x, y)       resizeIsland(islandId, radius)
rotateIsland(islandId, angle)    deleteIsland(islandId)

addItem(islandId, text, kind)    editItem(itemId, text)
setItemQuality(itemId, quality)  deleteItem(itemId)
moveItem(itemId, toIslandId)

connect(islandA, islandB, type)  setConnectionType(connectionId, type)
disconnect(connectionId)
```

Rules that fall out of this:

- **No surface may mutate state directly.** If the canvas reaches into an island object,
  list mode and undo both silently drift.
- Every operation carries a human-readable description for undo — *"Undo: renamed
  Second island"*. This is the second consumer of handles, after screen readers.
- Operations are the unit of persistence, not the unit of storage: persist the resulting
  document, keep operations in memory for undo.

---

## Data model

Write this down now. Migration-safety is what protects the long-term point of the
product — noticing what changed between the map you made in March and the one you make
in November — and it cannot be retrofitted.

```
Archipelago {
  schemaVersion: number          // integer, bump on any breaking shape change
  id: string                     // stable, survives export/import
  homeIslandId: string
  islands: Island[]
  items: Item[]                  // flat, not nested — see below
  connections: Connection[]
  createdAt: string              // ISO 8601
  updatedAt: string
}

Island {
  id, name: string               // name is "" when unnamed; never a default
  x, y, radius, rotation: number
  silhouetteSeed: number         // so a shape is stable across reloads
  createdAt: string              // also gives the ordinal for the handle
}

Item {
  id, islandId: string
  text: string                   // "" for an unnamed drawing or symbol
  quality: string | null         // one word, the user's
  kind: "word" | "symbol" | "drawing"
  createdAt: string
}

Connection { id, a, b, type, createdAt }
```

**Items are a flat list, not nested inside islands.** Gathering needs every item across
every island in one pass; list mode needs to render them per island; a future version
needs to diff two archipelagos item by item. A flat list with `islandId` gives all
three. Nesting gives none of them without a traversal.

**`name` is `""` when unnamed — never the handle.** The handle is derived at render
time from creation order. Storing it would turn an address into content, and the
distinction is the whole point.

Only items with non-empty `text` become shells. That is the rule that keeps unnamed
doodles out of the Meaning Maker, and it lives here in the model rather than in a
downstream filter where it can be forgotten.

---

## Canvas requirements

The direct-manipulation grammar is settled in `CLAUDE.md`. What this build must add to
the existing prototype:

**Quality attachment.** Currently missing and load-bearing. An item may carry one
descriptive word. On the shell it renders `Mum · steady`. Today the prototype makes
`Mum` and `steady` two items, which would produce two shells instead of one — a direct
violation of the shell ruling. Fix this first.

Invite the quality, never prefill it. Example placeholders only, and never as a value.

**Delete.** Islands and items. Confirm before deleting an island that holds items.
Undoable.

**Pan and zoom.** Drag open water to pan, scroll or pinch to zoom. Must remain usable at
200% browser zoom, which is a separate requirement from canvas zoom.

**Symbols and drawings.** Items whose `kind` is not `word`. Invite a name at the moment
of drawing — gently, never as an error later — because unnamed items cannot become
shells.

**Rotate.** A corner handle. Currently unimplemented.

---

## List mode requirements

Not a fallback. A way to use this product that a sighted mouse user might reasonably
prefer, and the primary path for anyone using a keyboard or a screen reader.

- One card per island, in creation order. Home Island first.
- Each card: the island's name or **handle** in placeholder styling, its items, each
  item's quality, and its connections stated in words — *"a bridge to Second island."*
- Add an island, rename, add an item, attach a quality, connect, delete — all reachable
  by keyboard, all issuing the same operations as the canvas.
- Switching between canvas and list preserves everything, including selection where it
  makes sense. It is a view toggle, not a mode with its own state.
- Live regions announce operation results, restrained: *"Added steady to Mum."* Not
  every keystroke.

### Geometry in list mode — the ruling

Position, size and rotation are **expressive, not semantic**. The app asserts nothing
about them; a standing prohibition forbids it. So a list-mode user loses no *meaning* by
not placing islands by hand — but they must not end up with a broken-looking keepsake
either.

**Islands created in list mode are auto-placed** on a calm, non-overlapping layout, and
size defaults to uniform. The user may adjust both from the card if they wish, plainly
labelled, but nothing requires them to. Both paths produce the same document and the
same keepsake.

Do not offer "near / far" or "big / small" as *choices with names* — naming a spatial
relationship is the app suggesting it means something.

---

## Acceptance — the parity test

Not a checklist. One test:

> Complete stages 2 and 3 twice. Once with a mouse and the canvas. Once with the
> keyboard only, canvas hidden, screen reader on. Export both.
>
> **The two exports must be structurally identical** — same islands, names, items,
> qualities, connections. Only geometry may differ.

If that passes, this build is done. If it cannot pass, list mode is not real, whatever
it looks like.

Alongside it, the relevant sections of `05` — interaction quality and accessibility —
must pass in full.

---

## Explicitly out of scope

Do not build these here, however tempting once the editor works:

Gathering · the Meaning Maker · Reflection Cove · My Map · the landing page · PDF/PNG
export · the "Why reflection?" drawer.

**In scope but easy to forget:** local persistence with `schemaVersion` and migration
handling, JSON export/import with validation, and delete-all. The editor is not finished
if a refresh loses the work.

---

## Open questions for the build

1. **Quality entry flow.** Is the quality a second field on the item, or a follow-up
   invitation after the item is named? The second reads warmer and matches "invite,
   never prefill" — but it costs a step per item, and with 16 items that adds up. Try
   both; the answer is a feel judgement, not a logic one.
2. **Connection types in list mode.** Cycling by click is right on canvas. In list mode
   it should probably be a plain labelled select — the five types are `bridge`,
   `boat route`, `dotted current`, `signal`, `custom`. Confirm the wording against
   `02-experience-and-content.md` before shipping strings.
3. **Does list mode need the course?** Probably yes, as text. Decide deliberately rather
   than by omission.
