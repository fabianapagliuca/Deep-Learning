# 🧠 Deep Learning Project – Garbage Classification

This project was developed as part of the **Deep Learning for AI** course.  
It explores how **Convolutional Neural Networks (CNNs)** can classify environmental waste images.

---

## ♻️ 1. Garbage Classification

### 📦 Dataset
The dataset ([Garbage Classification – Kaggle](https://www.kaggle.com/asdasdasasdas/garbage-classification)) includes **15,527 images** divided into **12 categories**:

`paper`, `cardboard`, `biological`, `metal`, `plastic`,  
`green-glass`, `brown-glass`, `white-glass`, `clothes`,  
`shoes`, `battery`, `trash`.

To handle imbalance, the dataset was **rebalanced** through downsampling:  
→ **600 images per class** were selected and organized into:

- **Training set:** 420 images/class (≈70%)  
- **Validation set:** 90 images/class (≈15%)  
- **Test set:** 90 images/class (≈15%)

All images were resized to **224×224 pixels**.

---

### 🧩 Data Augmentation
Applied transformations to improve model generalization:

- `RandomHorizontalFlip(p=1)`  
- `RandomResizedCrop((224,224), scale=(0.1,0.7))`  
- `RandomRotation(45°)`  
- `ColorJitter(brightness=0.25)`  
- `RandomAdjustSharpness(sharpness_factor=2)`

Augmentation was applied 4× to the training set before merging with the original images.

---

## 🏗️ Architectures

### 🔹 AlexNet
- 5 convolutional layers (ReLU activations)  
- 3 max pooling layers  
- 2 fully connected layers (4096 neurons each)  
- 1 output layer (12 neurons)  
- Dropout regularization to reduce overfitting  

**Input:** RGB images (224×224×3)

**Results:**

| Metric | Value |
|--------|--------|
| Training Accuracy | 70.6% |
| Validation Accuracy | 65.6% |
| Test Accuracy | 64.4% |

**Observations:**  
- Model struggled with **metal**, **plastic**, and **shoes** classes.  
- Precision lower for metal; recall lowest for plastic.

---

### 🔹 GoogLeNet
- 7×7 Conv + BatchNorm + MaxPool  
- 1×1 and 3×3 Conv layers  
- 9 **Inception blocks**  
- Dropout + Dense Layer + LogSoftmax  

**Results:**

| Metric | Value |
|--------|--------|
| Training Accuracy | 76.7% |
| Validation Accuracy | 73.6% |
| Test Accuracy | 72.8% |

**Observations:**  
- Improved generalization and accuracy compared to AlexNet.  
- Most errors involved confusion between *metal*, *paper*, and *white-glass*.  
- *Green-glass* achieved precision of 79%, while *shoes* remained the hardest (precision 51%).

---

## 🧠 Final Comparison

| Model | Test Accuracy | Notes |
|--------|----------------|--------|
| **AlexNet** | 64.4% | Struggled with specific material classes |
| **GoogLeNet** | 72.8% | Better precision and generalization |

**Conclusion:**  
> GoogLeNet outperformed AlexNet across all metrics, thanks to its deeper Inception architecture and improved regularization mechanisms.

---

## 🚀 How to Run
You can open and execute the notebook directly in Google Colab:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/fabianapagliuca/Deep-Learning/blob/main/Garbage_Classification.ipynb)

---
