# Islands Within — design tokens

Ground truth for this project's visual language. **Overrides any portable defaults**
(no dark canvas, no lime, no pill-shaped controls — see *Shape* below for why).

Concept: **handcrafted cartography at dawn.** A private atlas of watercolour paper, ink
lines, and cut-paper islands. Mature, tactile, quiet. Never childish, never nautical
pastiche, never a wellness app.

---

## The one decision everything cascades from

**There are no containers.**

No cards, no panels, no toolbars, no top bar. One continuous sheet of paper, and
everything on it is either *drawn on* it or *placed on* it. Where separation is needed,
use a hairline rule or plain space — never another bordered box.

This single rule is what removes the "menu feeling." Every other token below is
downstream of it. If a proposal reintroduces a container, it is wrong regardless of how
well it is styled.

---

## Palette

| Token | Hex | Role |
|---|---|---|
| `paper` | `#F6F0E4` | The canvas. Everything sits on this |
| `paper-deep` | `#EFE7D8` | Rare second paper tone — a raised sheet, a sheet edge |
| `ink` | `#17324D` | Primary text, drawn lines, shorelines |
| `ink-soft` | `#5A6E80` | Secondary text, labels, inactive marks |
| `tide` | `#397B7A` | **Water only.** Fills, washes, ocean. Not text, not controls |
| `tide-deep` | `#2F6362` | **The interactive teal.** Primary action fill, active states, links |
| `seaglass` | `#9BC7BD` | Shallow water, hover wash, soft fills |
| `coral` | `#E8876A` | Warm accent — decorative and light-source only |
| `gold` | `#E9B95B` | Meaning highlight — connector threads, the final shell |
| `plum` | `#68475F` | Reflective accent. Text-safe |
| `midnight` | `#10293C` | Deep water, heaviest ink |

### Contrast — measured, not assumed

| Pair | Ratio | Verdict |
|---|---|---|
| `ink` on `paper` | **11.6:1** | Passes everything |
| `plum` on `paper` | **7.0:1** | Text-safe |
| `tide-deep` on `paper` | **6.0:1** | Text-safe |
| `paper` on `tide-deep` | **6.0:1** | Primary button, safe |
| `tide` on `paper` | **4.3:1** | ✗ **Fails AA body text** (needs 4.5) |
| `coral` / `gold` on `paper` | ~2:1 | ✗ Never text |

**This produced `tide-deep`, and it is a real distinction, not a shade:** `tide` is a
*water* colour and `tide-deep` is the *interactive* one. A teal button at `#397B7A` with
paper text fails AA at body size. Anything a user reads or clicks uses `tide-deep`.

Colour is never the sole carrier of meaning — always pair with a label, shape, or mark.

---

## Shape — edge quality, not radius

**Pills are forbidden here.** Not because round is wrong, but because a 999px capsule is
a *manufactured* shape: nothing in a handmade atlas has one, and it reads instantly as
software. This is the deliberate override of the portable default.

What carries the shape language instead is **how an edge is made**:

| Token | Meaning |
|---|---|
| `edge-drawn` | A hand-inked stroke, 1.5–2px, slight pressure variance, never perfectly uniform |
| `edge-torn` | A soft irregular cut-paper boundary with a faint offset shadow beneath |
| `edge-hairline` | 1px `ink` at 12% — the only divider. Replaces every border-box |

Radii stay small and quiet: `radius-soft` 10px for text fields and sheets, `radius-tight`
6px for small marks. Nothing above 14px. Islands and shells are irregular vector
outlines, not radii at all.

Shadows are paper shadows: `0 2px 6px rgba(23,50,77,0.10)`, warm and shallow. Never a
glow, never elevation-as-blur-radius theatre.

---

## Typography

- **Display** — editorial serif (Fraunces / Newsreader / Source Serif 4). Stage titles,
  hero, the final meaning. 28–44px, weight 500–600, generous line-height.
- **UI / body** — humanist sans (Inter / Source Sans 3). 16px minimum.
- **Reflection input** — serif, 18px, line-height 1.7. Writing should feel like writing,
  not like filling a form.
- **Micro-label** — 12px sans, weight 500, `ink-soft`. Tracking 0.04em, sentence case.
  **No uppercase tracking** — it reads as a dashboard.

Hierarchy comes from size, weight, and space. Never from a coloured background.

---

## Spacing

| Token | Value |
|---|---|
| `space-edge` | 32–48px — margin from viewport to any chrome |
| `space-stack` | 12–16px |
| `space-inline` | 8–12px |
| `reading-column` | 680–760px max |

---

## The island editor — anatomy

Full-bleed canvas. The paper runs edge to edge. Nothing is docked.

**On the canvas**
- Water: `tide` wash over the ocean paper texture, `seaglass` in the shallows.
- Islands: `edge-torn` cut-paper shapes with a faint shadow, `ink` shoreline contour.
- Selected island: a hand-drawn `ink` ring around it — imperfect, as if circled in pen.
  Four resize handles at the cardinal points; one rotate mark above.
- Items sit *on* the island as ink words and small symbols.
- Connections: drawn ink routes between islands. Click to cycle type.
- Adding: click open water, an island appears. Type while selected, a word lands.
- Connecting: drag from an island's edge; a dotted route follows the cursor.

**Fixed chrome — four things, none in a container**
| Element | Placement | Treatment |
|---|---|---|
| The course | Top, centred | A drawn dotted route with waypoint marks, directly on paper. Active waypoint filled `gold`. No bar, no background |
| Undo / redo | Bottom left | Two small `ink` glyphs, no button surface |
| Save indicator | Bottom left, beside undo | *"Saved on this device"* — 12px `ink-soft` with a small pebble mark |
| Continue | Bottom right | The only filled control on the screen |

That's the entire interface. If a fifth persistent element appears, challenge it.

---

## Controls — there are only three

1. **Primary** — `tide-deep` fill, `paper` text, weight 600, `radius-soft`, padding
   12×24. One per screen, maximum. This is the only filled control anywhere.
2. **Quiet** — no fill, `ink` text, a 1.5px `edge-drawn` underline that thickens on
   hover. Reads as annotation, not as a button.
3. **Mark** — an icon alone in `ink-soft`, no surface; hover brings it to `ink`.
   Undo, redo, zoom, close. 44×44px hit area regardless of visual size.

Outlined-on-dark is anaemic; **outlined-on-paper is drawn.** That inversion is why the
portable "never use outline-only buttons" rule does not apply on this canvas.

### Focus and state

- Focus ring: 2px `ink`, 2px offset, following the object's real shape — including the
  irregular outline of an island. Never suppressed, never a faint tint.
- Hover: a `seaglass` wash at 20%, or ink deepening. Never a colour change that implies
  meaning.
- Disabled: `ink-soft` at 40%. Rare — this product doesn't gate much.

---

## This language forbids

Cards · panels · sidebars · top bars · pill buttons · uppercase tracked labels ·
glassmorphism · gradients · glows · drop shadows deeper than 8px · more than one filled
control per screen · colour used as the only signal · any surface whose only job is to
contain another surface.

And from the product thesis, which outranks all of the above: nothing that scores,
ranks, badges, or interprets the user.
