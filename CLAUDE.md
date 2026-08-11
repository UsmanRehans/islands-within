# Islands Within

**Make space for your own voice.**

A private, contemplative web experience. You build an inner archipelago, combine what
you find there into one personally made meaning, and reflect on what you notice.

---

## The one sentence

**It is a meaning-making machine that is forbidden from making meaning.**

Everything else in this repository descends from that. No scoring. No interpretation.
No "your result shows." The user names every merge, chooses every word, and decides
what any of it means. The app arranges, prompts, remembers, and gets out of the way.

If a proposed feature would have the app tell the user something about themselves,
the answer is no. That includes helpful, gentle, well-intentioned versions of it.

## The mountain

Not the map you make today — **the difference between the map you made in March and
the one you make in November.** Reflection is a practice, not a session.

V1 does not build this. V1 must not *block* it. Concretely that means: stable IDs,
schema versioning, timestamps on everything, and an export format that a future
version can read. Those are already required in `docs/01`; they are required *for this
reason*, and that reason should survive.

## Who it's for

A **public web product**. Anyone can find it and complete it alone, with no account,
no facilitator, and no explanation. It is not a workshop tool and not a clinical
instrument. Design for the person who arrives at 11pm with no context.

---

## Vocabulary

Get these right. Ambiguity here becomes confusion everywhere downstream.

| Term | Means | Never means |
|---|---|---|
| **Archipelago** | The whole composition | A stage, a progress bar |
| **Home Island** | The user's own island | A separate type from Island |
| **Island** | Any island, including Home | A stage marker |
| **Item** | A thing placed on an island | |
| **Quality** | One descriptive word attached to an item | A tag, a score, a category |
| **Shell** | A pairing token in the Meaning Maker | The stage-2 category hint |
| **The current** | The branching structure of merges | "The meaning tree" — no trees here |
| **The course** | The progress indicator | Anything drawn as islands |

Three rules that keep this clean:

1. **Home Island is a role, not a type.** One `Island` entity; the archipelago holds a
   `homeIslandId`. Never `class HomeIsland extends Island` — you will duplicate the
   editor and then the two will drift.
2. **The course is drawn as a dotted route with waypoint marks**, reusing the
   boat-route motif from `docs/04`. Not as tiny islands. "Island" already means two
   things; it must not mean three.
3. **Stage 2's category helper is not an object and has no name.** It is a hint
   labelled *"Need a starting point?"* Killing a name beats renaming one.

---

## Load-bearing decisions

These were argued and settled. Don't re-litigate without new evidence; do read the
reasoning before overturning.

### A shell is one named item

Not a quality, and not an item split into two tokens. Where an item has a quality, the
quality **rides on the shell's face as a subtitle** — `Mum · steady`.

Why: detaching a quality from its referent is itself an act of interpretation — it
asserts that "curious" is a free-floating concept rather than a thing the user said
about their brother. That is the app making meaning. It also halves the token count,
and it makes each pairing richer than two bare adjectives colliding.

**Unnamed doodles and symbols do not enter the pool.** You cannot ask someone to find
the shared meaning between a squiggle and their grandmother. Surface this gently at
the point of drawing, never as an error later.

Qualities still exist as an independently listable set — stage 6 needs them for the
three-sentence exercise.

### Count is curated, never capped

Rounds = log₂(shells). 16 shells is 15 merges is roughly ten minutes of real thought.
32 shells is 31 merges and an ordeal.

- **Target 12–16 shells. Floor 6.** Below the floor, offer to go back and add more.
  Never block.
- **No ceiling.** Instead, the Meaning Maker opens with **Gathering**: every named item
  washes up on a shore and the user chooses what to carry in. Suggested count shown,
  never enforced.

Gathering is a screen inside the Meaning Maker, not an eighth stage. Seven is already
a lot to hold.

This solves the too-many and too-few problems with a single move, and it is *on
thesis* — the user decides what they bring. Curation is authorship; it does not
compromise randomness, because randomness governs pairing, not participation.

### Merges are n-ary; shells are recursive

`merge(children[]) → Shell`. Two is the common case, three is the odd-round option, one
may rest a round. **A merged shell is the same type as a source shell** — bigger, more
layers of paper. The final concept is simply the last shell standing.

Model it this way from the first line and the group-of-three rule stops being a
special case bolted onto a binary tree.

### There is no reshuffle button

Random ordering is load-bearing. A reshuffle converts *"a meaning you made"* into *"a
result I re-rolled until I liked it"* — exactly the failure this product exists to
prevent.

