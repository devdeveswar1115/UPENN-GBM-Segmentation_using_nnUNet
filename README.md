# UPENN-GBM-Segmentation_using_nnUNet
This project focuses on segmenting key tumor subregions in glioblastoma patients using the **3D full-resolution nnU-Net** framework. Accurate tumor delineation enables improved diagnostic workflows and facilitates downstream tasks such as pseudoprogression vs true progression classification.

---

## 🏗️ Pipeline Overview

### ✅ Preprocessing

The preprocessing-Net employs a standardized pipeline, comprising:

- **Resampling**: All scans resampled to isotropic voxel spacing (dataset-specific).
- **Cropping**: Non-brain regions cropped using brain masks to optimize memory usage.
- **Normalization**: Z-score normalization applied independently to each MRI modality.
- **Label Encoding**: One-hot encoding for segmentation labels to support multi-class learning (e.g., edema, enhancing tumor, necrosis).

---

## 🧪 Training & Inference

- **Cross-validation**: 5-fold cross-validation.
- **Epochs**: 100 per fold.
- **Data split**: 147 annotated glioblastoma cases split into:
  - 80% Training
  - 20% Validation (per fold)
- **Model**: 3D full-resolution nnU-Net.
- **Inference**: Model applied to remaining pseudoprogression (PsP) and true progression (TP) patients.

---

## 📊 Evaluation Metrics

Two primary metrics were used to evaluate segmentation quality:

1. **Dice Similarity Coefficient (DSC)**  
   Measures the overlap between ground truth mask `G` and predicted mask `P`:  

2. **95% Hausdorff Distance (HD95)**  
   Captures the spatial dissimilarity between segmentation boundaries
---

## 📋 Results

| **Metric**     | **Whole Tumor (WT)** | **Tumor Core (TC)** | **Edema (ED)** | **Enhancing Tumor (ET)** |
|----------------|----------------------|----------------------|----------------|---------------------------|
| DSC            | 0.9375               | 0.6447               | 0.8748         | 0.8456                    |
| Sensitivity    | 0.9481               | 0.5019               | 0.8759         | 0.9717                    |
| HD95 (mm)      | 2.4495               | 6.1603               | 2.2361         | 2.0000                    |

---

## 📷 Segmentation Output
![image](https://github.com/devdeveswar1115/UPENN-GBM-Segmentation_using_nnUNet/blob/fd117db1789c6748f17228a47a10a63ad58ac3a2/output.png)
---

## 🔧 Requirements

```bash
pip install nnunet torch nibabel matplotlib numpy scikit-learn
```

---

## 📬 Contact

For queries or collaboration:  
📧 devdeveswarrana@gmail.com
