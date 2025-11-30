---
layout: post
title: "Deep Learning — MOAT + Adaptive Ensembling Project"
date: 2022-12-01
categories: [ML_DL]
---

> **Note**: This post summarizes the final team project for the course **Deep Learning: Statistical Perspective** at Seoul National University (Fall 2022).


## 📝 Project Summary

This project proposes an **efficient adaptive ensembling model using Tiny-MOAT**, a lightweight version of the MOAT architecture that combines MBConv blocks with Transformer self-attention.  
The goal is to achieve strong classification accuracy while keeping computational cost low.

We adopt the **Efficient Adaptive Ensembling** framework:  
- Split the training data into two disjoint subsets.  
- Overfit two Tiny-MOAT models separately using pretrained MOAT ImageNet weights.  
- Remove the final fully connected layers to obtain two feature extractors.  
- Train a **single-layer combination module** on the merged training data while freezing both extractors.

Experiments on **Oxford-IIIT Pet, CIFAR-10, and Flowers** show that the proposed Tiny-MOAT ensemble:  
- Uses **dramatically fewer parameters and FLOPs** than SOTA models,  
- Improves accuracy over a single Tiny-MOAT,  
- Avoids EfficientNet-based ensemble limitations (e.g., resolution constraints, overfitting on small images).

Although accuracy is slightly below SOTA and Efficient Adaptive Ensembling, the method offers an effective balance of **efficiency and performance**, making it suitable for low-resource environments.

---

## 🔗 Project Repository

The project was developed as part of the official course GitHub organization:

👉 **[Deep Learning SNU GitHub Organization](https://github.com/Deep-learning-snu/main)**

---

## 📄 Presentation PDF

You can download the final presentation slides used during the project presentation:

👉 **[Download:  _DL_project_2022_MOAT_Ensembling.pdf_](/assets/pdf/DL_project_2022_MOAT_Ensembling.pdf)**






---
