# 🚗 Vehicle Detection using YOLOv8, Faster R-CNN, and Fuzzy Hybrid Logic

This project presents a robust **vehicle detection system** combining:
- **YOLOv8** — a real-time object detector using YOLO-format dataset,
- **Faster R-CNN** — an accurate region-based CNN using COCO-style JSON annotations,
- and a custom **Fuzzy Logic layer** to fuse both model outputs for reliable final predictions.

---

## 📌 Objective

To improve vehicle detection accuracy and reliability by integrating predictions from two different models and applying fuzzy logic to handle uncertain or borderline cases effectively.

---

## 🧠 Method Overview

### 🔹 Step 1: Train Object Detectors

- **YOLOv8** was trained using a dataset in **YOLO format** (TXT files with normalized bounding boxes).
- **Faster R-CNN** was trained using a dataset in **COCO format** (JSON annotations with categories, images, and bounding boxes).
- The dataset was binary (Vehicle vs Background), preprocessed separately for each format.

### 🔹 Step 2: Perform Inference

- Both models generate bounding boxes and confidence scores on test images independently.

### 🔹 Step 3: Fuzzy Hybrid Decision

A custom **fuzzy inference system** was built using:
- YOLOv8 confidence score
- Faster R-CNN confidence score
- IoU (Intersection over Union) between predicted boxes

The fuzzy system outputs a final decision score for each candidate detection, allowing the system to:
- Fuse multiple detections
- Filter out uncertain predictions
- Enhance consistency and reduce false positives

---

## ✅ Why Use Fuzzy Logic?

While YOLOv8 offers **real-time detection speed**, it may be less precise in complex scenes.  
Faster R-CNN offers **high accuracy** but is slower.  
**Fuzzy logic** enables:
- Smarter fusion of model decisions
- Handling uncertain predictions with graded rules
- Reduction of false positives and conflicting outputs

---

## 🖼️ Example Output

| Image | YOLOv8 Output | Faster R-CNN Output | Fuzzy Decision |
|-------|---------------|----------------------|----------------|
| ![img](samples/image1.jpg) | Vehicle (0.91) | Vehicle (0.98) | ✅ Final Detection (Score: 0.96) |

---

## 🛠️ Technologies Used

- Python
- PyTorch
- YOLOv8 (Ultralytics)
- Faster R-CNN (TorchVision)
- OpenCV
- Fuzzy Logic (Manual Rule-Based)
- COCO and YOLO Datasets
- Evaluation Tools: Precision, Recall, Confusion Matrix, mAP

---

---

## 🚀 How to Use

There is no formal dependency file, but you will need:
- Python 3.8+
- PyTorch (tested on 1.13+)
- OpenCV
- Ultralytics YOLOv8
- Basic Python packages: numpy, matplotlib, etc.

To run:
1. Run YOLOv8 and Faster R-CNN inference on test images.
2. Pass their outputs to the `fuzzy_logic.py` script.
3. Visualize the final detection decisions.

---

## 📬 Contact

**Papince Kumar Gupta**  
📧 [papince2059@gmail.com](mailto:papince2059@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/papince/)

---

## 🏷️ Acknowledgements

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- [TorchVision Detection Models](https://pytorch.org/vision/stable/models.html)
- Concept of fuzzy systems from [scikit-fuzzy](https://github.com/scikit-fuzzy/scikit-fuzzy)
