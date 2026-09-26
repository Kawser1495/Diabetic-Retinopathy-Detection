# Diabetic-Retinopathy-Detection
Deep learning-based diabetic retinopathy severity classification using retinal fundus images, featuring a DenseNet121-based model, image augmentation, MixUp, ordinal-style labeling, and evaluation with Quadratic Weighted Kappa (QWK).



# Diabetic Retinopathy Detection

A deep learning-based medical image classification project for detecting and classifying diabetic retinopathy severity from retinal fundus images.

## Overview

Diabetic retinopathy (DR) is an eye condition associated with diabetes that can progress through different severity levels. This project develops a machine learning and deep learning pipeline to classify retinal fundus images into five diabetic retinopathy severity classes.

The project explores both a DenseNet121-based deep learning approach and traditional machine learning methods using handcrafted image features.

> **Note:** This project is intended for machine learning research and educational purposes. It is not a medical diagnostic system.

---

## Classes

The model classifies retinal images into five severity levels:

| Class | Severity |
|------:|----------|
| 0 | No Diabetic Retinopathy |
| 1 | Mild |
| 2 | Moderate |
| 3 | Severe |
| 4 | Proliferative |

---

## Dataset

The project uses labeled retinal fundus images for training and evaluation.

- **Training images:** 3,662
- **Test images:** 1,928
- **Number of classes:** 5
- **Image size for deep learning:** 224 × 224 × 3
- The dataset contains a noticeable class imbalance, with fewer samples in some severity categories.

---

## Methodology

The overall workflow is:

```text
Retinal Fundus Images
        ↓
Image Preprocessing
        ↓
Data Augmentation
        ↓
MixUp Augmentation
        ↓
DenseNet121-based Model
        ↓
Severity Classification
        ↓
QWK & Confusion Matrix Evaluation
