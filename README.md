# 📊 Smart Data Sampling and Augmentation for Efficient Experimental Design

## 🔍 Overview

This project presents a multi-strategy approach to tackle the challenge of limited labeled data in experimental domains (e.g., bioengineering, chemistry, or material science), focusing on improving model accuracy and resource efficiency. The pipeline includes:

- **Method 1**: Bayesian Optimization-Based Sampling  
- **Method 2**: Model-Based Distribution Learning using VAEs / GANs  
- **Method 3**: Non-Training Oversampling using Classical Techniques (e.g., GSMOTENC, CSBBoost)

Each method is tailored to specific scenarios based on compute availability, data imbalance, or experimental constraints.

---

## 🧠 Method 1: Bayesian Optimization-Based Sampling

- **Goal**: Use acquisition functions (e.g., UCB, EI) to explore high-potential `x` points.
- **Use Case**: When experiments are cheap or model predictions are reliable.
- **Key Tools**: `scikit-optimize`, `GPyOpt`, Gaussian Processes.
- **Strategy**: Select points either by maximizing the acquisition function or within a confidence interval around the mean (controlled exploration).

📄 *Workflow and pseudocode included in the PDF document — follow the link inside the PDF to view full method details.*

---

## 🔄 Method 2: Model-Based Distribution Learning

- **Goal**: Train a generative model to learn the data distribution and optimize in the latent space.
- **Options**:
  - If stable training is feasible: **Use GANs**
  - If GANs are unstable: **Use VAEs** (more robust, less sharp but structurally valid)
- **Use Case**: Ideal when experimentation is expensive.
- **Implementation Highlights**:
  - Fine-tune the latent space using Bayesian optimization.
  - Use decoder to reconstruct high-potential samples.

📄 *Refer to the PDF for linked pseudocode and architectural workflow.*

---

## ⚖️ Method 3: Non-Training Oversampling Techniques

- **Goal**: Handle skewed label distributions without needing generative model training.
- **Primary Techniques**:
  - **GSMOTENC**: A categorical-aware variant of SMOTE using nonlinear extrapolation.
  - **CSBBoost**: A clustering + ensemble boosting method shown to outperform 8 SOTA methods (published in *Nature*).
- **Key Advantages**:
  - Lightweight and scalable.
  - Avoids overfitting via intelligent synthetic sample generation.

📄 *Full pseudocode and flowchart are embedded in the PDF — links will redirect to the exact steps.*

---


