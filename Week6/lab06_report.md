# Lab 06 — YOLO aquarium results
## Test-set metrics (Ultralytics `model.val`, `split=test`)
Stage | Precision | Recall | mAP50 | mAP50-95
Pretrained yolo26n (COCO) | 0.0279 | 0.0545 | 0.0250 | 0.0185
Fine-tuned best.pt | 0.6507 | 0.4651 | 0.5534 | 0.3278
Training outputs under `runs_lab06/`.