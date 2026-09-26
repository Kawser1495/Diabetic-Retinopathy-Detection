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


🧠 Deep Learning Approach

The main classification model is based on DenseNet121.

Preprocessing
Resize images to 224 × 224
Prepare images for CNN-based classification
Apply image augmentation
Horizontal flipping
Vertical flipping
Zoom augmentation
MixUp augmentation
Model Architecture

The model uses a DenseNet121-based feature extractor followed by:

DenseNet121
     ↓
Global Average Pooling
     ↓
Dropout (0.5)
     ↓
Dense Layer (5 outputs)

The classification layer uses ordinal-style label encoding to represent the ordered nature of diabetic retinopathy severity.

Training Configuration
Optimizer: Adam
Learning rate: 5e-5
Loss: Binary Cross-Entropy
Batch size: 32
Training epochs: 15
MixUp: α = 0.2
📈 Evaluation

Because diabetic retinopathy severity is ordinal, the project uses Quadratic Weighted Kappa (QWK) as an important evaluation metric.

Best Validation Result

Quadratic Weighted Kappa (QWK)
0.9182

confusion matrix was also used to examine class-level prediction behavior.

Why QWK?

Accuracy treats every wrong prediction equally. However, predicting a neighboring severity level is different from predicting a very distant severity level.

For example:

Actual:     Moderate
Predicted:  Mild

is different from:

Actual:     Moderate
Predicted:  Proliferative

🤖 Traditional Machine Learning

A second pipeline was developed using handcrafted image features and classical machine learning algorithms.

Feature Extraction

The following features were explored:

HOG — Histogram of Oriented Gradients
LBP — Local Binary Patterns
GLCM — Gray-Level Co-occurrence Matrix
RGB Color Histograms
Image denoising
Grayscale conversion
Histogram equalization
Dimensionality Reduction

Principal Component Analysis (PCA) was used to reduce feature dimensionality before classification.

Classification Models

The following algorithms were evaluated:

| Model         | Purpose                     |
| ------------- | --------------------------- |
| Random Forest | Classical ensemble baseline |
| SVM           | Margin-based classification |
| XGBoost       | Gradient boosting           |
| CatBoost      | Gradient boosting           |

This provides a comparison between handcrafted-feature-based machine learning and the DenseNet121-based deep learning approach.

📊 Classical ML Results

The experiments produced the following approximate results:

| Model         | Accuracy | Macro F1 |
| ------------- | -------: | -------: |
| Random Forest |      73% |     0.40 |
| SVM           |      70% |     0.35 |
| XGBoost       |      71% |     0.42 |
| CatBoost      |      72% |     0.42 |


🛠️ Technologies
Programming
Python
Deep Learning
TensorFlow
Keras
DenseNet121
Machine Learning
Scikit-learn
Random Forest
SVM
XGBoost
CatBoost
Image Processing
OpenCV
HOG
LBP
GLCM
Data Analysis
NumPy
Pandas
Visualization
Matplotlib
Seaborn
Development
Jupyter Notebook
Google Colab

📁 Project Structure
Diabetic-Retinopathy-Detection/
│
├── dr-classification-kawser-and-tanvir.ipynb
├── Workspace.ipynb
├── README.md
└── ...

