# Drone Vehicle Speed Estimation with YOLOv8 + DeepSORT

Detect, track and estimate the speed of vehicles in top-down drone footage.
A YOLOv8s detector is fine-tuned on the **UAVDT** aerial dataset, objects are tracked across frames with **DeepSORT**, and each vehicle's speed (km/h) is computed from its tracked motion. The pixel-to-metre scale is auto-calibrated from the size of detected cars.

## Highlights
- **Dataset conversion**: UAVDT annotations to YOLO format, with a sequence-level train/val split to avoid frame leakage (2,134 train / 580 val images).
- **Transfer learning**: COCO-pretrained `yolov8s` fine-tuned with augmentations suited to aerial views (vertical flips, rotation, mosaic, HSV jitter).
- **Multi-object tracking**: DeepSORT with a MobileNet appearance embedder and Kalman-smoothed boxes.
- **Speed estimation**: sliding-window displacement, EMA smoothing, and outlier rejection.
- **Automatic calibration**: metres-per-pixel estimated as 4.5 m / median detected car length, so no manual camera parameters are needed.

## Requirements
- ultralytics
- deep-sort-realtime
- opencv-python
- torch
- numpy
- pandas
- matplotlib
- tqdm

## Run it
1. Open the notebook in Google Colab and set **Runtime → Change runtime type → T4 GPU**.
2. Download UAVDT (*"The Unmanned Aerial Vehicle Benchmark: Object Detection and Tracking"*, Du et al., ECCV 2018) and place the zip files in `MyDrive/UAVDT/` on Google Drive.
3. Run all cells. You'll be asked to upload a drone video for the speed-estimation part.

Outputs: an annotated video (`speed_output_custom.mp4`) and a per-frame CSV of track IDs, positions and speeds (`speeds_custom.csv`).

## Limitations
- Assumes a near top-down camera and flat ground (a single scale for the whole frame).
- Speed accuracy depends on the average-car-length assumption and hasn't been validated against GPS ground truth.
- Trucks and buses are under-represented in UAVDT.

## Tech stack
Python, PyTorch, Ultralytics YOLOv8, DeepSORT, OpenCV, pandas, Google Colab

## Acknowledgements
UAVDT dataset by Du et al. (ECCV 2018). The dataset and trained weights are not distributed in this repo.
