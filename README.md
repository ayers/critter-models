# critter-models

Trained model artifacts for browser-native Critter inference.

## Layout

- `index.json`: model catalog consumed by apps.
- `models/spot/*.onnx`: ONNX actor exports.
- `models/spot/*.vecnormalize.json`: SB3 VecNormalize stats for observation normalization.

## Catalog format

`index.json` contains:

- `schemaVersion`: catalog schema version.
- `models[]`: one entry per model.
- Entry fields:
  - `id`, `name`
  - `robotKey` (used for UI relevance filtering)
  - `obsDim`, `actionDim`
  - `onnxPath`, `vecnormalizePath`
  - `notes`

## Usage notes

- Host this repo as static files (GitHub Pages/CDN/raw URLs).
- Browser inference must apply VecNormalize stats before ONNX `run()`.
- Output actions should be clipped to action bounds before applying controls.
