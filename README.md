# Image Blur vs. Sharp Classification  
Using Traditional Neural Networks (MLP)

---

## Student Information
- **Name:** Asala Abdel-Naim Abu Gharaara & Sara Abu Mandil  
- **Major:** Data Science & Artificial Intelligence  
- **University:** University College of Applied Sciences  
- **Course:** Digital Image Processing  

---

## Project Overview

This project focuses on detecting whether an image is **Sharp** or **Blurred** using classical image processing techniques combined with a machine learning classifier.

Instead of relying on computationally expensive Convolutional Neural Networks (CNNs), this work adopts a lightweight and efficient approach based on **handcrafted spatial features** and a **Multi-Layer Perceptron (MLP)** model.

The goal is to demonstrate that carefully engineered features can achieve strong performance in blur detection without deep learning architectures.

---

## Problem Statement

Blur reduces edge clarity and high-frequency details in images, which negatively affects image quality and computer vision systems.

This project addresses a **binary image classification problem**:

- Sharp Images → 0  
- Blurred Images → 1  

---

## Dataset

The dataset used in this project is the **Blur Dataset** from Kaggle.

### Important Note
The dataset was accessed programmatically using Kaggle’s official API (`kagglehub`) directly through Python code.  
It was not downloaded manually.

### Dataset Categories
- `sharp`
- `motion_blurred`
- `defocused_blurred`

### Dataset Details
- Total images: **1050**
- 350 Sharp images
- 350 Motion Blur images
- 350 Defocus Blur images

For binary classification:
- `sharp` → 0  
- `motion_blurred` & `defocused_blurred` → 1  

### Data Split
- 80% Training
- 20% Testing

---

## Preprocessing

- Images loaded directly from Kaggle dataset directory
- Converted to **grayscale**
- No resizing applied (images were already consistent and suitable for feature extraction)
- Feature scaling performed using **StandardScaler**
- The fitted scaler was saved and reused during inference

---

## Feature Extraction

Spatial handcrafted features were extracted to measure edge strength and gradient energy:

- Sobel X Variance (`sobel_x_var`)
- Tenengrad
- Sobel Magnitude Mean (`sobel_mag_mean`)
- Laplacian Variance (removed after feature selection)

### Feature Selection Findings
- Sobel X Variance → Most important
- Tenengrad → Second most important
- Laplacian → Least important (removed in final model)

Blurred images show significantly lower edge-based feature responses compared to sharp images.

---

## Model Architecture

Multi-Layer Perceptron (MLP)

- Input: Feature vector
- Hidden Layer: 50 neurons (ReLU activation)
- Output Layer: 1 neuron (Sigmoid activation)

### Training Details
- Optimizer: Adam
- Loss Function: Binary Cross-Entropy
- Max Iterations: 2000
- Cross-validation applied
- Hidden neurons tested: 10, 20, 50, 100
- Best configuration: 50 neurons

---

## Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-score
- AUC

---

## Results

### Final Performance

- Test Accuracy: **90.95%**
- Cross-Validation Accuracy: **92.19%**
- AUC ≈ **0.95**

### Confusion Matrix

- True Negatives: 57
- True Positives: 134
- False Positives: 13
- False Negatives: 6

The model demonstrates strong performance and stable generalization without overfitting.

---

## Experiments Conducted

- Architecture comparison
- Feature importance analysis
- Feature ablation study
- Cross-validation validation

Feature ablation confirmed that removing Laplacian Variance did not reduce performance.

---

## Model Deployment

- Final trained MLP model saved using **Joblib**
- Selected feature list saved separately
- StandardScaler saved and reused
- Same preprocessing pipeline applied during inference to prevent data leakage

The model is fully prepared for real-world inference.

---

## Web Application

A web-based interface was developed to demonstrate real-time image classification.

### Interface Capabilities

- Users upload external images
- System automatically:
  - Converts image to grayscale
  - Extracts selected features
  - Applies saved StandardScaler
  - Loads trained MLP model
  - Generates prediction

### Output

- Displays classification result: **Sharp / Blurred**
- Shows prediction confidence score

### Live Demo

https://image-blur-sharp-classification-r85.vercel.app/

---

## Conclusion

This project proves that traditional machine learning methods, combined with well-designed handcrafted features, can effectively solve image blur detection problems.

The approach is:

- Computationally efficient
- Lightweight
- Suitable for real-time applications
- Practical for deployment environments where CNNs are impractical

---

## Final Note

This project demonstrates the successful integration of:

- Classical image processing
- Feature engineering
- Neural networks (MLP)
- Model evaluation
- Model deployment
- Web-based real-world inference

It represents a complete end-to-end Data Science pipeline.
