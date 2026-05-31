# Road-Ware-Detection

**Real-time road pothole and driver drowsiness detection using a single monocular camera.**

Bachelor's thesis project built for the Government of India. Detects potholes and driver drowsiness in real-time video using YOLOv5, optimised for edge deployment via model pruning and quantisation.

📄 **Published research:** [CNN-based Pothole & Driver Drowsiness Detection for Monitoring Road Condition](https://doi.org/10.48175/IJARSCT-11246)  
*International Journal of Advanced Research in Science, Communication and Technology (IJARSCT), Vol. 3, Issue 1, June 2023 · Crossref-indexed · Peer-reviewed*

---

## Results

| Metric | Value |
|--------|-------|
| Detection accuracy | **92%** |
| Inference speedup (post-optimisation) | **45%** |
| Optimisation method | Model pruning + INT8 quantisation |
| Deployment target | Edge devices (single monocular camera) |
| Severity classification | Small / Medium / Large |

---

## What it detects

**1. Pothole detection** — real-time bounding boxes on road surface damage, classified by severity (small / medium / large). Structured records logged to a database for Government of India road maintenance teams.

**2. Driver drowsiness detection** — facial landmark analysis to detect eye closure and head drop patterns indicating fatigue, triggering an alert before an incident occurs.

---

## How it works

1. **Input** — live video stream from a single monocular camera mounted on a vehicle
2. **Detection** — YOLOv5 model trained on annotated road surface images classifies pothole regions frame by frame
3. **Severity classification** — detected potholes categorised by size for maintenance prioritisation
4. **Drowsiness** — secondary CV module (`detect_drowsiness.py`) monitors driver facial landmarks
5. **Logging** — structured records written to database for downstream maintenance workflows
6. **Optimisation** — model pruned and quantised to achieve 45% inference speedup while maintaining 92% accuracy

---

## Stack

- **Model:** YOLOv5 (PyTorch)
- **Computer Vision:** OpenCV, TensorFlow/Keras (drowsiness module)
- **Backend:** Python, Flask (`mySite.py`)
- **Optimisation:** Model pruning + INT8 quantisation

---

## Project structure

```
Road-Ware-Detection/
├── classify/             # Classification utilities
├── data/                 # Training and test data
├── models/               # YOLOv5 model weights
├── static/               # Static assets for web interface
├── templates/            # HTML templates
├── utils/                # Helper functions
├── detect.py             # Pothole detection script
├── detect_drowsiness.py  # Driver drowsiness CV module
├── mySite.py             # Flask web server
└── supportFile.py        # Support utilities
```

---

## Running locally

```bash
git clone https://github.com/parth-patwardhan/Road-Ware-Detection.git
cd Road-Ware-Detection
pip install -r requirements.txt

# Run detection on a video file
python detect.py --source path/to/video.mp4

# Or launch the web interface
python mySite.py
```

---

## Publication

If you use this work, please cite:

> Patwardhan, P. P. et al. (2023). *Convolutional Neural Network based Pothole and Driver Drowsiness Detection for Monitoring Road Condition.* International Journal of Advanced Research in Science, Communication and Technology (IJARSCT), Vol. 3, Issue 1. DOI: [10.48175/IJARSCT-11246](https://doi.org/10.48175/IJARSCT-11246)

---

*Part of the portfolio of [Parth Patwardhan](https://github.com/parth-patwardhan) — AI Engineer, Universität Stuttgart.*
