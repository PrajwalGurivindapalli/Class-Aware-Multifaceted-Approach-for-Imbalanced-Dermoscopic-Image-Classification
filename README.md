# Class-Aware-Multifaceted-Approach-for-Imbalanced-Dermoscopic-Image-Classification
> Class-Aware Multifaceted Approach for Imbalanced Dermoscopic Image Classification. Combines class-specific augmentation, Focal Loss, and ResNet50 with CBAM attention mechanisms to improve melanoma detection on the HAM10000 dataset.

## 🚀 Project Overview
Accurately diagnosing rare skin conditions like Melanoma (mel) is critical for patient survival, yet standard deep learning models frequently fail due to severe class skew (where common benign lesions like Melanocytic nevi heavily outweigh minority malignant classes). 

This thesis introduces a **Class-Aware Multifaceted Approach** operating across three distinct layers:
1. **Data-Level:** Heavy class-specific augmentations applied to minority classes to boost feature heterogeneity.
2. **Algorithmic-Level:** Focal Loss optimization to force the model to prioritize hard-to-classify examples over easy majority instances.
3. **Architectural-Level:** Integration of CBAM (Channel + Spatial attention) across ResNet50 layers to focus strictly on lesion features while filtering out background artifacts (hair, gel bubbles).

---

## 📊 Dataset Characteristics
* **Dataset:** HAM10000 (Human Against Machine with 10,000 training images)[cite: 42].
* **Categories:** 7 diverse skin lesion types (Melanocytic nevi [nv], Melanoma [mel], Benign keratosis-like lesions [bkl], Basal cell carcinoma [bcc], Actinic keratoses [akiec], Vascular lesions [vasc], and Dermatofibroma [df])[cite: 42].
* **Imbalance Distribution:** Highly skewed, with dominant classes representing ~69% of impressions and minority classes dropping to ~1%[cite: 43].
* **Data Partitioning:** Stratified 70% Training, 15% Validation, and 15% Test split to ensure proportional representation across all splits[cite: 43].

---

## 🛠️ Methodology & Architecture
* **Backbone Architecture:** ResNet50 pre-trained on ImageNet with CBAM blocks integrated after Layers 1–4[cite: 44, 45].
* **Loss Function:** Focal Loss ($\gamma = 2.0$) to mitigate majority-class gradient domination[cite: 43].
* **Training Strategy:** Two-phase schedule (5-epoch warmup with frozen backbone followed by 45-epoch fine-tuning with all layers unfrozen)[cite: 44, 45].
* **Interpretability:** Gradient-weighted Class Activation Mapping (Grad-CAM) used to visually validate model reasoning and clinical focus areas[cite: 45].

---

## 📈 Key Results & Performance
* **ResNet50 + CBAM (Proposed):** Achieved a superior **Macro F1-Score of 0.7164** and a **Balanced Accuracy of 0.6976**[cite: 45].
* **Baseline Comparison:** Significantly outperformed the standard EfficientNet-B0 baseline (Macro F1: 0.5242) and vanilla ResNet50 ablation model (Macro F1: 0.5505)[cite: 45].
* **Qualitative Findings:** Grad-CAM heatmaps confirmed that the attention-enhanced architecture successfully localizes true pathological lesion features rather than irrelevant background noise[cite: 48].

---

## 🧰 Tech Stack
* **Language:** Python 3.8[cite: 45]
* **Deep Learning Framework:** PyTorch[cite: 45]
* **Data Augmentation:** Albumentations[cite: 45]
* **Evaluation & Explainability:** Scikit-Learn, Grad-CAM[cite: 45]

---

## ⚙️ Getting Started & Installation

1. Clone the repository:
   ```bash
   git clone [https://github.com/Prajwal-Gurivindapalli/dermoscopic-image-classification.git](https://github.com/Prajwal-Gurivindapalli/dermoscopic-image-classification.git)
   cd dermoscopic-image-classification
