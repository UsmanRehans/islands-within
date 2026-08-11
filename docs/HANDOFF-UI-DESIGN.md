# Islands Within — UI design brief

**Self-contained.** Everything you need is in this document; there are no files to open
and no links to follow. Read it fully before designing anything.

---

## 1. The one thing to understand

**Islands Within is a meaning-making machine that is forbidden from making meaning.**

Every constraint below descends from that single rule. The user builds a private map of
their inner life, combines what they find there into one meaning *they* write, and
reflects on it. The product arranges, prompts, remembers, and gets out of the way.

It never scores, interprets, diagnoses, ranks, or tells the user what anything means.
If a design decision would have the interface say something *about* the user — even
gently, even helpfully — it is wrong. This is not a wellness app, a personality test, a
therapy tool, or a game.

The emotional register: **a private atlas, not a meditation app.** Editorial, tactile,
adult, quiet. Closer to a beautifully made book than to a product.

---

## 2. What the product is

Seven stages, completed alone, in about 20–35 minutes, pausable at any point. Saved
only in the browser — no account, no server, no sync.

1. **Arrival** — a quiet landing page and a grounding invitation.
2. **Home Island** — the user shapes their own island and fills it with what belongs to
   them: words, symbols, simple drawings.
3. **The Islands Around Me** — they add the islands around it (people, places, values,
   memories) and attach one descriptive **quality** to each item. They can connect
   islands with bridges, boat routes, dotted currents, signal arcs — or leave them
   unconnected.
4. **Archipelago View** — a pause. Observational questions only: *"Where does your eye
   go first?"*
5. **Meaning Maker** — every named item becomes a paper **shell**. The user chooses
   which to carry in, then shells are paired *at random* and the user writes one shared
   meaning for each pair. Merged shells pair again, round after round, until one
   remains.
6. **Reflection Cove** — written reflection prompts, all skippable.
7. **My Map** — a keepsake: the archipelago, the meanings, the chosen reflections.
   Export as PDF/PNG/JSON, print, or delete everything.

---

## 3. Vocabulary — use these exact words

Bad names create bad systems. These are settled; please don't invent alternatives.

| Term | Means |
|---|---|
| **Archipelago** | The whole composition |
| **Home Island** | The user's own island |
| **Island** | Any island, including Home |
| **Item** | A thing placed on an island |
| **Quality** | One descriptive word attached to an item |
| **Shell** | A pairing token in the Meaning Maker — and nothing else |
| **The current** | The branching structure of merges (never "tree") |
| **The course** | The progress indicator |

Two traps:

- **"Island" must not mean a third thing.** The progress indicator is **the course** —
  a hand-inked dotted route with small waypoint marks. Do **not** draw progress as a
  row of tiny islands, however charming.
- **"Shell" means only the Meaning Maker token.** The category hint in the island
  editor is just a hint labelled *"Need a starting point?"* — not a tray of shells.

---

## 4. What I'm asking you to design

**Not the landing page first.** Anyone can make a calm landing page. The real problem
is below, and if it solves, everything else inherits from it.

### Deliverable A — the island editor, desktop

The working canvas for stages 2 and 3. Show:

- the canvas with a Home Island and three or four surrounding islands, some connected
- the contextual side panel (roughly 30% width; canvas 70%)
- selection state on an island — resize and rotate handles, visible keyboard focus
- the item editor: adding a word, a symbol, a quality
- the tool set, the undo/redo affordance, and the autosave indicator
- **the course** across the top
- the *"Need a starting point?"* hint, both collapsed and open

### Deliverable B — the same editor, mobile at 360px

Canvas first, tools in a draggable bottom sheet. The sheet must never cover the
selected object. Touch targets 44×44px minimum.

### Deliverable C — list mode

**This is the one that matters.** Every canvas action has a text equivalent: a
non-visual path through the entire exercise using fields and island cards, for
keyboard-only and screen-reader users.

Design it as a **first-class way to use the product**, not a stripped fallback. If it
reads as an accessibility afterthought, the design has failed — and I will say so.

