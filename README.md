# 😴 Robust Face & Eye-Based Fatigue Detection Using EAR and PERCLOS on Jetson Nano

Real-time drowsiness detection using facial landmarks, Eye Aspect Ratio (EAR), and PERCLOS metrics, deployed on NVIDIA Jetson Nano 4GB with OpenCV and Dlib.

---

## 📋 Table of Contents
## 📋 Table of Contents
- [Overview](#-overview)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Dataset](#-dataset)
- [Algorithm Details (EAR + PERCLOS)](#-algorithm-details-ear--perclos)
- [Training (Optional for CNN/Landmark Refinement)](#-training-optional-for-cnnlandmark-refinement)
- [Deployment on Jetson Nano](#-deployment-on-jetson-nano)
- [Results](#-results)
- [Literature Review](#-literature-review)
- [Team](#-team)
- [Acknowledgments](#-acknowledgments)
- [References](#-references)
- [License](#-license)


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

The system runs entirely on the NVIDIA Jetson Nano and performs all AI processing locally.

```
Webcam → Face Detector → Eye Landmark Detector → EAR Calculation → PERCLOS Computation → Fatigue Decision
```

### 🔧 Components
- **Camera Module** – Logitech C270 captures live video  
- **Face Detection** – Dlib HoG / CNN or OpenCV DNN  
- **Facial Landmarks** – 68-point predictor  
- **EAR Module** – Calculates Eye Aspect Ratio per frame  
- **PERCLOS Module** – Tracks % of frames where eyes are closed  
- **Alert System** – Buzzer/LED/On-screen warning  

---

# 📁 Project Structure

```
fatigue-detection/
│── models/
│   ├── shape_predictor_68_face_landmarks.dat
│── src/
│   ├── main.py
│   ├── ear.py
│   ├── perclos.py
│   ├── face_detector.py
│── utils/
│   ├── helpers.py
│── docs/
│   ├── report.pdf
│── README.md
│── requirements.txt
```

---

# 🛠 Installation

### 1️⃣ Clone Repository
```bash
git clone https://github.com/username/fatigue-detection.git
cd fatigue-detection
```

### 2️⃣ Install Dependencies
```bash
sudo apt-get update
sudo apt-get install python3-pip cmake libopenblas-dev liblapack-dev libx11-dev

pip3 install -r requirements.txt
```

### 3️⃣ Add Facial Landmark Model  
Download:
```
shape_predictor_68_face_landmarks.dat
```
Place it inside:
```
/models
```

---

# 📦 Dataset (Optional)

If training your own models:

- **Eye Blink Dataset (CEW)**
- **Closed Eye Kaggle Dataset**
- **Drowsiness Dataset (Yawn + Eyes)**

---

# 🔍 Algorithm Details

## 1️⃣ Eye Aspect Ratio (EAR)
EAR is computed using eye-landmark coordinates:

```
EAR = (‖p2−p6‖ + ‖p3−p5‖) / (2 * ‖p1−p4‖)
```

Low EAR → Eyes closing  
EAR < 0.25 → Drowsiness indication  

---

## 2️⃣ PERCLOS (Percentage of Eye Closure)

```
PERCLOS = (Closed_Eye_Frames / Total_Frames) * 100
```

Threshold:
- > 70% → High fatigue  
- 40–70% → Moderate fatigue  

---

# 🏋️ Training (Optional CNN Model)

To train your own blink classifier:

```bash
python3 train_model.py
```

Outputs:
```
model_eye_state.h5
```

---

# 🚀 Deployment on Jetson Nano

### Enable 10-W performance mode:
```bash
sudo nvpmodel -m 0
sudo jetson_clocks
```

### Run Model
```bash
python3 src/main.py
```

---

# 📊 Results

| Metric | Value |
|--------|-------|
| EAR Accuracy | ~92% |
| PERCLOS Accuracy | ~90% |
| FPS on Jetson Nano | 20–25 FPS |
| False Alarms | Low |

---

# 📚 Literature Review

- Bergasa et al. — Real-time Drowsiness Based on Eye Closure  
- PERCLOS Standard defined by US DOT / NHTSA  
- Soukupová & Čech — EAR formulation  

---

# 👥 Team
| Name             | Role                        | Responsibilities                                                                 |
|-----------------|-----------------------------|-------------------------------------------------------------------------------|
| Imran Ali        | Research & Documentation Lead | Literature review, proposal writing, GitHub management, final report          |
| Ali Ahsan        | Simulation & Training Lead    | Dataset preparation, model training, algorithm pipeline, Google Colab         |
| H. Adeela Arif   | Embedded Systems Lead         | Jetson Nano deployment, TensorRT optimization, hardware benchmarking          |


---

# 🙏 Acknowledgments
- NVIDIA Jetson Community  
- Dlib + OpenCV Contributors  

---

# 📖 References
- OpenCV Documentation  
- Dlib Library  
- Research Papers on PERCLOS & EAR  

---

# 📝 License
MIT License


