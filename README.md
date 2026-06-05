# 🍅 Tomato Leaf Care - Plant Disease Prediction System

A modern, deep learning-powered web application designed to help farmers, agronomists, and garden enthusiasts instantly diagnose tomato leaf diseases and receive actionable, science-backed treatment recommendations.

![Deep Learning](https://img.shields.io/badge/Deep%20Learning-TensorFlow%20%2F%20Keras-orange)
![Computer Vision](https://img.shields.io/badge/Computer%20Vision-OpenCV-blue)
![Web Framework](https://img.shields.io/badge/Backend-Flask-green)
![Deployment](https://img.shields.io/badge/Deployment-PythonAnywhere-yellow)

---

## 🌟 Key Features

1. **Instant AI Diagnosis:** Upload a close-up image of a tomato leaf, and the custom deep learning model classifies it into one of 10 categories (9 diseases + healthy state) in milliseconds.
2. **Robust Out-of-Distribution (OOD) Verification:** Integrated safety filters prevent false positives from non-leaf images or unrelated content:
   * **Color Check (HSV):** Uses OpenCV to ensure the image contains at least 5% foliage tones (greens, yellows, and browns).
   * **Feature Activation Check:** Inspects the L2 Norm, Mean, and Max activation values at the neural network's penultimate layer to mathematically reject out-of-distribution patterns (e.g., rejecting an image of a green car).
3. **Actionable Treatments:** Provides detailed, organic, and chemical treatment routines for every diagnosed disease.
4. **Modern Glassmorphism UI:** A high-end interface built with frosted-glass containers, side-by-side image comparisons, and fully responsive CSS.
5. **Lightweight Fallback Support:** Native support for `tflite-runtime` ensures the model can run on low-memory servers (like the PythonAnywhere Free Tier) without crashing.

---

## 📋 Supported Disease Categories

The neural network is trained to identify the following conditions:

| Diagnosis Label | Status | Example Treatment Approach |
| :--- | :--- | :--- |
| **Healthy and Fresh** | Clean Foliage | N/A |
| **Bacteria Spot Disease** | Infected | Copper fungicides |
| **Early Blight Disease** | Infected | Liquid Copper / Organic Fungicides |
| **Late Blight Disease** | Infected | Immediate organic/chemical fungicide intervention |
| **Leaf Mold Disease** | Infected | Pruning, drip irrigation, airflow increase |
| **Septoria Leaf Spot** | Infected | Potassium bicarbonate, Chlorothalonil |
| **Target Spot Disease** | Infected | Mancozeb, copper oxychloride |
| **Tomato Mosaic Virus** | Infected | Eradication (Incurable, preventative tools only) |
| **Yellow Leaf Curl Virus** | Infected | Azadirachtin (Neem), insecticidal soaps for whiteflies |
| **Two Spotted Spider Mite** | Infected | Bifenazate, Neem oil, selective miticides |

---

## 🛠️ Technical Architecture

* **Frontend:** HTML5, CSS3 (Custom Glassmorphism Design System), Bootstrap 4.5.1, Vanilla JavaScript.
* **Backend:** Python 3, Flask framework.
* **Computer Vision:** OpenCV (`cv2`) for HSV masking.
* **Deep Learning Inference:** 
  * Primary: TensorFlow/Keras (`model.h5`)
  * Lightweight Fallback: TensorFlow Lite (`model.tflite`) for resource-constrained environments.

---

## 🚀 Running Locally

### Prerequisites
Make sure Python 3.9+ is installed on your machine.

1. **Clone the repository and enter the directory.**
2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```
3. **Install the dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Start the Web Server:**
   ```bash
   python leaf.py
   ```
5. **Access the Interface:**
   Open your web browser and go to `http://127.0.0.1:5001`.

---

## ☁️ Deployment (PythonAnywhere)

Deploying machine learning models to free cloud tiers is notoriously difficult due to strict memory (RAM) and disk space limits (512MB).

We have solved this by implementing a `tflite-runtime` fallback mechanism inside `leaf.py`. 

**For a complete, step-by-step guide on how to successfully deploy this exact project to PythonAnywhere without hitting disk quota or memory crashes, please read the included [PythonAnywhere Deployment Guide](pythonanywhere_deployment_guide.md).**

---

## 📂 Directory Structure

```text
├── leaf.py                     # Core Flask application and prediction logic
├── requirements.txt            # Python dependencies
├── pythonanywhere_deployment_guide.md  # Detailed cloud deployment guide
├── model.tflite                # Lightweight quantized model for deployment
├── model.h5                    # Full TensorFlow Keras model
├── static/
│   ├── css/                    # Glassmorphism and Bootstrap stylesheets
│   ├── images/                 # UI assets and reference images
│   └── upload/                 # Temporary storage for user uploads
└── templates/
    ├── index.html              # Main upload interface
    ├── unrecognized.html       # OOD Rejection page
    └── Tomato-*.html           # 10 specific disease diagnosis pages
```
