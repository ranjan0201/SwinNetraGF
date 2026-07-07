# SwinNetraGF: A Gated Attention Fusion Transformer for Retinal Disease Classification

<div align="center">

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red.svg)
![Conference](https://img.shields.io/badge/IEEE-SPCOM%202026-orange.svg)

**Official PyTorch implementation of SwinNetraGF**

*A Gated Attention Fusion Transformer for Automated Retinal Disease Classification*

</div>

---

## 📖 Overview

Retinal diseases, particularly **Diabetic Retinopathy (DR)** and **Glaucoma**, are among the leading causes of irreversible blindness worldwide. Although Vision Transformers effectively capture long-range contextual information, efficiently integrating hierarchical multi-scale retinal representations remains a significant challenge. **SwinNetraGF** addresses this limitation through a novel **Adaptive Gated Attention Fusion (GAF)** module that selectively integrates shallow structural information with deep semantic representations extracted by **Swin Transformer V2**, resulting in improved retinal disease classification.

---

## ✨ Highlights

- Hierarchical feature extraction using **Swin Transformer V2**
- Novel **Adaptive Gated Attention Fusion (GAF)** module
- Learnable spatial alignment for multi-scale compatibility
- End-to-end transformer architecture for retinal disease classification
- Robust performance on multi-class retinal disease datasets

---

# 🏗️ Proposed Framework

<div align="center">

<img src="figures/retina_R.png" width="95%" alt="SwinNetraGF"/>

<br>

<sub>
<b>Figure 1.</b>
Overview of the proposed <b>SwinNetraGF</b>.
The framework extracts hierarchical retinal representations using
<b>Swin Transformer V2</b>, aligns shallow features through a learnable
projection module, and adaptively integrates them using the proposed
<b>Gated Attention Fusion (GAF)</b> mechanism before classification.
</sub>

</div>

# 📂 Dataset

### Eye Disease Image Dataset (https://data.mendeley.com/datasets/s9bfhswzjb/1)

| Property | Value |
|-----------|------:|
| Dataset | Eye Disease Image Dataset |
| Source | Mendeley Data |
| Total Images | 3882 |
| Classes | 3 |
| Categories | Healthy, Diabetic Retinopathy, Glaucoma |
| Image Size | 256 × 256 |
| Training | 70% |
| Validation | 15% |
| Testing | 15% |

---

# 🧠 Methodology

The proposed framework consists of four major components:

```
Fundus Image
      │
      ▼
Swin Transformer V2
      │
      ▼
Hierarchical Feature Extraction
      │
      ▼
Spatial Alignment
      │
      ▼
Adaptive Gated Attention Fusion
      │
      ▼
Classification Head
      │
      ▼
Healthy / Glaucoma / DR
```

---

# 🔥 Adaptive Gated Attention Fusion

The proposed fusion module computes

\[
G=\sigma(\mathrm{LN}(T_{deep}W_g))
\]

and fuses hierarchical features as

\[
F_{fused}=T_{deep}+G\odot(\hat{T}_{shallow}W_f)
\]

where

- \(T_{deep}\) denotes deep semantic features
- \(\hat T_{shallow}\) denotes aligned shallow features
- \(G\) is the adaptive gating map
- \(F_{fused}\) is the final fused representation

---

# ⚙️ Training Configuration

| Parameter | Value |
|-----------|------:|
| Backbone | Swin Transformer V2 |
| Optimizer | AdamW |
| Batch Size | 16 |
| Epochs | 40 |
| Scheduler | Cosine Annealing LR |
| Label Smoothing | 0.15 |
| Mixed Precision | ✓ |
| Gradient Clipping | ✓ |

---

# 📊 Experimental Results

| Metric | Score |
|---------|------:|
| Accuracy | **91.42%** |
| Precision | **91.29%** |
| Recall | **91.15%** |
| F1-score | **0.9089** |
| AUC | **0.9844** |

---


# 📚 Citation

TBD

