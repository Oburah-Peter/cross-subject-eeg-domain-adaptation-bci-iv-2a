# Cross-Subject EEG Motor Imagery Classification with Domain Adaptation

## 🧠 Project Overview

This project explores how well deep learning models can decode motor imagery signals from EEG data when tested on **unseen subjects**, and whether **domain adaptation techniques** can improve generalization.

We use the **BCI Competition IV 2a dataset** and systematically evaluate multiple domain adaptation strategies under a cross-subject setting.

---

## 🎯 Problem Statement

EEG-based Brain-Computer Interfaces (BCIs) suffer from a major limitation:

> Models trained on one subject do not generalize well to another.

This is due to **domain shift**, where EEG signal distributions vary significantly across individuals.

The goal of this project is to:

- Understand how severe this problem is  
- Evaluate different domain adaptation techniques  
- Identify which methods actually improve cross-subject performance  

---

## ⚙️ Approach

We frame this as a **cross-subject classification problem**:

- Train on a set of subjects (**source domain**)  
- Evaluate on unseen subjects (**target domain**)  

### Dataset Setup

- Dataset: **BCI Competition IV 2a**
- Subjects: 9
- EEG Channels: 22
- Classes: 4 motor imagery tasks  
- Input shape: `(Trials, Channels, Time) = (N, 22, 1001)`

---

## 🧪 Experimental Design

### Cross-Subject Split

- **Training (Source):** 6 subjects  
- **Testing (Target):** 3 unseen subjects  

### Baseline Model

We use **EEGNet**, a compact CNN designed for EEG decoding, as our baseline.

---

## 🔬 Domain Adaptation Techniques

We evaluate a wide range of domain adaptation methods, grouped as follows:

### 1. Distribution Alignment
- DeepCORAL
- MMD
- Sinkhorn (Optimal Transport)

### 2. Adversarial Methods
- DANN
- CDAN
- CoDATS

### 3. Representation Learning
- Contrastive Learning
- CLUDA

### 4. Structure-Based Methods
- SASA

### 5. Other Strategies
- Pseudo-labeling
- Raincoat
- SSSS-TSA

---

## 📊 Results

| Method | Accuracy | Macro F1 |
|-------|--------|---------|
| **EEGNet (Baseline)** | **0.3531** | **0.3542** |
| DANN | 0.3542 | 0.3508 |
| SASA | 0.3496 | 0.3492 |
| CDAN | 0.3461 | 0.3451 |
| MMD | 0.3333 | 0.3338 |
| Sinkhorn | 0.3357 | 0.3324 |
| DeepCORAL | 0.3310 | 0.3322 |
| CoDATS | 0.3310 | 0.3305 |
| Contrastive | 0.3298 | 0.3302 |
| CLUDA | 0.3287 | 0.3281 |
| Pseudo-label | 0.3113 | 0.3017 |
| SSSS-TSA | 0.2915 | 0.2870 |
| Raincoat | 0.2811 | 0.2812 |

---

## 📈 Key Observations

- The **baseline EEGNet model achieved the best overall performance**
- Domain adaptation methods did **not consistently improve results**
- Adversarial methods (DANN, CDAN) performed closest to baseline
- Complex methods (SSSS-TSA, Raincoat) showed instability
- Pseudo-labeling failed due to **low confidence on target samples**

---

## 🧠 Interpretation

These results highlight an important insight:

> Domain adaptation is not a guaranteed solution for EEG generalization.

Even advanced techniques can:
- distort useful features  
- introduce instability  
- fail without careful tuning  

Cross-subject EEG classification remains a **challenging open problem**.

---

## 📂 Project Structure

## 🛠️ Tech Stack

- Python  
- PyTorch  
- NumPy / SciPy  
- Scikit-learn  
- MNE (for EEG processing)

## ▶️ How to Run

Install dependencies:

```bash
pip install -r requirements.txt
jupyter notebook
```

---

## 🚀 Future Work

- Improve stability of advanced domain adaptation methods  
- Explore transformer-based EEG models  
- Investigate subject-specific calibration  
- Extend to real-time BCI systems  

---

## 👤 Author

**Peter Otieno**  
AI Engineer | Data Scientist | BCI Research
