#  Image Blur Detection Project

##  Student Information
- **Name:** Asala Abdel-Naim Abu Gharaara  
- **Major:** Data Science & Artificial Intelligence  
- **University:** University College of Applied Sciences 
- **Course:** Digital Image Processing 
---

##  Project Overview
This project focuses on detecting whether an image is **sharp** or **blurred** using
classical image processing techniques combined with a machine learning classifier.

Instead of relying on deep learning models, this project extracts **handcrafted features**
related to image sharpness and uses them to train a classifier that distinguishes between
sharp and blurred images.

---

##  Dataset Source
The dataset used in this project is the **Blur Dataset** from **Kaggle**.

 **Important Note:**  
The dataset was **not downloaded manually**.  
Instead, it was accessed directly using Kaggle’s official API through Python code
(`kagglehub`), and the experiments were performed on the dataset path provided by Kaggle.

Dataset categories:
- `sharp`
- `motion_blurred`
- `defocused_blurred`

 **Dataset Details:**
- Total images: **1050**
- Images per class: **350**
- Labels used for classification:
  - `sharp` → 0  
  - `motion_blurred`, `defocused_blurred` → 1  

---

##  Preprocessing
- Images were loaded directly from the Kaggle dataset directory.
- All images were converted to **grayscale**.
- No resizing was applied since the dataset images were

## Final Notes
This project demonstrates that classical image processing features,
when carefully selected and combined with a machine learning model,
can achieve strong performance in image blur detection tasks without
the need for deep learning. 
