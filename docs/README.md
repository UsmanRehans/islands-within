# Islands Within — design documents

**Tagline:** Make space for your own voice.

These five documents are the source of truth for the product. Read `../CLAUDE.md`
first — it holds the thesis, the vocabulary, and the settled decisions these documents
implement.

## This is a bundle, not a sequence

`01` explicitly depends on the copy in `02`, the visual system in `03`, and the gate in
`05`. Handing a builder only the first file will get you invented microcopy and a
different aesthetic. **Provide all five together, every time.**

| File | Role |
|---|---|
| `01-master-website-build-prompt.md` | The build brief — scope, journey, requirements |
| `02-experience-and-content.md` | Approved copy and microcopy. Authoritative over `01` where they differ |
| `03-visual-system-and-ui.md` | Palette, type, layout, motion, signature elements |
| `04-graphic-generation-prompts.md` | Art direction; which assets to generate and which to author |
| `05-quality-accessibility-and-safety.md` | The final gate. Audit before calling anything done |

## What the experience does

The user shapes a Home Island and fills it with what belongs to them, adds the Islands
around it and names a quality for each, pauses to look at the whole archipelago, then
carries a chosen handful of items into the Meaning Maker — where random pairs merge,
round by round, into one meaning they wrote themselves. They finish in Reflection Cove
and leave with a map.

## Suggested technology

Next.js, TypeScript, Tailwind CSS, Framer Motion, accessible SVG canvas. Local
persistence via IndexedDB. No backend, no account, no server for v1.

## Naming history

Considered: Inner Archipelago · The Space Between · My Island, My Voice · Archipelago
of Self.

**Chosen: Islands Within** — memorable, calm, inclusive, tied to the exercise without
sounding clinical.
