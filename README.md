# Pattern

A browser-based generator for the **DB diagonal logo pattern**. The exact vector
artwork is turned into a seamless, recolorable, zoomable SVG tile — no build
step, no dependencies.

## Features

- **Three configurable pattern colors** — each of the pattern's tones can be set
  via a color-picker swatch **or** by typing a hex value (`#RRGGBB` / `#RGB`).
- **Zoom / scale** — slider, `+` / `−` buttons, or mouse-wheel (up to 2400%);
  the wheel zooms toward the cursor.
- **Pan** — drag to move the pattern.
- **Overlay bars** — scatter larger copies of the pattern's base element (the
  slanted bar) that **snap perfectly onto the lattice**:
  - three discrete sizes (S / M / L),
  - three configurable colors, distributed **⅓ / ⅓ / ⅓** across scattered bars,
  - **click anywhere** to place a bar (snaps to the pattern), with size/colour
    pickers for the next placement, plus Undo / Clear.
- **Save PNG** — export the current view (pattern + bars) as a 2× PNG.

More features will be added later.

## How it works

`pattern-data.js` holds the pattern's polygons (extracted from the source SVG),
already replicated across its horizontal period (477 units) and pruned to a
single seamless tile. `index.html` renders them as an SVG `<pattern>` whose three
colour groups and `patternTransform` (scale + translate) are updated live.

The overlay bars reuse the pattern's **base element** — a parallelogram of
thickness `477/10`, height `2916.85/21`, shear `¾·height`. `pattern-data.js` also
stores the real bar **anchor** positions of one tile, so any integer-scaled copy
placed on an anchor lines up exactly with the underlying hatch.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server
```

## Deployment

Pushes to `main` (or the active development branch) are published to GitHub
Pages via the workflow in `.github/workflows/deploy.yml`.
