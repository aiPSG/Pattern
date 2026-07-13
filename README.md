# Pattern

A browser-based generator for the **DB diagonal logo pattern**. The exact vector
artwork is rendered to a canvas — seamless, recolorable, and **sharp at any zoom**
— with no build step and no dependencies.

## Features

- **Configurable colors from a brand palette** — the three pattern tones and the
  three overlay-bar colors are each chosen from a swatch palette (the DB brand
  colors plus the tones in use), or via a **Custom** picker for anything else.
  All six colors are set independently.
- **Zoom / scale** — slider, `+` / `−` buttons, or mouse-wheel (up to 2400%);
  the wheel zooms toward the cursor. The pattern stays crisp at every zoom level.
- **Pan** — drag to move the pattern.
- **Overlay bars** — larger copies of the pattern's base element (the slanted
  bar) that **snap precisely onto the lattice**:
  - three discrete sizes (S / M / L),
  - three configurable colors, distributed **⅓ / ⅓ / ⅓** across scattered bars,
  - **click empty canvas** to place a bar; **click a placed bar** to recolor it
    individually or delete it; plus Undo / Clear.
- **Aspect masks** — overlay a centered framing guide for common ratios
  (21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16). Save PNG crops to the
  active mask.
- **Save PNG** — export the current view (pattern + bars) at 2×.
- **Hide the menu** — the `×` button or the **M** key toggles the control panel.

More features will be added later.

## How it works

`pattern-data.js` holds the pattern's polygons (extracted from the source SVG),
replicated across its horizontal period (477 units) and pruned to a single
seamless tile. `index.html` draws them on a `<canvas>` as real vector geometry,
so there is no blur when zoomed in. When zoomed out it blits a cached
`ImageBitmap` of the tile (downscaled, still sharp) for speed; above the raster's
native scale it switches to vector.

The overlay bars reuse the pattern's **base element** — a parallelogram of
thickness `477/10`, height `2916.85/21`, shear `¾·height`. For a scaled copy to
line up exactly, its corners must fall on real pattern vertices, which only holds
for a sub-lattice of anchor points; `pattern-data.js` stores those **valid anchor
positions per size**, and placement snaps to them.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server
```

## Deployment

Pushes to `main` (or the active development branch) are published to GitHub
Pages via the workflow in `.github/workflows/deploy.yml`.
