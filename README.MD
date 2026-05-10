# GEAD: Explainable Deep Learning-Based Anomaly Detection for Network Security

## Overview

This project implements and analyzes the GEAD (Generating Explainable Anomaly Detection) framework for explainable network intrusion detection using deep learning and regression-tree based explainability.

Traditional Intrusion Detection Systems (IDS) mainly rely on signature-based detection methods, which struggle to detect unknown or zero-day attacks. Deep learning models improve detection performance but usually behave as black-box systems that cannot clearly explain why network traffic is classified as malicious.

GEAD addresses this problem by combining:
- Deep anomaly detection
- Explainable AI (XAI)
- Rule-based interpretation

The framework generates interpretable security rules from deep anomaly detection models, helping analysts understand anomaly decisions more clearly.

---

# Objectives

The objectives of this implementation are:

- Train an autoencoder-based anomaly detection model
- Detect malicious traffic using reconstruction error
- Generate explainable regression-tree based rules
- Identify low-confidence regions in anomaly predictions
- Generate fine-grained interpretable security rules
- Analyze explainability and anomaly detection performance
- Reproduce the GEAD framework in a modern cloud-based environment

---

# Dataset Used

## CICIDS2017 Dataset

The project uses the CICIDS2017 intrusion detection dataset.

The Tuesday traffic subset was used for training and evaluation.

The dataset includes:
- Benign traffic
- DoS attacks
- Brute-force attacks
- Web attacks
- Botnet traffic

Features include:
- Flow duration
- Packet statistics
- Bytes per second
- Header information
- Connection statistics

These features help distinguish between normal and malicious network behavior.

---

# Technologies Used

- Python 3.12
- PyTorch
- Scikit-learn
- NumPy
- Pandas
- Matplotlib
- Google Colab

---

# How GEAD Works

The implemented pipeline follows these stages:

```text
Network Traffic Dataset
↓
Feature Extraction
↓
Data Preprocessing
↓
Feature Normalization
↓
Train / Validation / Test Split
↓
Autoencoder Training
↓
Reconstruction Error Computation
↓
Anomaly Detection
↓
Root Regression Tree Generation
↓
Low-confidence Leaf Detection
↓
Data Augmentation
↓
Fine-grained Subtree Generation
↓
Interpretable Security Rules

# Autoencoder-based Anomaly Detection (GEAD)

This repository contains the implementation and analysis of the **GEAD (Generative Explainable Anomaly Detection)** framework for explainable anomaly detection in network security.

The core anomaly detection is powered by an autoencoder trained exclusively on benign traffic. The model learns normal traffic behavior and reconstructs normal inputs efficiently. For malicious traffic, the reconstruction quality decreases, and the reconstruction error increases.

## Reconstruction Error

Anomaly detection is based on the reconstruction error:

```text
Reconstruction Error = |X − X̂|

Where:
X = original input
X̂ = reconstructed output

```

*If the reconstruction error exceeds a predefined threshold, the traffic is classified as anomalous.*

---

## Explainability in GEAD

GEAD improves the explainability of the black-box neural network using:

* **Regression Trees**
* **Low-confidence Leaf Analysis**
* **Fine-grained Local Subtrees**

The regression tree approximates the neural network's behavior and generates interpretable `IF-THEN` rules.

**Example Rule:**

```text
IF flow_duration > threshold
AND bytes/sec < threshold
THEN anomaly

```

Low-confidence regions from the global tree are further refined using **synthetic data augmentation** and **local subtree generation**. This improves the fidelity between the explainable surrogate model and the underlying neural anomaly detector.

---

## Experimental Results

### Autoencoder Performance

* **ROC-AUC Score:** ≈ 0.75
* **TPR (True Positive Rate):** ≈ 0.997

*The model successfully generated anomaly scores capable of separating normal and malicious traffic.*

### Explainability Results

The framework successfully generated:

* **41** regression-tree leaf nodes
* **12** (Maximum tree depth)
* **24** low-confidence leaves
* **47** interpretable local security rules

### Data Augmentation Results

* **Augmented explainability samples:** Increased from `22,611` to `201,430` samples.
* *Impact:* Significantly improved local explainability and rule generation quality.

---

## Visualizations Generated

The following visualizations were generated to help analyze anomaly detection performance, explainability quality, and decision boundary behavior:

* ROC Curve
* Reconstruction Error Distribution
* Regression Tree Statistics
* Low-confidence Leaf Analysis
* Root Regression Tree Visualization

---

## Practical Adaptation & Additional Work

The original GEAD implementation was developed using older Python and `scikit-learn` versions. During reproduction in a modern **Python 3.12** environment, several compatibility issues were encountered due to NumPy 2.x updates, Pandas API changes, and internal changes to sklearn's tree structure.

**Additional Practical Work Performed:**

* Adapted implementation for Python 3.12 compatibility.
* Fixed deprecated NumPy and Pandas APIs.
* Added ROC and reconstruction-error visualizations.
* Added regression-tree analysis and explainability visualizations.
* Performed compatibility patching and environment adjustments.
* Successfully reproduced major explainability stages in Google Colab.

### Challenges Faced

Compatibility challenges included:

* Deprecated NumPy attributes.
* Pandas compatibility issues.
* `sklearn` tree serialization incompatibilities.

*Note: The final merged-tree reconstruction stage encountered compatibility limitations with modern sklearn internals. However, the major explainability stages of GEAD were successfully reproduced (anomaly detection, regression-tree generation, low-confidence leaf analysis, data augmentation, and fine-grained rule generation).*

---

## Repository Structure

```text
GEAD-Implementation-1598/
│
├── README.MD
├── Description.md
├── GEAD Report.pdf
├── GEAD PPT.pdf
├── Original Research Paper.pdf
├── demo.ipynb
├── GEAD Implementation 1598.zip
└── .gitignore

```

### Files Included

* **GEAD Report.pdf:** Complete project report including methodology, results, visualizations, and analysis.
* **GEAD PPT.pdf:** Project presentation slides.
* **demo.ipynb:** Main implementation notebook containing preprocessing, anomaly detection, explainability stages, and visualizations.
* **Original Research Paper.pdf:** Original GEAD research paper used for implementation reference.
* **GEAD Implementation 1598.zip:** Source code and implementation files.

---

## References

1. GEAD Research Paper
2. CICIDS2017 Dataset Documentation
3. PyTorch Official Documentation
4. Scikit-learn Official Documentation
5. NumPy Documentation
6. Pandas Documentation
7. Explainable AI Research Papers
8. Autoencoder-based Intrusion Detection Research Papers

---

## Conclusion

This project successfully implemented and analyzed the GEAD framework for explainable anomaly detection in network security. The implementation demonstrates how explainable AI can improve trust and interpretability in deep learning-based intrusion detection systems while maintaining strong anomaly detection capabilities.

```

```
