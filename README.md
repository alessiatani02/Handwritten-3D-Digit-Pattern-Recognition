# Handwritten-3D-Digit-Pattern-Recognition
This project addresses the problem of recognizing hand-drawn digits from **3D motion trajectories** captured by a Leap Motion sensor.  
Each digit is drawn in mid-air and represented as a variable-length 3D time series.

The goal is to design a **complete pattern recognition pipeline** that maps a single 3D trajectory to one of the ten digit classes (0–9).

---

## Overview

The system consists of:
- A **preprocessing pipeline** that converts variable-length trajectories into fixed-dimensional feature vectors
- A **custom implementation of a linear soft-margin SVM**, trained using the Sequential Minimal Optimization (SMO) algorithm
- A **One-vs-One multiclass strategy** to handle the 10-class digit recognition task

The final model achieves high accuracy while remaining interpretable and computationally efficient.

---

## Preprocessing Pipeline

Each 3D trajectory undergoes the following steps:

1. Translation to the origin  
2. Arc-length normalization  
3. Uniform resampling  
4. Velocity computation  
5. Feature vector construction via concatenation of positions and velocities  

This process ensures invariance to drawing speed, scale, and absolute position.

---

## Classification Model

- **Classifier:** Linear soft-margin Support Vector Machine
- **Training algorithm:** Sequential Minimal Optimization (SMO)
- **Multiclass strategy:** One-vs-One (45 binary classifiers)
- **Hyperparameter tuning:** 5-fold cross-validation

The linear kernel was preferred to avoid overfitting while maintaining strong generalization performance.

---

## Results

- **Training accuracy:** ~94%
- **Test accuracy:** ~92%
- Consistently high precision, recall, and F1-scores across all digit classes
- Confusion matrices show strong diagonal dominance, indicating robust classification

---

## digit_classify Function

A dedicated function `digit_classify` is provided to classify a **single 3D trajectory**.
The function applies the same preprocessing steps used during training and outputs the predicted digit label.

---

## Project Context

This project was developed as part of the course  
**Pattern Recognition and Machine Learning**  
LUT University – Lappeenranta, Finland

---

## Authors

- Alessia Tani  
- Sara Zambetti  
- Noah Heuser

