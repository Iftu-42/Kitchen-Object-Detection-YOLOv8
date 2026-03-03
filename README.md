# 🍴 YOLOv8 Kitchen Utensil Detection

---

## 📌 Project Overview
This project focuses on the development of a robust object detection system tailored for smart kitchen environments. Using the **YOLOv8 Nano** architecture, the model was trained to accurately identify and track common kitchenware specifically **Spoons, Forks, and Knives** even in dynamic, high-motion video sequences.

---

## 🚀 Technical Performance
After rigorous testing between Nano, Small, and Medium models, the **Nano** version was selected for its superior real-time efficiency.

| Metric | Result | Why it matters? |
| :--- | :--- | :--- |
| **mAP50** | **0.95** | 95% accuracy in correctly identifying objects. |
| **Inference Speed** | **2.14ms** | Faster than the human eye; perfect for live edge devices. |
| **Peak Confidence** | **0.81** | Exceptional certainty even with complex metallic reflections. |
| **Real-Time Speed** | **9.5ms/frame** | Proven capability to process 105+ Frames Per Second (FPS). |

---

## 📸 Final Inference Results
The model was validated using the weights from the **train11** session, demonstrating strong generalization on both static and moving subjects.

### **📍 The "Star" Performer: Metal Fork**
* **Confidence**: **0.81**
* **Analysis**: The model has successfully learned the unique geometric features and metallic textures of forks, providing high-certainty detection.

### **📍 The Real-Time Test: Wooden Spoon**
* **Confidence**: **0.49**
* **Analysis**: Despite the motion blur in the dynamic GIF, the model maintained a stable bounding box throughout the entire sequence.

---

## 💡 Lessons Learned
During this project, I discovered that metallic objects like forks provide strong features for detection, resulting in high confidence scores. I also learned that motion blur can lower confidence, but by optimizing the model to run at **9.5ms per frame**, we can maintain a stable "real-time" track without flickering.

---

## 📂 Repository Contents
* **Final_Workshop_Kitchen_Detection.ipynb**: Complete training pipeline and inference logs.
* **weights/best.pt**: Optimized model weights from the `train11` directory.
* **fork.png** and **spoon.png**: Final inference result images.
* **big spoon.gif**: Input file used for real-time performance demonstration.

---

## 🔮 Future Improvements
Dataset Expansion: Adding more diverse kitchen tools like spatulas and whisks.

Edge Deployment: Converting the best.pt model to TensorRT or ONNX for even faster performance on mobile hardware.

## 🛠️ Technology Stack
Language: Python 3.12

Library: Ultralytics YOLOv8

Hardware: NVIDIA T4 GPU via Google Colab

Data Format: Roboflow YOLOv8 format

## 🛠️ Reproduction Guide
### **Setup**
Clone this repo and install the requirements:
```bash
pip install ultralytics

from ultralytics import YOLO
model = YOLO('weights/best.pt')
model.predict(source='big spoon.gif', save=True, conf=0.25)
