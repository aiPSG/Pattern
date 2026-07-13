# Pattern

A browser-based generator for the **DB diagonal logo pattern**. The exact vector
artwork is turned into a seamless, recolorable, zoomable SVG tile — no build
step, no dependencies.

## Features

- **Three configurable colors** — each of the pattern's three tones can be set
  via a color-picker swatch **or** by typing a hex value (`#RRGGBB` / `#RGB`).
- **Zoom / scale** — slider, `+` / `−` buttons, or mouse-wheel.
- **Pan** — drag to move the pattern.
- **Save PNG** — export the current view as a 2× PNG.

More features will be added later.

## How it works

`pattern-data.js` holds the pattern's polygons (extracted from the source SVG),
already replicated across its horizontal period (477 units) and pruned to a
single seamless tile. `index.html` renders them as an SVG `<pattern>` whose three
colour groups and `patternTransform` (scale + translate) are updated live.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server
```

## Deployment

Pushes to `main` (or the active development branch) are published to GitHub
Pages via the workflow in `.github/workflows/deploy.yml`.
