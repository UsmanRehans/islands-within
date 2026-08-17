# Master Website Build Prompt

Copy everything below into a capable AI website builder or coding agent — **together
with `02`, `03`, `04`, and `05`.** This brief depends on them; alone it is incomplete.

The governing thesis and vocabulary live in `../CLAUDE.md`. Where this document and
`02-experience-and-content.md` differ on wording, `02` wins.

---

Build a polished, responsive web application called **Islands Within** with the tagline **“Make space for your own voice.”** It is a private, contemplative, interactive version of the Personal Island / Archipelago self-reflection exercise. The product should help users express what is within them, distinguish their own needs and choices from other people’s feelings or expectations, discover patterns, and arrive at one personally meaningful final concept.

This is not a diagnostic tool, a personality test, therapy, fortune-telling, or a scored assessment. Never interpret a user’s drawing for them. Use gentle, invitational language such as “What do you notice?” and “What might this mean to you?” Avoid authoritative claims.

## Product principles

- Private by default: save in the browser only. Clearly state this.
- No artistic skill required: words, symbols, simple shapes, and stick figures are welcome.
- No right or wrong answers; no scores, streaks, leaderboards, or forced sharing.
- Let users skip, undo, edit, pause, return later, and export or delete their work.
- The user creates the meaning; the app only facilitates.
- Calm and spiritually respectful, but inclusive of users of any or no faith.

## Core journey

Create seven clear stages with a persistent but subtle progress indicator called **the
course** — a hand-inked dotted route with small waypoint marks, reusing the boat-route
motif from `04-graphic-generation-prompts.md`. Do not draw the course as tiny islands;
"island" already means two things in this product and must not mean three.

### Vocabulary (use these exact terms in code and UI)

- **Archipelago** — the whole composition.
- **Home Island** — the user's own island. A *role*, not a type: one `Island` entity,
  and the archipelago holds a `homeIslandId`. Never subclass it.
- **Island** — any island, including Home.
- **Item** — a thing placed on an island. **Quality** — one descriptive word attached
  to an item.
- **Shell** — a pairing token in the Meaning Maker, and nothing else.
- **The current** — the branching structure of merges. There are no trees in this
  world; never call it a meaning tree.

### 1. Arrival — “A quiet place to notice”

Create a cinematic landing page with a softly animated dawn ocean and scattered paper-cut islands. Main copy: “Make space between what others feel and what you choose.” Supporting copy: “Build an inner archipelago, follow the meanings that emerge, and listen for your own voice.” Primary CTA: “Begin my archipelago.” Secondary CTA: “How it works.” Include “Private on this device” and “About 20–35 minutes; pause anytime.”

The secondary CTA opens **"See how it works"** — a substantial explanation of the whole
exercise, written out in full in `02-experience-and-content.md`. It is not a three-bullet
summary. The person arriving with no context needs to know what kind of thing this is,
what the seven stages actually involve, that the random pairing has no reshuffle and
why, where their work lives, and — critically — **that nothing here will interpret
them.** Someone who begins expecting a result will read the ending as a let-down rather
than the point; resetting that expectation up front is what lets the ending land.

The same content must be reachable from every stage via a small persistent
**"What am I doing?"** link that opens without blocking or losing work.

All instructional copy explains the **process, never the content**, and there is **no
worked example** anywhere — no sample island, no illustrative items. A worked example
would anchor every user's first entries to ours.

Before beginning, show a brief grounding invitation: “Take one unhurried breath. You do not need to make anything beautiful. Let the first honest shape, word, or symbol be enough.” Add Start and “Skip grounding” controls.

### 2. Home Island — “What belongs at the center?”

Provide an intuitive SVG or canvas island builder. Users can:

- choose a freeform island silhouette or draw one;
- resize, rotate, and position it;
- select terrain colors and textures;
- add words, simple icons, symbols, doodles, and notes;
- add/edit/move/delete items and undo/redo actions;
- name the island if they wish.

Naming is optional, so every island also carries a **handle** — a factual ordinal the
system supplies for reference: `Home Island`, `Second island`, `Third island`. The
handle states position, never content, and is what `aria-label`, list-mode rows, export,
and undo descriptions use when no name exists. It renders in placeholder styling and is
replaced the moment the user types.

**Never supply a content default** such as "Family" or "Work" — that asserts what
categories a life comes in. The categories in the "Need a starting point?" hint *may* be
made tappable to create a named island, because there the user chose it. A default is
assertion; a pick is authorship.

