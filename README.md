# 🩺 Diabetic Retinopathy Detection

### Deep Learning-Based Retinal Image Classification

A deep learning project for **five-class diabetic retinopathy severity classification** using retinal fundus images. The project explores a DenseNet121-based deep learning approach alongside traditional machine learning models using handcrafted image features.

> **Disclaimer:** This project is developed for educational and research purposes and should not be used as a medical diagnostic system.

---

## 📌 Project Overview

Diabetic retinopathy is a diabetes-related eye condition that can develop through different stages of severity. Automated analysis of retinal fundus images can help researchers investigate machine learning approaches for severity classification.

This project focuses on building and evaluating machine learning pipelines that classify retinal images into five diabetic retinopathy severity levels.

### Project Highlights

- 🧠 DenseNet121-based deep learning model
- 🖼️ Retinal fundus image classification
- 🔄 Image augmentation and MixUp
- 📊 Quadratic Weighted Kappa (QWK) evaluation
- 🤖 Traditional ML model comparison
- 🔍 HOG, LBP, GLCM and color-based feature extraction
- 📈 Confusion matrix and prediction analysis

---

## 🎯 Classification Classes

The system classifies retinal images into five severity categories:

| Class | Severity |
|:---:|---|
| **0** | No Diabetic Retinopathy |
| **1** | Mild |
| **2** | Moderate |
| **3** | Severe |
| **4** | Proliferative |

---

## 📊 Dataset

The project uses labeled retinal fundus images for training and evaluation.

| Property | Value |
|---|---:|
| Training images | 3,662 |
| Test images | 1,928 |
| Number of classes | 5 |
| Deep learning input size | 224 × 224 × 3 |

The dataset is imbalanced, with substantially fewer samples in some of the more severe categories.

---

# 🔬 Methodology

The project contains two main experimental pipelines.

```text
                  Retinal Fundus Images
                           │
                           ▼
                  Image Preprocessing
                           │
                 ┌─────────┴─────────┐
                 │                   │
                 ▼                   ▼
        Deep Learning Pipeline   Classical ML Pipeline
                 │                   │
                 ▼                   ▼
            DenseNet121        Feature Extraction
                 │                   │
                 │              ┌────┴────┐
                 │              │         │
                 │             HOG       LBP
                 │              │         │
                 │             GLCM   Color Hist.
                 │              │         │
                 │              └────┬────┘
                 │                   ▼
                 │                  PCA
                 │                   │
                 │            ┌──────┼──────┬──────┐
                 │            ▼      ▼      ▼      ▼
                 │            RF     SVM   XGBoost CatBoost
                 │
                 ▼
          Severity Prediction
                 │
                 ▼
        QWK / Confusion Matrix
