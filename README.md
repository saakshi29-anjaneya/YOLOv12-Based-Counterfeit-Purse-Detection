# Efficient Image Spoofing Detection using YOLOv12 and Siamese Networks

This project implements an end-to-end **Embedded Intelligent Systems (EIS)** pipeline for detecting counterfeit brand logos using a combination of **object detection**, **synthetic data generation**, and **metric learning**. The system integrates YOLOv12 for logo detection and a Siamese neural network for brand authenticity verification.

The workflow is designed to be modular, scalable, and suitable for academic research and real-world experimentation.

---

## Project Overview

The pipeline addresses the problem of fake brand logo detection through the following stages:

* Automatic logo detection using **YOLOv12**
* Synthetic fake logo generation using **Stable Diffusion**
* Dataset organization and preprocessing
* Feature-based brand similarity learning using a **Siamese Network**
* Final authenticity decision based on similarity scores

This hybrid approach combines spatial localization with semantic similarity learning for robust spoof detection.

---

## System Architecture

### 1. Dataset Preparation

* Real logo images collected via Roboflow
* Fake logo images generated using Stable Diffusion with prompt-based logo manipulation
* Data augmentation and preprocessing
* YOLOv12-compatible label generation

---

### 2. YOLOv12 Model Training

* YOLOv12 repository cloned and configured
* Model trained on a custom logo detection dataset
* Hyperparameters tuned for efficient convergence
* Best-performing model weights saved (`best.pt`)

YOLOv12 is used to accurately localize logos within images.

---

### 3. Logo Cropping and Dataset Organization

* Detected logos are cropped from images
* Cropped logos are automatically organized into brand-specific folders
* Enables structured input for metric learning

---

### 4. Synthetic Fake Logo Generation

* Stable Diffusion v1.5 used for generating counterfeit logo images
* Prompts introduce subtle logo spelling and style variations
* Synthetic images expand the fake data distribution

---

### 5. Siamese Network for Brand Verification

* ResNet18 backbone used for feature extraction
* Siamese architecture trained on logo pairs
* Learns inter-brand similarity and dissimilarity
* Binary classification output indicating authenticity

---

### 6. Inference Pipeline

1. Input image passed through YOLOv12 for logo detection
2. Detected logo region cropped
3. Cropped logo compared against known real logos
4. Maximum similarity score computed
5. Final decision made based on similarity threshold

---

## Technologies Used

* **YOLOv12** – Logo detection
* **PyTorch** – Model training and inference
* **Ultralytics** – YOLO training framework
* **Stable Diffusion** – Synthetic fake image generation
* **Roboflow** – Dataset management
* **OpenCV / PIL** – Image processing
* **FAISS** – Scalable similarity search

---

## Results and Observations

* Accurate logo localization using YOLOv12
* Improved robustness through synthetic fake data
* Siamese network effectively differentiates real vs fake logos
* Suitable for extension to multiple brands and domains

---

## Notes

* Large datasets and trained weights are excluded due to GitHub size limits
* Models are trained and tested in Google Colab
* GPU acceleration recommended for training and image generation

---

## Use Cases

* Counterfeit product detection
* Brand protection systems
* Visual similarity analysis
* Academic research in multimodal vision systems
