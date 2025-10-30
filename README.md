# 🧩 Implementation of the Paper: *T-SMOTE – Temporal Synthetic Minority Oversampling Technique for Time-Series Classification*

This notebook is a **hands-on, educational implementation** of the paper:

> **Yuxin Luo, Yichao Shen, Jiajie Li, and Liang He (2022)**  
> *T-SMOTE: A Temporal Synthetic Minority Oversampling Technique for Time-Series Classification.*  
> *Proceedings of the Thirty-First International Joint Conference on Artificial Intelligence (IJCAI-22).*

---

## 🎯 Purpose

Traditional oversampling algorithms like **SMOTE** work well for static tabular data — but **fail on time-series** because they ignore the sequential order of events.  
T-SMOTE bridges this gap by generating *time-aware synthetic samples* that respect the **temporal continuity** of signals.

In this notebook, we:

1. **Reproduce the core ideas of the paper** using clear Python code and dummy time-series data.  
2. **Visualize every step** — from sliding window extraction, model confidence calculation, spy-based thresholding, to synthetic temporal interpolation.  
3. Show how T-SMOTE can help balance **rare events** (like anomalies, failures, or diseases) without breaking time dependencies.

---

## 🧠 What You’ll Learn

- How **leading-time subsequences** are generated from each positive sequence.  
- How a **spy-based threshold** helps decide where the positive–negative boundary lies.  
- How **temporal neighbors** (adjacent subsequences) are used instead of random KNNs.  
- How the **Beta distribution** governs the interpolation weight between windows.  
- How to **reconstruct a full synthetic sequence** of the same length as the original.

---

## ⚙️ Notebook Flow

1. **Create Dummy Data:** Build synthetic positive/negative time-series samples.  
2. **Spy-Based Classification:** Train a logistic model to learn border behavior.  
3. **Leading-Time Windows:** Generate subsequences across temporal shifts.  
4. **Compute Scores:** Evaluate model confidence per window.  
5. **Determine Max Leading Time (L):** Stop when confidence drops below spy threshold.  
6. **Temporal Interpolation:** Blend adjacent windows using Beta-weighted mixing.  
7. **Reconstruction:** Combine overlapping synthetic windows into full sequences.  
8. **Visualization:** Plot both original and synthetic time-series.

---

## 📊 Applications

T-SMOTE is especially powerful for:
- Predictive maintenance (sensor data before machine failure)  
- Biomedical signals (ECG, EEG, gait analysis)  
- Anomaly detection in IoT or finance  
- Human activity or gesture recognition  
- Any temporal domain with class imbalance

---

## 🧩 Key Formulae

1. **Subsequence extraction:**
   \[
   X_i^l = [x_{T-l-w+1}, ..., x_{T-l}]
   \]
2. **Temporal interpolation:**
   \[
   X_{\text{new}} = α·X_i^l + (1−α)·X_i^{l+1}, \quad α ∼ \text{Beta}(s_i^l, s_i^{l+1})
   \]
3. **Synthetic confidence:**
   \[
   s_{\text{new}} = α·s_i^l + (1−α)·s_i^{l+1}
   \]
4. **Weighted sampling:**
   \[
   w = \max(0, s_{\text{new}} − h)
   \]

---

## 🪶 Author

**Prashanna Raj Pandit**  
M.S. Computer Science, Southern Illinois University Edwardsville  
Focus: Time-Series Modeling, Gait Analysis, AI for Sequential Data

---

> ⭐ *This notebook is not just code — it’s a visualization of an idea:  
> that synthetic data should understand time, not just copy it.*

