# Generated assets

Produced 2026-08-11 with Recraft V4.1 (`standard`, 2k) via Higgsfield. Art direction
and the prompt rules that produced these live in [`../docs/04`](../docs/04-graphic-generation-prompts.md).

**These are backgrounds only.** Island silhouettes, connection symbols, and shell
tokens are hand-authored SVG — see the split at the top of `docs/04`. A builder that
generates images for this project is violating the brief, not filling a gap.

## generated/

| File | Use | Note |
|---|---|---|
| `archipelago-topdown-master.png` | Social preview (1200×630) — **and the reference for both heroes** | The direction. Cut-paper islands, torn edges, real shadows, gold connector threads, empty water left |
| `hero-mobile.png` | Mobile landing, 9:16 | Top-down, headline space in the upper third |
| `cove-divider.png` | Reflection Cove divider / empty state | Best asset of the set. Crop to a 3:1 band through the middle |
| `current-backdrop.png` | Meaning Maker backdrop, 3:2 | Pale enough to sit under shells and text |
| `ocean-texture.png` | Canvas ground, 2048² | Not truly seamless — tile with a CSS blend or use as a single ground layer. Hue runs slightly warm of sea-glass `#9BC7BD` |

## Still needed

- **Desktop hero, 16:9** — recipe proven, ran out of credits. Use the
  `archipelago-topdown-master` prompt at 16:9.
- **Keepsake frame, portrait** — needs the anti-sepia clauses from `docs/04`.

## rejected/

Kept as evidence, not as assets — **downscaled to 1400px**, since git history is
forever and a small version proves the point identically. Each names its failure mode:

- `hero-desktop-VISTA-REJECTED` — "cinematic elevated angle" produced alpine mountains.
  The finding that forced the top-down ruling.
- `current-backdrop-TOO-DARK-REJECTED` — beautiful illustration, unusable as a
  backdrop. Saturated navy and plum masses would fight every shell placed on it.
- `keepsake-frame-SEPIA-REJECTED` — drifted to aged treasure-map pastiche, which is on
  the project's own avoid-list.

Before regenerating anything, read the six prompt rules in `docs/04` — they were paid
for with these three.
