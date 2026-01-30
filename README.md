# Darknet Traffic Classifier 🕵️‍♂️💻

A comparative study of **Deep Learning (1D-CNN)** vs. **Ensemble Learning (Random Forest)** for detecting encrypted network traffic (Tor/VPN) without Deep Packet Inspection.

![Project Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-red)

## 📖 Overview
Traditional network analysis relies on Deep Packet Inspection (DPI) to identify malicious traffic. However, with the rise of encrypted protocols (TLS, Tor), payload inspection is often impossible or unethical. 

This project implements a **privacy-preserving network analyzer** that classifies traffic based solely on **flow metadata** (e.g., packet timing, size, inter-arrival times). It compares a baseline Random Forest model against a custom **1D-Convolutional Neural Network (1D-CNN)** designed to extract latent features from tabular network data.

## 🚀 Key Features
* **Privacy-First:** Uses only statistical flow features; no payload data is accessed.
* **Feature Hashing:** Implements the "Hashing Trick" to handle high-cardinality IP addresses without exploding dimensionality.
* **1D-CNN Architecture:** Treats tabular flow data as a sequential signal to detect local correlations between IP fingerprints and traffic volume.
* **CIC-Darknet2020 Dataset:** Trained on real-world encrypted traffic including Tor, VPN, and benign applications.

## 🧠 Model Architecture

### 1. Baseline: Random Forest
* **Estimators:** 100 Trees
* **Criterion:** Gini Impurity
* **Role:** Acts as the industry standard benchmark for tabular data.

### 2. Proposed: 1D-CNN
A 3-layer Convolutional Neural Network specifically adapted for non-image signal processing.
* **Input:** Hashed IP Vectors + Normalized Flow Stats (1x186 vector).
* **Layers:** 3x Conv1d blocks with Batch Normalization and ReLU.
* **Pooling:** MaxPool1d for dimensionality reduction.
* **Output:** Sigmoid activation (Probability of "Darknet").

## 📂 Dataset
This project utilizes the **CIC-Darknet2020** dataset from the Canadian Institute for Cybersecurity.
* **Classes:** Benign vs. Darknet (Tor/VPN).
* **Samples:** ~141,000 traffic flows.
* **Features:** 85 statistical features per flow.
* **Source:** [Kaggle - CICDarknet2020](https://www.kaggle.com/datasets/peterfriedrich1/cicdarknet2020-internet-traffic/data)

## 📊 Results (Preliminary)
* **Random Forest Accuracy:** *[To be updated]*
* **1D-CNN Accuracy:** *[To be updated]*

## 📚 References
1.  **Dataset:** Lashkari, A. H., et al. "DIDarknet: A Contemporary Approach to Detect and Characterize the Darknet Traffic using Deep Image Learning." (2020).
2.  **Methodology:** Wang, W., et al. "End-to-end encrypted traffic classification with one-dimensional convolution neural networks." (2017).
