# Implementation of the Paper — *T-SMOTE: Temporal Synthetic Minority Oversampling Technique for Time-Series Classification*

When I first encountered **T-SMOTE**, it immediately stood out as more than just another oversampling algorithm.  
It addresses one of the most fundamental problems in time-series learning — **how to synthesize new samples that understand time**.

Traditional oversampling techniques like SMOTE treat data points as isolated records.  
But in time-series, **every observation carries temporal context** — the meaning of one timestamp depends on what came before it.  
T-SMOTE introduces *temporal reasoning* into synthetic sample generation, ensuring that the artificial sequences preserve the evolving dynamics of real-world signals.

---

## 📘 Reference Paper

> **Yuxin Luo, Yichao Shen, Jiajie Li, and Liang He (2022)**  
> *T-SMOTE: A Temporal Synthetic Minority Oversampling Technique for Time-Series Classification*  
> In *Proceedings of the Thirty-First International Joint Conference on Artificial Intelligence (IJCAI-22)*.  
> [🔗 Read the paper on IJCAI](https://www.ijcai.org/proceedings/2022/0431.pdf)

---

## 🎯 Purpose of This Notebook

This notebook represents my **hands-on, from-scratch implementation** of the original T-SMOTE framework.  
Rather than reproducing the exact code from the paper, my goal was to deeply **understand the intuition and mathematics** behind each step — and make it *explainable, visual, and reproducible* for other researchers and practitioners.

I wanted to trace every part of the reasoning:
- How *leading time* captures temporal distance from the event boundary,  
- How the **spy-based classifier** defines the decision threshold dynamically,  
- How the **Beta distribution** controls interpolation between subsequences,  
- And how the **weighted sampling strategy** filters out noisy synthetic samples.

This notebook breaks down the T-SMOTE pipeline into concrete, visual steps for learning and experimentation.

---

## 🔬 The Core Intuition

Imagine predicting an upcoming fault in a machine, or a physiological anomaly in medical data.  
We have hundreds of “normal” sequences but only a handful of rare failures — a classic class imbalance problem.

T-SMOTE doesn’t simply duplicate rare events.  
It **creates realistic temporal variations** of those sequences by:

1. **Sliding windows** across each time-series to form overlapping subsequences (controlled by window length *w* and leading time *l*).  
2. **Evaluating model confidence** across different lead times to determine how far from the event boundary each window lies.  
3. **Interpolating** between temporally adjacent windows using the **Beta distribution**, reflecting asymmetric uncertainty between them.  
4. **Assigning weights** to new synthetic samples based on how confidently they lie near the decision boundary.

The outcome is a set of synthetic time-series that are both **statistically balanced** and **temporally consistent**.

---

## 🧩 What This Notebook Demonstrates

1. **Synthetic Data Generation** – Multivariate time-series for positive and negative classes  
2. **Spy-Based Classifier** – Logistic regression trained to estimate temporal border confidence  
3. **Leading-Time Analysis** – Progressive window slicing with increasing *l*  
4. **Temporal Interpolation** – Beta-based generation of synthetic sequences  
5. **Weighted Sampling** – Noise control near class boundaries  
6. **Reconstruction & Visualization** – Rebuilding full-length synthetic sequences and visual comparison  

---

## 💡 Why This Work Matters

Imbalanced time-series appear across domains — predictive maintenance, biomedical monitoring, IoT, and behavioral analytics.  
Yet, most resampling strategies still ignore the sequential nature of the data.

T-SMOTE changes that perspective.  
It proves that synthetic data generation isn’t just about balancing numbers — it’s about **preserving the story of time** within the data itself.

This notebook is not a replication of the paper, but an **interpretation for understanding** — a way to see *why* the method works, not just *how*.

---

## 🧠 Repository Goals

- Make the T-SMOTE process **accessible, interpretable, and visual**  
- Provide a **transparent baseline** for future work in temporal data augmentation  
- Inspire more research into **time-aware synthetic learning**  

---

## 👤 Author

**Prashanna Raj Pandit**  
Graduate Researcher, M.S. Computer Science  
Southern Illinois University Edwardsville  
Focus: Sequential Modeling, Gait Analysis, Temporal AI Systems  

> “Synthetic data shouldn’t just exist — it should remember time.”

---