Prompt: “Give your island the size and shape you want it to have. Here, you have every ability and possibility. Add anything that is in your heart.” Keep an always-visible reassurance: “Simple is enough.”

Include a small collapsible hint labelled “Need a starting point?” offering optional,
non-leading categories: people, places, abilities, needs, hopes, rest, play,
faith/meaning, safety, and “my own.” Users may ignore it. This is a hint, not a named
object — do not call it a tray of shells; “shell” means only a Meaning Maker token.

Items may be words, symbols, or drawings. **Only named items can later become shells**,
so when a user adds an unlabelled drawing, invite a name gently at that moment — never
raise it as an error later.

### 3. The Islands Around Me — “What do I want near me?”

Let users add any number of surrounding islands by clicking the sea. Each island can contain a person, place, thing, group, memory, dream, value, or symbol that the user wants around them but not necessarily on their own island.

For every added item, invite the user to attach one descriptive quality or characteristic. Example placeholders only: “steady,” “curious,” “warm,” never prefill answers. Allow bridges, dotted paths, boats, radio lines, or no connection. Let users adjust distance and scale freely. Use proximity visually but never assign it an automatic interpretation.

### 4. Archipelago View — “Pause and notice”

Show the full composition in a beautiful zoomable view. **This is the same renderer as
stage 7** — build one map component with a `mode` of `review` or `keepsake`, never two
implementations. Ask only observational questions:

- “Where does your eye go first?”
- “What feels spacious? What feels crowded?”
- “Is anything missing?”

Allow full editing before continuing. Include an optional private note field.

### 5. Meaning Maker — “Let unexpected connections emerge”

#### 5a. Gathering — “Choose what you carry”

Open this stage with a short curation beat, not a jump straight into pairing. Every
**named item** from every island washes up on a shore as a tactile paper **shell**.
The user chooses which to carry into the Meaning Maker.

**A shell is one named item.** It is never a quality on its own, and an item is never
split into two shells. Where an item has a quality, the quality rides on the shell’s
face as a subtitle — `Mum · steady`. Detaching a quality from the thing it described
would be the app asserting a meaning, which is forbidden.

Guidance, never enforcement:

- Show a suggested count: “Most people carry twelve to sixteen.”
- **No ceiling.** The user may carry everything if they wish.
- **Floor of six.** Below six, offer to return and add more; never block.
- Qualities remain independently listed elsewhere — stage 6 needs them.

Copy: “Not everything needs to come with you. Choose what you want to carry into this.”

#### 5b. Pairing

Shuffle the carried shells randomly and pair them. For each pair, ask the user to
create a shared title, meaning, or concept that represents both. The user must supply
the meaning; do not generate it automatically. Offer only process prompts: “What can
hold both of these?” or “If these belonged to one story, what might its title be?”

Model merges as **`merge(children[]) → Shell`**, not as a binary tree:

- two children is the common case;
- when a round has an odd number, let the user choose whether one shell rests until
  the next round or joins a group of three;
- **a merged shell is the same type as a source shell** — larger, with more layers of
  paper. There is no separate “meaning” entity and no special case for the root;
- repeat until one final shell remains.

**There is no reshuffle button, ever.** Random ordering is load-bearing: a reshuffle
turns “a meaning you made” into “a result I re-rolled until I liked it,” which is the
exact failure this product exists to prevent. **Persist the shuffle seed with the
session** so a refresh cannot re-deal the pairs.

Animate pairs drifting together like islands joined by a current. Show the full
**current** — the branching structure of merges — and allow users to revisit a title
without losing later work. Celebrate the final shell quietly, without confetti: the
ocean stills, a soft ring of light appears, and the final words settle at the center.
Phrase: “This is not an answer assigned to you. It is a meaning you made.”

### 6. Reflection Cove — “Listen for your own voice”

First ask users to write three sentences using qualities they identified. Then present the original reflection questions one at a time, with autosaved text areas:

1. What are the main elements you included on your island?
2. To what extent do you need other people?
3. Is there communication between the islands?
4. Are your basic needs available on your island?
5. What is most important to you?
6. How large is your island compared with the other islands?
7. Who is on your island, and who is on the other islands?
8. What forms of communication connect the islands?

After those, add an optional deeper-reflection section, clearly labeled optional:

- What is taking up so much space inside me that there is not enough room for my own voice?
- What fear have I been allowing to make decisions for me?
- What expectations have I internalized?
- What guilt have I confused with love?
- What responsibility have I taken on that may belong to someone else?
- What might become possible if I stayed deeply connected to the people I love while becoming psychologically free?

