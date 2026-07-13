# Pattern

A browser-based generator for a diagonal "weave" pattern, built as a single
self-contained `index.html` (HTML5 canvas, no dependencies).

## Features

- **Three configurable colors** — a base tone plus two dash tones, each set with
  a color picker.
- **Zoom / scale** — slider, `+` / `−` buttons, or mouse-wheel to scale the
  pattern.
- **Pan** — drag to shift the pattern.
- **Save PNG** — export the current canvas as an image.

More features will be added later.

## Run locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server
```

## Deployment

Pushes to `main` (or the active development branch) are published to GitHub
Pages via the workflow in `.github/workflows/deploy.yml`.
