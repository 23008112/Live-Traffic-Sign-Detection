

---

# 🚦 Live Traffic Sign Detection using YOLO

This project implements **real-time traffic sign detection** using the YOLO (You Only Look Once) object detection algorithm. It uses **custom-labeled image data** for training and performs **live detection** through a webcam feed.

---

## 📌 Project Overview

* **Goal**: Detect and classify traffic signs in real-time from a webcam feed.
* **Model Used**: YOLOv5 / YOLOv8 (configurable)
* **Training Data**: Custom traffic sign images annotated in YOLO format.
* **Frameworks**: PyTorch, OpenCV
* **Applications**: Smart driving systems, ADAS (Advanced Driver Assistance Systems), autonomous vehicles.

---

## 📂 Folder Structure

```
Live-Traffic-Sign-Detection/
│
├── dataset/
│   ├── images/
│   │   ├── train/
│   │   └── val/
│   └── labels/
│       ├── train/
│       └── val/
│
├── weights/
│   └── best.pt                  # Trained YOLO model
│
├── detect.py                    # Script for live detection
├── train.py                     # Training script using YOLO
├── data.yaml                    # Dataset configuration
├── requirements.txt
└── README.md
```

---

## 🧠 YOLO Training Setup

1. **Annotation Format**: YOLO (bounding box in `label.txt` with class x\_center y\_center width height).

2. **Data YAML Example**:

   ```yaml
   train: dataset/images/train
   val: dataset/images/val

   nc: 5
   names: ['Stop', 'Speed Limit', 'Yield', 'No Entry', 'Pedestrian']
   ```

3. **Training Command** (for YOLOv5):

   ```bash
   python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt --cache
   ```

---

## 🎯 Live Detection (Webcam)

Run the live detection script:

```bash
python detect.py --weights weights/best.pt --source 0 --conf 0.25
```

* `--source 0`: Uses webcam
* `--conf`: Confidence threshold
* You can also use a video file: `--source path/to/video.mp4`

---

## 📸 Preparing Your Dataset

1. **Collect Images**: Download or capture traffic sign images.
2. **Label Images**: Use [LabelImg](https://github.com/tzutalin/labelImg) or [Roboflow](https://roboflow.com).
3. **Export Format**: YOLO format (`.txt` with same name as image).

---

## 📦 Requirements

Install dependencies:

```bash
pip install -r requirements.txt
```

**requirements.txt**:

```
torch>=1.8
opencv-python
numpy
matplotlib
PyYAML
```

If you're using YOLOv5, clone and install it:

```bash
git clone https://github.com/ultralytics/yolov5
cd yolov5
pip install -r requirements.txt
```

---

## 📈 Evaluation Metrics

During training:

* **Precision**
* **Recall**
* **mAP\@0.5**
* **Loss curves**

To evaluate the model post-training:

```bash
python val.py --data data.yaml --weights weights/best.pt
```

---

## ✅ Tips for Better Accuracy

* Use **balanced class distribution**
* Ensure **varied lighting and backgrounds**
* Use **image augmentation** (YOLO does this by default)
* Train for enough **epochs** until validation loss stabilizes

---

## 💡 Future Work

* Add support for **YOLOv8**
* Integrate with **GPS and navigation**
* Improve **low-light performance**
* Deploy on **mobile or edge devices**

---

## 🤝 Acknowledgements

* [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)
* OpenCV for video streaming
* Roboflow for dataset preprocessing

---

## 📬 Contact

---
