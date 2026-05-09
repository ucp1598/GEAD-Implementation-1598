# GEAD: Explainable Deep Learning-Based Anomaly Detection

## Overview
This project reproduces the GEAD framework for explainable network intrusion detection using deep learning and regression-tree based explainability.

## Features
- Autoencoder-based anomaly detection
- Explainable regression-tree generation
- Low-confidence leaf analysis
- Fine-grained interpretable rule generation
- ROC and reconstruction-error visualizations

## Dataset
Dataset used: CICIDS2017 Tuesday traffic subset

## Technologies Used
- Python
- PyTorch
- Scikit-learn
- NumPy
- Pandas
- Google Colab

## Results
- Generated 47 interpretable rules
- Produced regression-tree explainability statistics
- Generated anomaly detection visualizations

## Note
Some compatibility issues were encountered with modern sklearn tree internals in Python 3.12 environments during merged-tree reconstruction.