Tell me honestly if this is the piece that breaks the aesthetic. That is useful
information, not a failure.

### Deliverable D — the landing page

Once A–C hold, the landing page. It should feel like the same world.

### Form

Interactive HTML/React mockups are ideal — I want to see focus states, the bottom sheet
moving, and the panel responding. Static high-fidelity frames are acceptable if that
suits you better. Annotate your reasoning where a decision isn't obvious.

---

## 5. Visual system

### Creative concept

**Handcrafted cartography at dawn.** A private atlas assembled from watercolour paper,
ink lines, translucent currents, and small found objects. Mature, tactile, quietly
magical. Never childish, never nautical-themed, never gamified.

### Palette

| Role | Name | Hex |
|---|---|---|
| Primary text / ink | Ink navy | `#17324D` |
| Ocean / primary action | Tidal teal | `#397B7A` |
| Soft water accent | Sea glass | `#9BC7BD` |
| Main background | Parchment | `#F6F0E4` |
| Warm highlight | Coral | `#E8876A` |
| Meaning highlight | Sun gold | `#E9B95B` |
| Reflective accent | Plum | `#68475F` |
| Dark ocean | Midnight tide | `#10293C` |

Text on parchment is navy or dark teal. **Never light coral or gold text on parchment.**
Validate every text/background pair at WCAG AA. Colour is never the sole carrier of
meaning — always pair it with a label, shape, or pattern.

### Typography

- **Display:** a warm humanist editorial serif — Fraunces, Newsreader, or Source Serif 4.
- **UI and body:** Inter, Source Sans 3, or system UI.
- Body 16px minimum; reflection text areas 18px where possible.
- Generous whitespace, soft asymmetry. Reading columns 680–760px.

### Motion

- Ambient water: nearly imperceptible drift, 12–20 second loops.
- UI transitions: 180–450ms, soft ease-out.
- Shell merge: 700–1000ms, interruptible.
- `prefers-reduced-motion`: all travel animation becomes crossfade or instant. Ambient
  motion becomes still layered artwork. **Motion must never block interaction.**

### Signature elements

- **The course** — dotted inked route, waypoint marks, the active one glowing softly.
- **Shells** — paper tokens carrying one item name, with its quality set beneath as a
  subtitle: `Mum · steady`. Merged shells are the same object, larger and more layered.
- **The current** — flowing lines joining shells as they merge; streams converging.
- **Privacy pebble** — a small persistent indicator reading *"On this device."*
- **Quiet celebration** — still water and a widening ring of light. No confetti, no
  badges, no achievement language, ever.

### Iconography

Simple hand-inked line icons with slightly imperfect pressure: shell, compass point,
pencil, bridge, small boat, dotted signal, eye, pebble, seed, home, hands, pause.

No therapy symbols, no brains, no medical crosses, no tropical clip art, no emoji as
primary icons.

---

## 6. Artwork — please do not generate any

Seven background illustrations already exist in the project. You cannot see them, so
here is what they are, and **please leave slots for them rather than inventing
substitutes.** Flat colour blocks keyed to the palette are the right placeholder.

- **Archipelago master image** — viewed from *directly overhead*: flat cut-paper islands
  with soft torn edges casting faint shadows on translucent teal water, fine ink
  shoreline contours, thin gold thread-lines connecting some islands and pointedly not
  others. Used for the heroes and the social card.
- **Ocean texture** — pale sea-glass wash on fibrous paper, very low contrast. The
  canvas ground.
- **The current backdrop** — near-blank warm parchment with faint streams converging
  toward one pale luminous centre. Sits *under* the Meaning Maker UI.
- **Cove divider** — a curved parchment shore meeting teal water, one smooth pebble, one
  fine tide line. Mostly empty.

### Two hard rules

**Everything is top-down. There is no horizon, no sky, and no mountains.** This was
tested: prompts saying "cinematic elevated angle" produced alpine peaks every time, and
they were rejected. The canvas is a map seen from above; the landing image must show
the same world.