Include “I’m not ready to answer this” for each prompt. Never block completion.

### 7. My Map — “Carry one thing forward”

Create a final keepsake page using the **same map renderer as stage 4** in `keepsake`
mode, containing the archipelago, the current, the final shell, chosen reflections, and one optional sentence beginning “The space I want to protect is…” Let users:

- download a tasteful PDF;
- export the island artwork as PNG;
- export/import a private JSON backup;
- print;
- start a new map;
- permanently delete local data.

Sharing must be opt-in and should warn users to review private writing before export. Do not add public galleries or social comparison.

## UI and art direction

Create an original aesthetic called **handcrafted cartography at dawn**: layered paper-cut islands, subtle watercolor grain, inked contour lines, translucent sea currents, tiny shell-shaped controls, and warm light. The interface should feel editorial and artful, not childish, nautical-themed, gamified, or like a generic meditation app.

Use a palette built around deep ink navy `#17324D`, tidal teal `#397B7A`, sea-glass `#9BC7BD`, parchment `#F6F0E4`, coral `#E8876A`, sun-gold `#E9B95B`, and plum `#68475F`. Meet WCAG AA contrast; do not place light coral or gold text on parchment.

Use an elegant humanist serif for display text and a highly readable sans-serif for UI/body. If external fonts are unavailable, use `Georgia` and `system-ui`. Add generous whitespace and soft asymmetry. Avoid glassmorphism, neon gradients, excessive rounded cards, stock wellness photography, and cartoon palm trees.

Motion should be slow and organic: 180–450ms for UI, longer ambient loops for the sea. Respect `prefers-reduced-motion`, turning ambient movement into still layered artwork. Never use motion that prevents interaction.

## Functional requirements

- Responsive from 360px mobile through desktop; touch, mouse, and keyboard support.
- Desktop: canvas and contextual side panel. Mobile: full-width canvas with bottom sheet tools.
- Local autosave with clear “Saved on this device” status.
- Use semantic HTML, visible focus, screen-reader labels, skip links, and keyboard alternatives for all drawing actions.
- Provide a non-canvas “list mode” where users can complete the entire exercise using text fields and island cards.
- Do not make color the sole carrier of meaning.
- Confirm before destructive deletion.
- Gracefully handle refresh, empty states, odd-number pairings, very long text, and 30+ items.
- Include unit tests for pairing logic and persistence, and end-to-end tests for the core journey, keyboard-only completion, and export.

## Suggested implementation

Use Next.js with TypeScript, Tailwind CSS, Framer Motion, and accessible SVG for the archipelago. Use Zustand or a small reducer for state, IndexedDB for local persistence, Zod for import validation, and a client-side PDF/PNG export solution. No backend is required for version one.

Define a robust state model with stable IDs, schema versioning, timestamps, island
geometry, items, qualities, connections, the carried-shell set, **the shuffle seed**,
merge rounds, reflections, preferences, and completion state. Migration-safe
persistence is required — a future version must be able to read a map exported today,
because the long-term point of this product is noticing what changed between the map
you made in March and the one you make in November.

Keep modules clean: onboarding, island editor, item editor, connection editor, map
renderer (shared by stages 4 and 7), gathering, the current, reflection journal,
export, and privacy controls.

## Content details

Use the complete approved copy and microcopy from `02-experience-and-content.md`. It is
authoritative wherever it differs from this file. Preserve the exercise’s meaning,
especially the distinction between loving others and assuming responsibility for
regulating their emotions.

Place the faith-inspired reflection context in an optional “Why reflection?” drawer.
**For v1 this drawer ships with English framing only** — no Arabic text and no verse
citations, which removes an external verification dependency without restructuring
anything. Verified quotations can be added into the existing drawer later. Until then,
the RTL and Noto Naskh Arabic requirements are deferred, not deleted. The full
experience must work without ever opening the drawer.

## Deliverables

Produce a production-quality app, not a static mockup. Include reusable components, complete responsive states, empty/loading/error states, local privacy language, tests, and a concise README with setup commands and architecture notes. Do not leave non-functional buttons or TODO labels.

On artwork, follow the split in `04-graphic-generation-prompts.md`: **atmosphere is
generated, interface is hand-authored SVG.** Island silhouettes, connection symbols,
and shell tokens are vector assets you draw — they are resized, rotated, recoloured,
and have text set inside them, which raster cutouts cannot survive. Use original
placeholder SVG textures for the generated backgrounds until final artwork is supplied.

Before finishing, audit every stage against `05-quality-accessibility-and-safety.md` and fix all failed checks.

---
