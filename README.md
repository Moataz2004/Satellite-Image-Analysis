# Satellite-Image-Analysis

A Deep Learning project for satellite image classification using the **EuroSAT RGB dataset**. This project explores and compares three Transformer-based approaches: **Vision Transformer (ViT), Swin Transformer, and a Hybrid ViT-Swin architecture**.

The main objective is to investigate how different Transformer architectures perform on remote sensing image classification and evaluate whether combining their feature representations can improve classification performance.

---

## Project Overview

Satellite image classification plays an important role in remote sensing applications, including land-use analysis, environmental monitoring, urban planning, and agricultural assessment.

In this project, we developed and evaluated three deep learning models to classify satellite images into 10 different land-use and land-cover categories.

### Implemented Models

- **Vision Transformer (ViT):** Uses self-attention mechanisms to capture global relationships between image patches.
- **Swin Transformer:** Uses shifted-window attention to learn hierarchical visual representations efficiently.
- **Hybrid ViT-Swin:** Combines feature representations from ViT and Swin Transformer into a unified classification framework.

---

## Dataset

We used the **EuroSAT RGB dataset**, a publicly available satellite image dataset containing 27,000 RGB images across 10 land-use and land-cover classes.

| Class | Number of Images |
|---|---:|
| Annual Crop | 3,000 |
| Forest | 3,000 |
| Herbaceous Vegetation | 3,000 |
| Highway | 2,500 |
| Industrial | 2,500 |
| Pasture | 2,000 |
| Permanent Crop | 2,500 |
| Residential | 3,000 |
| River | 2,500 |
| Sea Lake | 3,000 |
| **Total** | **27,000** |

### Dataset Split

The dataset was divided into:

- Training: 70% (18,900 images)
- Validation: 15% (4,050 images)
- Testing: 15% (4,050 images)

---

## Methodology

### 1. Data Preprocessing

The preprocessing pipeline included:

- Resizing images to 64 × 64 pixels.
- Converting images into PyTorch tensors.
- Normalizing images using ImageNet mean and standard deviation.
- Applying data augmentation using random horizontal and vertical flips during training.

### 2. Model Development

Three architectures were implemented and evaluated:

**Vision Transformer (ViT)**

A pretrained Vision Transformer was fine-tuned for the 10-class classification task.

**Swin Transformer**

A pretrained Swin Transformer was used to learn hierarchical image features through shifted-window self-attention.

**Hybrid ViT-Swin**

A hybrid architecture combining feature representations extracted from both ViT and Swin Transformer backbones. The fused features are passed through a classification head to predict the final class.

### 3. Training Strategy

- Optimizer: AdamW
- Loss Function: Cross Entropy Loss
- Learning Rate: 0.0001
- Batch Size: 32
- Epochs: 15
- Weight Decay: Model-dependent
- Learning Rate Scheduler: ReduceLROnPlateau
- Mixed Precision Training: Automatic Mixed Precision (AMP)
- Checkpoint Selection: Best validation accuracy

---

##  Results and Model Comparison

The following table summarizes the test performance of the three implemented models.

| Metric | ViT | Swin Transformer | Hybrid |
|---|---:|---:|---:|
| Accuracy | 97.14% | 98.27% | **98.42%** |
| Macro F1-Score | 97.09% | 98.22% | **98.38%** |
| ROC-AUC (OvR) | 99.92% | — | 99.93% |

**Key Findings:**

- All three architectures achieved strong classification performance.
- Swin Transformer outperformed the standalone ViT model.
- The Hybrid architecture achieved the highest test accuracy and Macro F1-score among the three models.
- Feature fusion provided a promising approach for combining complementary visual representations.

---

## 🖼️ Project Visualizations

### Dataset Samples

<img width="951" height="814" alt="image" src="https://github.com/user-attachments/assets/2ab27e17-b1df-46e8-9992-9223c49c55c9" />


### Model Architecture

<img width="1200" height="965" alt="image" src="https://github.com/user-attachments/assets/de53ff0c-bf03-4f69-ab10-c4981fbc52c4" />
g)

### Training Performance

[![Training and Validation Curves](images/training_curves.png)](https://chatgpt.com/share/6ae88d72-8318-83e9-ab6c-7b5c714d444f)

### Confusion Matrix

<img width="875" height="875" alt="image" src="https://github.com/user-attachments/assets/1f7d51ce-cafe-4e47-8251-3044886639e7" />

---

##  Technologies & Libraries

- Python
- PyTorch
- Torchvision
- TIMM
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab

---

## 📁 Repository Structure

```text
Satellite-Image-Classification/
│
├── notebooks/
│   ├── ViT.ipynb
│   ├── Swin.ipynb
│   └── Hybrid.ipynb
│
├── images/
│   ├── dataset_samples.png
│   ├── hybrid_architecture.png
│   ├── training_curves.png
│   ├── hybrid_confusion_matrix.png
│   └── model_comparison.png
│
├── results/
│   └── model_results.csv
│
├── README.md
└── requirements.txt
```
