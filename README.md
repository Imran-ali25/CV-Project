# 😴 Robust Face & Eye-Based Fatigue Detection Using EAR and PERCLOS on Jetson Nano

Real-time drowsiness detection using facial landmarks, Eye Aspect Ratio (EAR), and PERCLOS metrics, deployed on NVIDIA Jetson Nano 4GB with OpenCV and Dlib.

---

## 📋 Table of Contents
- Overview  
- Features  
- System Architecture  
- Project Structure  
- Installation  
- Dataset  
- Algorithm Details (EAR + PERCLOS)  
- Training (Optional for CNN/Landmark Refinement)  
- Deployment on Jetson Nano  
- Results  
- Literature Review  
- Team  
- Acknowledgments  
- References  
- License  

---

# 🎯 Overview
Fatigue and drowsiness contribute significantly to road accidents, industrial hazards, and reduced cognitive performance.  
This project implements a **non-intrusive, real-time fatigue detection system** using:

✔ Face detection  
✔ Eye landmark extraction  
✔ Eye Aspect Ratio (EAR)  
✔ PERCLOS (Percentage of Eye Closure)  

It runs entirely **on-device**, without cloud dependency, using:

- **NVIDIA Jetson Nano 4GB Developer Kit**
- **Logitech C270 HD Webcam**
- **OpenCV + Dlib + TensorRT (optional)**

---

# ⭐ Features

| Feature | Description |
|--------|-------------|
| Real-time Eye Tracking | 20–25 FPS on Jetson Nano |
| EAR Calculation | Detects micro-sleep, blinking, drooping eyelids |
| PERCLOS Monitoring | Reliable long-term fatigue index |
| Privacy-Preserving | Fully local on edge — no cloud |
| Expandable | Plug-in CNN or YOLO models |
| Low Power | Runs on 5–10W |

---

# 🧱 System Architecture

