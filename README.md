# 🌌 Galaxy Morphology Classification: CNN vs. Random Forest

## 📜 Project Overview
[cite_start]In this project, I developed and compared two machine learning models to classify the morphology of galaxies using the **Galaxy Zoo 2** dataset[cite: 10]. [cite_start]The goal was to evaluate which algorithm works best for classifying deep-space imagery into three distinct categories based on the Hubble sequence[cite: 17, 18]:

- [cite_start]**Ellipticals:** Rounded/oval shapes with no disk structure[cite: 19].
- [cite_start]**Spirals:** Disks with spiral arms (the most common class)[cite: 20].
- [cite_start]**Irregulars:** Galaxies with no defined shape[cite: 21].

## 💾 Dataset & Preprocessing
- [cite_start]**Source:** Galaxy Zoo 2 (Kaggle)[cite: 30].
- [cite_start]**Data Volume:** The original dataset contained approximately 240,000 images[cite: 31].
- [cite_start]**Processing:** Images were resized to **64x64 pixels** for efficiency and normalized to a range of `[-1, 1]`[cite: 51, 52].
- **Handling Imbalance:**
  - [cite_start]I used *under-sampling* for Spiral and Elliptical galaxies to equalize them (97,670 images each) to prevent model bias[cite: 39].
  - [cite_start]I kept all available **Irregular** galaxies (595 images) as they are rare in the dataset[cite: 45].

---

## 🧠 Models Implemented

I compared a Deep Learning approach against a classical Machine Learning baseline to test their efficiency.

### 1. Convolutional Neural Network (CNN)
- [cite_start]**Framework:** PyTorch[cite: 52].
- [cite_start]**Architecture:** A custom model with 2 convolutional blocks (32 & 64 filters) followed by a fully connected classifier[cite: 63, 66].
- [cite_start]**Optimization:** Trained with Adam optimizer (LR=0.001) and Cross-Entropy Loss[cite: 70, 71].

### 2. Random Forest (RF)
- [cite_start]**Framework:** Scikit-Learn[cite: 80].
- **Method:** Used as a baseline. [cite_start]Images were **flattened** into 1D vectors (12,288 elements) to analyze pixel intensity without spatial context[cite: 77, 78].
- [cite_start]**Configuration:** 100 decision tree estimators[cite: 80].

---

## 📊 Results

[cite_start]The CNN proved to be the superior model for this task, achieving higher accuracy and better generalization[cite: 11].

| Metric | CNN (Deep Learning) | Random Forest (Classic) |
| :--- | :--- | :--- |
| **Accuracy** | [cite_start]**~83%** [cite: 11] | [cite_start]~77% [cite: 11] |
| **F1-Score (Elliptical)** | [cite_start]0.84 [cite: 13] | [cite_start]0.77 [cite: 135] |
| **F1-Score (Spiral)** | [cite_start]0.82 [cite: 13] | [cite_start]0.77 [cite: 135] |
| **F1-Score (Irregular)** | [cite_start]0.12 [cite: 12] | [cite_start]0.12 [cite: 136] |

**Key Findings:**
- [cite_start]The **CNN** significantly outperformed the Random Forest, especially in distinguishing the two main classes (Spirals and Ellipticals)[cite: 13].
- [cite_start]Both models struggled with **Irregular** galaxies in the main test due to the extreme data imbalance (only 595 images vs ~97k others)[cite: 12].
- [cite_start]*Experiment:* When tested on a smaller, fully balanced dataset, the CNN's ability to identify Irregular galaxies jumped to an F1-score of **0.85**, proving the model architecture is robust[cite: 305].

---

## 🛠️ Tech Stack
- **Python 3**
- **PyTorch** (CNN Implementation)
- **Scikit-Learn** (Random Forest & Metrics)
- **Pandas & NumPy**

## 🤝 Contact
You can check the code in this repository and use it for your own projects. If you have any doubts, feel free to contact me.
