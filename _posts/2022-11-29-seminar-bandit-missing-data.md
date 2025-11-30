---
layout: post
title: "Seminar in Statistics — Multi-Armed Bandit with Missing Data"
date: 2022-11-29
categories: [Seminar]
---

> **Note**: This post summarizes the project completed in the graduate seminar **“Seminar in Statistics: Missing Data and Online Decision Making”** at Seoul National University (Fall 2022).


# 📝 Project Summary
This project examines how **missing data influences multi-armed bandit (MAB) algorithms** and whether **mean imputation** improves allocation decisions.  
Using binary-reward two-armed bandits under MAR settings, we simulate four algorithms—**Tuned Thompson Sampling, Raw Thompson Sampling, Current Belief, and UCB**—across various missingness patterns.

Key findings:
- **Explorative algorithms** (TTS, RTS, UCB) remain **stable** even with missing outcomes.  
- **Current Belief**, an exploitative method, is **highly sensitive** and performs poorly under missingness.  
- **Mean imputation** strengthens explorative policies but offers limited improvement for exploitative ones.

Overall, explorative bandit strategies combined with simple imputation yield reliable performance even when outcome data are missing.

---

## 🔗 Project Code Repository
👉 **[GitHub: bandit-with-missing](https://github.com/dayeonjung5294/bandit-with-missing)**

---

## 📄 Final Report PDF  

👉 **[Download:  _Seminar_in_Statistics___final_paper.pdf_](/assets/pdf/Seminar_in_Statistics___final_paper.pdf)**


