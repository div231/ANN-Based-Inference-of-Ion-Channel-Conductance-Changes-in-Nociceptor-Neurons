# ANN-Based-Inference-of-Ion-Channel-Conductance-Changes-in-Nociceptor-Neurons




### 📌 Overview

This project explores a data-driven approach to identifying ion channel conductance changes in pain-sensing neurons (nociceptors) using simulated neuronal action potentials. Inspired by prior work in cardiac electrophysiology, where artificial neural networks (ANNs) were trained to infer modified ion channels from action potential morphology, this project adapts the methodology to neuronal systems relevant to pain signaling.

Unlike cardiac cells, nociceptor neurons exhibit short-duration action potentials and spike-train dynamics. By selectively perturbing ion channel conductances in a Hodgkin–Huxley–based nociceptor model and analyzing action potential differences, we train machine-learning models to infer which ion channel was altered.

---

### 🧠 Methodology

1. **Neuron Modeling**
   A Hodgkin–Huxley–style nociceptor neuron model was implemented using the Brian2 simulator, incorporating multiple pain-relevant ionic currents (sodium, potassium, calcium, leak, and background currents).

2. **Conductance Perturbation**
   Ten ion channel conductances were selectively scaled one at a time, while all others were held constant, analogous to ion channel perturbation studies in cardiac electrophysiology.

3. **Action Potential Difference Encoding**
   For each perturbation:

   * A baseline action potential was simulated
   * A perturbed action potential was simulated
   * The **difference waveform (ΔAP)** was computed as
     [
     \Delta AP(t) = AP_{\text{perturbed}}(t) - AP_{\text{baseline}}(t)
     ]
     This encoding emphasizes channel-specific morphological changes while suppressing shared baseline dynamics.

4. **Dataset Generation**
   The final dataset consists of labeled ΔAP waveforms, with each sample corresponding to a specific ion channel perturbation.

5. **Machine Learning**
   A lightweight artificial neural network (ANN) was trained as a baseline classifier to predict which ion channel conductance was altered based solely on ΔAP features. Early stopping was used to prevent overfitting.

---

### 📊 Exploratory Data Analysis (EDA)

* Random ΔAP waveforms reveal that most channel-specific information is concentrated during early spike dynamics.
* Mean ΔAP plots per ion channel demonstrate distinct temporal signatures, confirming class separability.
* Channels with subtle or overlapping electrophysiological effects show higher confusion in baseline ANN models.

---

### 🤖 Results

* **Task:** 10-class ion channel classification
* **Model:** Feedforward ANN (baseline)
* **Test Accuracy:** ~76%
* Channels with strong electrophysiological influence were classified reliably, while channels with weaker or overlapping effects showed confusion—motivating the use of more advanced temporal models.

---

### 🚀 Future Work

* Convolutional Neural Networks (CNNs) for localized spike-shape learning
* Recurrent Neural Networks (RNNs/LSTMs) for temporal firing-pattern modeling
* Feature windowing focused on early spike dynamics
* Validation using real electrophysiological recordings and pharmacological channel blockers

---

### 🛠 Tech Stack

* **Simulation:** Brian2
* **Data Processing:** NumPy, Pandas
* **Machine Learning:** TensorFlow / Keras
* **Visualization:** Matplotlib, Seaborn

---

### 🎯 Key Takeaway

This project demonstrates that ion channel conductance changes in pain neurons can be inferred directly from action potential morphology using data-driven methods, opening pathways for computational pain phenotyping and neuroscience-inspired machine learning.

---


