# Breast Cancer Ultrasound Segmentation

This project implements a U-Net-based deep learning model for automatic segmentation of breast tumors in ultrasound images. The goal is to assist early detection of breast cancer by accurately identifying tumor regions in medical scans.

---

## Overview

- **Task:** Semantic segmentation of breast tumors in ultrasound images.
- **Approach:** U-Net architecture with data augmentation and regularization.
- **Outcome:** Achieved strong segmentation performance, making the model suitable for real-world medical imaging applications.

---

## Model Highlights

- **Architecture:** Deep U-Net with Dropout layers for regularization.
- **Loss Function:** Combined Binary Crossentropy and Dice Loss for robust segmentation.
- **Data Augmentation:** Mild geometric transformations (rotation, shift, zoom, flip) to improve generalization.
- **Early Stopping:** Prevents overfitting by monitoring validation loss.

---

## Results

| Metric                | Value   |
|-----------------------|---------|
| Validation Accuracy   | ~0.96   |
| Validation Loss       | ~0.40   |
| IoU (Jaccard Score)   | 0.66    |
| Mean IoU              | 0.81    |

> **Note:** Mean IoU above 0.8 is considered strong for medical segmentation tasks.

---


## How to Run

1. Clone the repository.
2. Download the dataset (see below) and update the dataset path in the notebook.
3. Run `breast-cancer-ultrasound-unet-segmentation.ipynb` step by step.

---

## References

- **Dataset:** [Breast Ultrasound Images Dataset on Kaggle](https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset/data)
- **U-Net Paper:** [U-Net: Convolutional Networks for Biomedical Image Segmentation](https://arxiv.org/abs/1505.04597)
