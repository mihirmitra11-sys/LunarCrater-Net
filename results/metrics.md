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

## Section 6- Discussion
Our results demonstrate that Reducing tile coverage from 60° to 15° increased crater box size from 0.003 to 0.022 — the single biggest improvement factor, mAP50 jumped from 0.0149 to 0.481 with three changes: tile resolution, dataset size, and training duration. This suggests that in small object detection tasks, reducing tile resolution is the dominant factor in small object detection performance for planetary imagery. 
The primary limitation of this work is our synthetic data overestimated real-world performance —our mAP50 reduced from 0.481 to 0.298 despite having 100 epochs 
Future work should incorporate real LROC WAC imagery instead of synthetic tiles, upgrade to YOLOv8s for higher model capacity, and evaluate performance separately on small, medium, and large craters to understand detection failure modes.

## Abstract
Automated lunar crater detection is critical as accurate crater maps are essential for safe landing site selection and surface navigation.
We present LunarCrater-Net, an automated crater detection pipeline using YOLOv8n fine-tuned via transfer learning on the Robbins (2018) lunar crater catalog.
Our key finding is that by decreasing tile_deg from 60 to 15, our mAP50 increased from 0.0149 to 0.481 and crater box size increased from 0.003 to 0.022. 
These results suggest that tile resolution is a critical and often overlooked parameter in planetary small object detection, with implications beyond lunar crater mapping to other bodies in the Solar System.
