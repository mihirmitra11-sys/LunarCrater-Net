# Model Performance Metrics

## Phase 2 — Baseline
- mAP50: 0.0149
- mAP50-95: 0.0085
- Epochs: 17 (early stopped)
- box_loss final: 4.2

## Phase 3 — Improvements
- mAP50: 0.481
- mAP50-95: 0.152
- Epochs: 50
- box_loss final: 3.18
- Improvement: 32x over baseline

## Section 2 — Related Work

Silburt et al. (2019) demonstrated a model that was CNN 
trained from scratch on lunar DEMs achieving 92% recall 
on known craters. However, training from scratch requires 
large datasets and significant computations making it hard 
to reproduce or adapt to other planetary bodies. In contrast, 
LunarCrater-Net uses YOLOv8 with transfer learning, which 
outputs bounding boxes with coordinates instead of just 
detection masks.