**Island silhouettes, connection symbols, and shell tokens are hand-authored SVG, never
generated raster.** They get resized, rotated, recoloured, and have text set inside them
at arbitrary scale. If you design these shapes, design them as vector forms with a real
text slot — a shell must hold a long name and a subtitle without breaking.

---

## 7. Copy — use this, don't invent your own

The voice is warm, spacious, curious, non-judgmental. It speaks *beside* the user, never
above them. Prefer "might," "notice," "if you wish," "to you." Never "This means…,"
"You are…," or "Your result shows…"

**Landing hero**

> **Make space for your own voice.**
>
> Build an island for what belongs to you. Place the people, places, and possibilities
> you want nearby. Then follow the meanings that emerge.
>
> Primary: **Begin my archipelago** · Secondary: **See how it works**
>
> Private on this device · No artistic skill needed · Pause anytime

**Three-step preview**

1. **Create** — Shape your Home Island and fill it with whatever is in your heart.
2. **Connect** — Add the islands around you and name the qualities they hold.
3. **Discover** — Pair what you carry until one personally made meaning remains.

**Opening reassurance**

> This is not about drawing well or making something beautiful. Use stick figures,
> simple shapes, words, or symbols. There are no right or wrong answers, and no one will
> evaluate your drawing. What matters is the meaning it holds for you.

**Stage titles**

- A quiet place to notice — *"Arrive without needing to know the answer."*
- Home Island — *"What belongs at the center?"*
- The Islands Around Me — *"What do I want near me?"*
- Archipelago View — *"Pause before you explain."*
- Gathering — *"Choose what you carry."*
- Meaning Maker — *"Let unexpected connections emerge."*
- Reflection Cove — *"Listen for your own voice."*
- My Map — *"Carry one thing forward."*

**Island editor**

> Give your island the size and shape you want it to have. Here, you have every ability
> and possibility. Add anything that is in your heart.

Always-visible reassurance: **"Simple is enough."**

**Tool labels**

Add island · Add word · Add symbol · Add person · Add place · Add connection · Draw ·
Move · Resize · Undo · Redo · Zoom in · Zoom out · Center map · List view · Save and pause

**Privacy**

> Your work is saved only in this browser on this device unless you choose to export it.
> Islands Within does not analyze, score, or upload your reflections.

**Support note** (present but never alarming)

> Reflection can sometimes bring up strong feelings. Pause if you need to. Consider
> reaching out to someone you trust or a qualified professional for support. This
> experience is educational and reflective; it is not a substitute for mental-health
> care or emergency help.

---

## 8. Non-negotiable constraints

These shape the design. They are not a later engineering concern.

- The entire exercise is completable **by keyboard alone**.
- **List mode** replaces every canvas-only action — designed, not bolted on.
- Visible focus states and a logical focus order throughout.
- Touch targets ≥ 44×44px; responsive from 360px to desktop.
- WCAG AA text contrast; colour never the sole indicator.
- Usable at **200% zoom** with nothing lost.
- Dynamic updates ("paired", "saved") use restrained live regions — not chatty ones.
- Reduced motion removes all ambient and travel animation.
- Print and PDF output stay legible **in greyscale**.
- Destructive actions confirm first.
- Long labels and 30+ items must not break any layout.

---

## 9. Avoid

Generic wellness gradients · glassmorphism · floating blobs · stock meditation
photography · cartoon palm trees · pirate-map or treasure-map clichés · aged sepia
parchment · excessive rounded rectangles · neon · glossy 3D · forced positivity ·
personality-result cards.

And structurally — no scores, streaks, percentages, badges, leaderboards, public
galleries, forced sharing, or any AI interpretation of what the user made.

---

## 10. What to hand back

1. Deliverables A–C, then D.
2. A short note on where the aesthetic and the accessibility requirements fought each
   other, and how you resolved it. **This is the most useful thing you can tell me** —
   more useful than a polished frame.
3. Anything in this brief you think is wrong. It has been argued over, but it is not
   sacred, and you will see things from the design side that I cannot.

If something here is ambiguous, ask before designing around it. Ambiguity at this layer
becomes confusion everywhere downstream.