**Corollary:** the shuffle seed is persisted with the session. A refresh must not
re-deal the pairs.

### A name is content; a handle is an address

Naming an island is optional, but every island still needs something to be called — in
list mode, in a screen reader, in an export, in an undo description. Those are two
different strings with two different owners.

- **Name** — the user's. Always chosen, never suggested, never prefilled.
- **Handle** — the system's. Factual and ordinal: *Home Island*, *Second island*,
  *Third island*. It states position, never content.

The handle renders in placeholder styling so it never reads as committed content, and
it is replaced the instant the user types. It is what `aria-label`, list-mode rows, and
export use when there is no name.

**Never a content default.** "Family", "Work", "Friends" would be the app asserting what
categories a life comes in — a worse violation than a prefilled quality, because the
island is the larger unit.

**The hint may be clickable, and that is not the same thing.** Tapping *people* in
"Need a starting point?" to create an island named `people` is authorship: the user
chose it. A default is assertion; a pick is choice. Same string, opposite meaning.

Safe by construction: only *items* become shells, so a handle can never enter the
Meaning Maker.

### The canvas is the interface. There is no tool palette.

A place you edit through a menu is a document, not a place. This product is about
making somewhere that feels like yours — direct manipulation is not a style preference
here, it is the difference between operating software and being somewhere.

**Noun first, then verb — and the verb appears where the noun is.**

| Intent | Interaction |
|---|---|
| Add an island | Click open water. It appears there. No mode, no button |
| Select | Click an island. Handles appear *on it*; contextual actions ring the island itself |
| Add an item | Type while an island is selected |
| Connect | Drag from one island to another. Click the connection to cycle its type |
| Resize / rotate | Drag an edge / drag a corner |
| Pan / zoom | Drag open water / scroll or pinch |

That removes eleven of the fifteen tool labels in `docs/02`. What survives as chrome:
**undo/redo, the save indicator, the course, and continue.** Four things, all small, all
at the edges.

**Why the palette existed, and why it can go:** it was a hedge — something for keyboard
users to reach for on the canvas. List mode already solves that completely, as a full
parallel path. The hedge produced the worst of both worlds: a menu-ish canvas *and* a
list mode. Remove it and each path gets to be pure.

**This changes interaction, not aesthetic.** "Handcrafted cartography at dawn" is
unchanged. Modern here means direct, immediate, low-chrome — never sleek, never
minimal-tech, never a change of visual direction.

### One map renderer, two framings

Archipelago View (stage 4) and My Map (stage 7) draw the same thing for different
reasons. One component, a `mode` of `review` or `keepsake`. If they fork you get two
bug surfaces and a keepsake that doesn't match what the user made.

### Graphics: generate atmosphere, author interface

**Generated** (Higgsfield or equivalent): heroes, ocean texture, confluence backdrop,
cove divider, keepsake frame, social preview. Static, decorative, never manipulated.

**Hand-authored SVG**: island silhouettes, connection symbols, shell tokens.

The rule underneath: **interactive means parameterized, and parameterized means
vector.** Each of these is resized, rotated, recoloured, or has text set inside it at
arbitrary scale. `docs/04` already requires an SVG fallback for exactly these three —
which means the SVG *is* the asset and the raster is the thing you'd delete.

### Faith context: drawer, English framing only

The optional "Why reflection?" drawer ships in v1 with the reflection framing and no
Arabic quotation or verse citation. This removes an external verification dependency
without restructuring anything — verified text can be added into the existing drawer
later.

Until that day: no Arabic strings, and the RTL/Noto Naskh requirements in `docs/05`
are deferred rather than deleted.

---

## Working in this repo

`docs/` is the source of truth. It is a **bundle, not a sequence** — the build prompt
in `docs/01` depends on the copy in `docs/02`, so an agent handed only the first file
will invent your microcopy. Hand over all five.

`docs/05` is the final gate. Audit against it before calling anything done.

## Standing prohibitions

Not style preferences. Violations of the thesis.

- No scores, streaks, percentages, badges, leaderboards, or public galleries.
- No AI interpretation of a drawing, a placement, a distance, a size, or a colour.
- No claim that island size, proximity, colour, or connection type carries fixed meaning.
- No analytics that touches reflection text, names, canvas labels, or exports.
- No cloud sync, no account, no hidden upload.
- No forced completion. Every prompt is skippable, every stage revisitable.
- No marketing this as therapy or as a substitute for care.
