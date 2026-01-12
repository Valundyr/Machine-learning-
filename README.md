# 🌌 Galaxy Morphology Classification: CNN vs. Random Forest

## 📜 Project Overview
In this project, I developed and compared two machine learning models to classify the morphology of galaxies using the **Galaxy Zoo 2** dataset. The goal was to evaluate which algorithm works best for classifying deep-space imagery into three distinct categories based on the Hubble sequence:

- **Ellipticals:** Rounded/oval shapes with no disk structure.
- **Spirals:** Disks with spiral arms (the most common class).
- **Irregulars:** Galaxies with no defined shape.

## 💾 Dataset & Preprocessing
- **Source:** Galaxy Zoo 2 (Kaggle).
- **Data Volume:** The original dataset contained approximately 240,000 images.
- **Processing:** Images were resized to **64x64 pixels** for efficiency and normalized to a range of `[-1, 1]`.
- **Handling Imbalance:**
  - I used *under-sampling* for Spiral and Elliptical galaxies to equalize them (97,670 images each) to prevent model bias.
  - I kept all available **Irregular** galaxies (595 images) as they are rare in the dataset.

---

## 🧠 Models Implemented

I compared a Deep Learning approach against a classical Machine Learning baseline to test their efficiency.

### 1. Convolutional Neural Network (CNN)
- **Framework:** PyTorch.
- **Architecture:** A custom model with 2 convolutional blocks (32 & 64 filters) followed by a fully connected classifier.
- **Optimization:** Trained with Adam optimizer (LR=0.001) and Cross-Entropy Loss.

### 2. Random Forest (RF)
- **Framework:** Scikit-Learn.
- **Method:** Used as a baseline. Images were **flattened** into 1D vectors (12,288 elements) to analyze pixel intensity without spatial context.
- **Configuration:** 100 decision tree estimators.

---

## 📊 Results
The CNN proved to be the superior model for this task, achieving higher accuracy and better generalization.

| Metric | CNN (Deep Learning) | Random Forest (Classic) |
| :--- | :--- | :--- |
| **Accuracy** | **~83%**  | ~77%  |
| **F1-Score (Elliptical)** |0.84 | 0.77  |
| **F1-Score (Spiral)** | 0.82 | 0.77 |
| **F1-Score (Irregular)** | 0.12 | 0.12 |

**Key Findings:**
- The **CNN** significantly outperformed the Random Forest, especially in distinguishing the two main classes (Spirals and Ellipticals).
- Both models struggled with **Irregular** galaxies in the main test due to the extreme data imbalance (only 595 images vs ~97k others).
- *Experiment:* When tested on a smaller, fully balanced dataset, the CNN's ability to identify Irregular galaxies jumped to an F1-score of **0.85**, proving the model architecture is robust.

---

## 🛠️ Tech Stack
- **Python 3**
- **PyTorch** (CNN Implementation)
- **Scikit-Learn** (Random Forest & Metrics)
- **Pandas & NumPy**

## 🤝 Contact
You can check the code in this repository and use it for your own projects. If you have any doubts, feel free to contact me.
