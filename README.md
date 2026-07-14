# LunarCrater-Net 🌑

Automated detection of lunar impact craters using YOLOv8
on NASA planetary imagery.

## Results

| Model | Dataset | mAP50 | mAP50-95 | Epochs |
|-------|---------|-------|----------|--------|
| YOLOv8n (baseline) | Synthetic, 100 tiles, tile_deg=60 | 0.0149 | 0.0085 | 17 |
| YOLOv8n (Phase 3) | Synthetic, 500 tiles, tile_deg=15 | 0.481 | 0.152 | 50 |
| YOLOv8n (Phase 4) | Real Robbins, 500 tiles, tile_deg=15 | 0.298 | 0.124 | 100 |

**32× improvement** from baseline by fixing tile resolution
and increasing dataset size.

**Real data finding:** Switching to real Robbins catalog
reduced mAP50 from 0.481 to 0.298 — real crater clustering
patterns are harder to learn than uniform synthetic distributions.

## Problem Statement

Manual crater counting is slow, subjective, and impossible
to scale across planetary bodies. This project trains an
object detection model to automatically locate and size
lunar craters from grayscale terrain imagery.

## Dataset

- **Catalog:** Robbins Lunar Crater Database (2018) —
  1.3M craters mapped from LRO imagery
- **Filter:** Craters ≥ 5 km diameter only (WAC imagery
  at 100m/px cannot resolve smaller craters)
- **Imagery:** Synthetic lunar tiles generated from
  catalog coordinates (real LROC WAC imagery in progress)
- **Format:** YOLO annotation format
  (`class x_center y_center width height`)
- **Split:** 70% train / 20% val / 10% test

## Installation

```bash
pip install ultralytics pandas numpy matplotlib pillow
```

## Usage

Open the notebook in order:

Covers Phase 0 (foundations) → Phase 1 (data) →
Phase 2 (baseline) → Phase 3 (improvements) →
Phase 4 (real data)

## Key Findings

- Reducing tile coverage from 60° to 15° increased crater
  box size from 0.003 to 0.022 — the single biggest
  improvement factor (32× mAP50 improvement)
- Real Robbins catalog data is harder than synthetic —
  mAP50 drops from 0.481 to 0.298 due to non-uniform
  crater clustering in highlands vs maria
- Box loss still decreasing at epoch 50 — model has not
  fully converged, suggesting further gains possible
- Synthetic data overestimates real-world performance —
  a finding relevant to any ML pipeline using simulated
  planetary data

## Paper

See `LunarCrater_Net_Paper.pdf` for the full 4-page
research paper targeting ML4PS NeurIPS 2026 workshop.

## Future Work

- Replace synthetic imagery with real LROC WAC tiles
- Scale to YOLOv8s for higher capacity
- Train to 100+ epochs
- Multi-scale crater evaluation (small/medium/large)
- Target: ML4PS NeurIPS 2026 workshop submission

## References

- Silburt et al. (2019) — Lunar Crater Identification
  via Deep Learning. arXiv:1803.02192
- Robbins (2018) — Lunar Crater Database.

- ## Paper
**Preprint:** [doi.org/10.5281/zenodo.21348960](https://doi.org/10.5281/zenodo.21348960)
  doi:10.1029/2018JE005592
- Ultralytics YOLOv8
## Usage

Open the notebook in order:
