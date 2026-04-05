# LunarCrater-Net 🌑

Automated detection of lunar impact craters using YOLOv8 
on NASA planetary imagery.

## Results

| Model | Dataset | mAP50 | mAP50-95 | Epochs |
|-------|---------|-------|----------|--------|
| YOLOv8n (baseline) | Synthetic, 100 tiles, tile_deg=60 | 0.0149 | 0.0085 | 17 |
| YOLOv8n (Phase 3) | Synthetic, 500 tiles, tile_deg=15 | 0.481 | 0.152 | 50 |

**32× improvement** from baseline by fixing tile resolution 
and increasing dataset size.

## Problem Statement

Manual crater counting is slow, subjective, and impossible 
to scale across planetary bodies. This project trains an 
object detection model to automatically locate and size 
lunar craters from grayscale terrain imagery.

## Dataset

- **Catalog:** Robbins Lunar Crater Database (2018) — 
  1.3M craters mapped from LRO imagery
- **Imagery:** Synthetic lunar tiles generated from 
  catalog coordinates (real LROC WAC imagery in progress)
- **Format:** YOLO annotation format 
  (class x_center y_center width height)
- **Split:** 70% train / 20% val / 10% test

## Installation
```bash
pip install ultralytics pandas numpy matplotlib pillow
```

## Usage

Open the notebooks in order:
1. `notebooks/Phase0_Foundations.ipynb` — environment setup
2. `notebooks/Phase1_Data.ipynb` — data pipeline
3. `notebooks/Phase2_Baseline.ipynb` — baseline training
4. `notebooks/Phase3_Improvements.ipynb` — improvements

## Key Findings

- Reducing tile coverage from 60° to 15° increased crater 
  box size from 0.003 to 0.022 — the single biggest 
  improvement factor
- mAP50 jumped from 0.0149 to 0.481 with three changes: 
  tile resolution, dataset size, and training duration
- Box loss still decreasing at epoch 50 — model has not 
  fully converged, suggesting further gains possible

## Future Work

- Replace synthetic catalog with real Robbins + LROC WAC imagery
- Scale to YOLOv8s for higher capacity
- Train to 100+ epochs
- Multi-scale crater evaluation (small/medium/large)
- Target: IEEE GRSL or ML4PS NeurIPS workshop submission

## References

- Silburt et al. (2019) — Lunar Crater Identification 
  via Deep Learning. arXiv:1803.02192
- Robbins (2018) — Lunar Crater Database. 
  doi:10.1029/2018JE005592
- Ultralytics YOLOv8
