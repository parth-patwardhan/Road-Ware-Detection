# Road-Ware-Detection

**Real-time road pothole detection using a single monocular camera.**

Bachelor's thesis project built for the Government of India. Detects potholes in real-time video using YOLOv5, optimised for edge deployment via model pruning and quantisation.

---

## Results

| Metric | Value |
|--------|-------|
| Detection accuracy | **92%** |
| Inference speedup (post-optimisation) | **45%** |
| Optimisation method | Model pruning + quantisation |
| Deployment target | Edge devices (single monocular camera) |

---

## How it works

1. **Input** — live video stream from a single monocular camera mounted on a vehicle
2. **Detection** — YOLOv5 model trained on annotated road surface images classifies pothole regions frame-by-frame
3. **Optimisation** — model pruned and quantised to reduce inference time by 45% while maintaining 92% accuracy
4. **Output** — bounding boxes with confidence scores overlaid on the video stream; alarm triggered on detection

---

## Stack

- **Model**: YOLOv5 (PyTorch)
- **Computer Vision**: OpenCV
- **Backend**: Python (Flask via `mySite.py`)
- **Data**: Custom annotated dataset (`data/`), pre-trained shape predictor for landmark detection
- **Inference optimisation**: Pruning + INT8 quantisation

---

## Project structure

```
Road-Ware-Detection/
├── classify/          # Classification utilities
├── data/              # Training and test data
├── models/            # YOLOv5 model weights
├── static/            # Static assets for web interface
├── templates/         # HTML templates
├── utils/             # Helper functions
├── detect.py          # Main detection script
├── detect_drowsiness.py  # Secondary CV module
├── mySite.py          # Flask web server
└── supportFile.py     # Support utilities
```

---

## Running locally

```bash
# Clone the repo
git clone https://github.com/parth-patwardhan/Road-Ware-Detection.git
cd Road-Ware-Detection

# Install dependencies
pip install -r requirements.txt

# Run detection on a video file
python detect.py --source path/to/video.mp4

# Or run the web interface
python mySite.py
```

---

## Context

Built as part of a B.E. Computer Science degree at Pune University (2022). The system was developed for Government of India infrastructure monitoring use cases — providing a low-cost, camera-only alternative to LiDAR-based road survey equipment.

---

*Part of the portfolio of [Parth Patwardhan](https://github.com/parth-patwardhan) — AI/ML Engineer, Universität Stuttgart.*
