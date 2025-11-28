# 🍼 Neonatal Disease Analysis Using a Multimodal Deep Learning Framework

This repository contains the complete implementation of our final-year B.Tech project titled:

> **"Neonatal Disease Analysis Using a Multimodal Deep Learning Framework"**

The project focuses on **early prediction of Bronchopulmonary Dysplasia (BPD) and Neonatal Sepsis** by integrating **clinical data, genomic data, and neonatal MRI imaging** using **machine learning and deep learning models**.

---

## 📌 Project Motivation

Neonatal diseases account for nearly **47% of global under-five mortality**. Early diagnosis of:
- **Neonatal Sepsis**
- **Bronchopulmonary Dysplasia (BPD)**  

is extremely difficult due to:
- Non-specific symptoms  
- Noisy MRI scans  
- High-dimensional genomic data  
- Limited availability of multimodal datasets  

This project proposes a **multimodal deep learning framework** that fuses **physiological, molecular, and anatomical data** to improve early diagnosis.

---

## 🎯 Objectives

- Analyze **clinical, genomic, and imaging datasets**
- Apply **modality-specific preprocessing pipelines**
- Train **unimodal models** for each modality
- Develop a **multimodal fusion classifier**
- Perform **MRI denoising using classical and deep learning methods**
- Evaluate models using **AUC, Accuracy, F1-score, PSNR, and SSIM**

---

## 🧠 System Overview

### 🚑 Diseases Studied
- **Bronchopulmonary Dysplasia (BPD)**
- **Neonatal Sepsis**

### 🧬 Modalities Used
| Modality | Data Type | Purpose |
|----------|-----------|---------|
| Clinical | Tabular EHR Data | Disease severity and physiological patterns |
| Genomic | Gene Expression (Microarray) | Early molecular signatures |
| Imaging | Neonatal Lung MRI | Structural lung abnormalities |

---

# ⚙️ Project Methodology

This project employs a multi-modal approach, leveraging genomic, clinical, and imaging data through several parallel and integrated pipelines for prediction and analysis.

---

## 1️⃣ Genomic Data Pipeline

This pipeline focuses on processing high-dimensional genomic data to extract the most relevant features for classification.

* **Data Preprocessing:**
    * **Standardization**
    * **Variance Threshold Filtering**
    * **SelectKBest** (using ANOVA F-score)
* **Dimensionality Reduction:**
    * **PCA** (Principal Component Analysis) / **Autoencoder**
    * **Denoising Autoencoder** (specifically for Bronchopulmonary Dysplasia - BPD prediction)
* **Classification Models:**
    * **Logistic Regression**
    * **SVM** (Linear & RBF kernels)
    * **Random Forest**
    * **XGBoost**
    * **Tabular Transformer**

---

## 2️⃣ Clinical Data Pipeline

This pipeline handles structured clinical data, focusing on robustness and handling data imperfections, such as class imbalance.

* **Data Preprocessing:**
    * **Missing Value Imputation**
    * **Feature Scaling**
    * **Class Imbalance Handling** using **SMOTE** (Synthetic Minority Over-sampling Technique)
* **Classification Models (for Sepsis Prediction):**
    * **Logistic Regression**
    * **Random Forest**
    * **Gradient Boosting**
    * **XGBoost**
    * **SVM**
    * **Stacked Ensemble** (for Clinical Sepsis Prediction)

---

## 3️⃣ Imaging & Radiomics Pipeline

This pipeline extracts quantitative features from medical images, reducing high-dimensional pixel data into informative radiomic features.

* **Image Processing:**
    * **Image Normalization & Resizing**
* **Feature Extraction & Reduction:**
    * **Radiomic Feature Extraction** using **PyRadiomics**
    * **PCA** for dimensionality reduction
* **Classification Models:**
    * **SVM**
    * **Random Forest**
    * **XGBoost**

---

## 4️⃣ MRI Denoising Module

A dedicated module for enhancing image quality prior to feature extraction, ensuring robust radiomic analysis. 

* **Spatial Domain Methods:**
    * **Median Filter**
    * **Gaussian Filter**
    * **Non-Local Means**
* **Transform Domain Methods:**
    * **BM3D** (Block-Matching and 3D filtering)
* **Deep Learning Method:**
    * **CNN-based DnCNN Model** (Denoising Convolutional Neural Network)
* **Evaluation Metrics:**
    * **PSNR** (Peak Signal-to-Noise Ratio)
    * **SSIM** (Structural Similarity Index Measure)

---

## 5️⃣ Multimodal Fusion

This final step combines information from different modalities to achieve a more comprehensive and accurate prediction model.

* **Fusion Strategy:**
    * **Feature-level fusion** of: Clinical features + Imaging features (Specifically for BPD prediction)
    * **Dimensionality Reduction:** **PCA** applied after feature concatenation
* **Final Classifiers:**
    * **SVM**
    * **Random Forest**
    * **XGBoost**
 
---

## ✅ Key Results

### 🔬 BPD Prediction Performance
| Modality | Best Model | Validation AUC |
|----------|------------|----------------|
| Genomic  | Autoencoder + SVM | 0.84–0.85 |
| Clinical | XGBoost | 0.82–0.85 |
| Imaging  | XGBoost | 0.84–0.87 |
| **Fusion (Clinical + Imaging)** | **XGBoost** | **0.92–0.94 ✅** |

---

### 🩺 Sepsis Prediction Performance
| Modality | Best Model | Validation AUC |
|----------|------------|----------------|
| Genomic  | RBF-SVM | 0.94–0.97 |
| Clinical | XGBoost | 0.88–0.90 |

---

### 🖼 MRI Denoising Results
| Method | PSNR | SSIM |
|--------|------|------|
| Noisy Image | 28.63 | 0.59 |
| Median Filter | 32.01 | 0.94 |
| BM3D | 35.08 | 0.90 |
| **DnCNN (CNN-Based)** | **37.42 ✅** | **0.94 ✅** |

---

### 📌 Summary Highlights
- Multimodal **fusion model achieved the best AUC (0.92–0.94)** for BPD prediction.
- **Genomic models performed strongest for Sepsis detection**.
- **CNN-based DnCNN denoising outperformed all classical filters** in PSNR and SSIM.

---

## 🛠️ Installation
```bash
git clone https://github.com/your-username/neonatal-multimodal-ai.git
cd neonatal-multimodal-ai
pip install -r requirements.txt
```
## 📊 Evaluation Metrics

- Accuracy  
- Precision  
- Recall  
- F1-Score  
- ROC–AUC  
- PSNR  
- SSIM  

---

## ⚠️ Limitations

- Small neonatal dataset size  
- Single-center data  
- Genomic batch effects  
- Limited interpretability in fusion models  

---

## 🔮 Future Scope

- Real-time NICU deployment  
- Multicenter prospective validation  
- Explainable AI integration  
- Lightweight model deployment for low-resource hospitals  
- Integration with neonatal bedside monitoring devices  

---

## 👨‍🎓 Authors

- **Shivansh Katiyar**  
- **Kushal Makkar** 
- **Pragyan Sharma** 
---

## 📜 MIT License

MIT License
