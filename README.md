# 🧠 Deep Learning Project – Garbage Classification

This project was developed as part of the **Deep Learning for AI** course.  
It explores how **Convolutional Neural Networks (CNNs)** can be used for **image recognition and classification** on environmental datasets.

---

## ♻️ 1. Garbage Classification

### 📦 The Dataset
The dataset ([Garbage Classification](https://www.kaggle.com/asdasdasasdas/garbage-classification)) contains **15,527 images** divided into **12 categories** of household waste:
`paper`, `cardboard`, `biological`, `metal`, `plastic`, `green-glass`, `brown-glass`, `white-glass`, `clothes`, `shoes`, `battery`, `trash`.

- **Training set:** 420 images per class (≈70%)  
- **Validation/Test set:** 90 images per class (≈15%)  
- **Resized images:** 224×224 pixels  

---

### 🧩 Model
Architecture used: **AlexNet**  
- 5 convolutional layers  
- 3 max pooling layers  
- 2 fully connected hidden layers (4096 neurons each)  
- 1 fully connected output layer (1000 neurons)  

**Input:** RGB images of size 224×224×3.

---

### 📊 Results
- Initial accuracy: ~16.7%  
- Accuracy after 10 epochs: **≈60%**  
- Early stopping applied at epoch 10 to avoid **overfitting**.  
- Best classification performance achieved for **Green-glass** (85/90 correct).  
- **Plastic** was the most challenging category.  

**Confusion matrix analysis** showed generally correct class assignments, with varying precision between categories.

---

## 🔥 2. Fire Detection with Image Recognition

### 📦 Dataset
Two classes:  
- **Fire Images (755)**  
- **Non-Fire Images (244)**  

- **Balanced training set:** 60 images per class  
- **Validation/Test:** 92 images per class  
- **Resized to 224×224 pixels**

**Data augmentation:**  
`RandomHorizontalFlip`, `ColorJitter`, and `Normalization` applied to improve generalization.

---

### 🧩 Model and Results
Architecture: **AlexNet**  
- Accuracy stabilized around **75–76%** after training.  
- Validation and training loss decreased consistently.  
- Some overfitting signs detected but mitigated through early stopping.

**Confusion Matrix Analysis:**  
- **Non-Fire class:** Precision 0.68, Recall 1.00  
- **Fire class:** Precision 1.00, Recall 0.52  

---

## 🧠 Conclusions

| Dataset | Final Accuracy | Key Notes |
|----------|----------------|-----------|
| Garbage | ~60% | Overfitting controlled via early stopping. Plastic class remains challenging. |
| Fire | ~76% | Stronger generalization thanks to data augmentation, but fire detection precision still limited. |

**Takeaways:**
- Deep learning can effectively classify complex visual data even with limited training size.  
- Regularization and augmentation are essential to avoid overfitting.  
- Further improvements could be achieved with transfer learning (e.g., ResNet, EfficientNet).

---

### 🚀 How to run
You can open and execute the notebook directly in Google Colab:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/fabianapagliuca/Deep-Learning/blob/main/Garbage_Classification.ipynb)
