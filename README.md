# YOLO-Based Vehicle Speed Estimation from Aerial Video

**Goal**:  Estimates vehicle speeds from aerial drone footage, where vehicles are small and often occluded. A YOLOv8 detector, custom-trained on UAVDT with tuned resolution and augmentation, feeds DeepSORT (Kalman filter + appearance embeddings) for multi-object tracking. Speeds are computed from the tracked trajectories and overlaid on the output video.

## Current Stage
Fine-tuning YOLO for better detetction using UAVDT dataset.

## What Works

## What doesn't work

## References
- This project uses the [UAVDT](https://sites.google.com/view/grli-uavdt) benchmark:
D. Du, Y. Qi, H. Yu, Y. Yang, K. Duan, G. Li, W. Zhang, Q. Huang, and Q. Tian, "The Unmanned Aerial Vehicle Benchmark: Object Detection and Tracking," in *European Conference on Computer Vision (ECCV)*, 2018.

