# YOLO-Based Vehicle Speed Estimation from Aerial Video

**Goal**:  Estimates vehicle speeds from aerial drone footage, where vehicles are small and often occluded. A YOLOv8 detector, custom-trained on UAVDT with tuned resolution and augmentation, feeds DeepSORT (Kalman filter + appearance embeddings) for multi-object tracking. Speeds are computed from the tracked trajectories and overlaid on the output video.

## Current Stage
Fine-tuning YOLO for better detetction

## What Works

## What doesn't work
