# F-NRO: F-Score–Based Nuclear Reaction Optimization for Gene Selection  
### Official Repository of the Method Published in *Current Issues in Molecular Biology (2025)*  
**“Hybrid Gene Selection Algorithm for Cancer Classification Using Nuclear Reaction Optimization (NRO)”**  
Alkamli & Alshamlan, 2025  
 
---

## 📌 Overview

This repository presents the methodology, datasets, and experimental results of **F-NRO**, a hybrid gene-selection algorithm designed for high-dimensional microarray cancer datasets.  

F-NRO integrates:

- **F-Score filtering** for initial dimensionality reduction  
- **Nuclear Reaction Optimization (NRO)** as a metaheuristic search  
- **Linear SVM classification** evaluated with **Leave-One-Out Cross-Validation (LOOCV)**  

The framework effectively reduces thousands of genes to a small predictive subset while achieving **state-of-the-art accuracy** on six benchmark datasets.

According to the published paper, F-NRO achieves:

- **100% accuracy** on *five* datasets  
- **98.39% accuracy on Colon**  
- **Very compact gene subsets (2–22 genes)**  
- Competitive performance against 10 hybrid gene-selection algorithms  

---

## 🔒 Code Availability

The implementation of the F-NRO algorithm is available upon request for academic and research purposes.

To request access, please contact: shahad.s.alkamli@gmail.com

---

## 📁 Repository Structure

```
F-NRO/
│
├── FNRO.py               # Code availability notice
│
├── Datasets/
│     ├── Colon.arff
│     ├── Lek1.arff
│     ├── Lek2.arff
│     ├── LungM.arff
│     ├── Lym.arff
│     └── SRBCT.arff
│
└── README.md
```

---

## 🔬 Methodology Summary

The F-NRO pipeline consists of three main components:

### **1. Preprocessing**
- Missing value imputation (Lymphoma dataset contains 4.91% missing values)  
- Z-score normalization  
- Label encoding for binary and multiclass datasets  

---

### **2. F-Score Filtering (Top 500 Genes)**
Before optimization, genes are ranked using the **ANOVA F-score**, and the **top 500 genes** are selected as input to NRO.  

This step removes noisy or irrelevant genes while preserving the most informative ones.

---

### **3. Nuclear Reaction Optimization (NRO)**

The optimization phase simulates two nuclear phenomena:

#### **🔹 Nuclear Fission (Exploration)**
- Random perturbation  
- Lévy-flight–based mutation  
- Gaussian variation of selected genes  

#### **🔹 Nuclear Fusion (Exploitation)**
- Ionization operator  
- Solution refinement by combining candidate vectors  
- Adaptive convergence toward high-fitness gene subsets  

Each candidate solution is evaluated by:

- **Binary mask of selected genes**  
- **SVM classifier accuracy** using **LOOCV**  

---

### **4. Classification & Evaluation**

A **linear SVM** is used to measure fitness:

- LOOCV ensures reliable results on small datasets  
- Accuracy is used as the optimization fitness function  
- Experiments repeated **30 times** for statistical validity  

---

## 📊 Datasets

F-NRO is evaluated on six well-known microarray datasets:

| Dataset | Classes | Samples | Genes |
|--------|---------|---------|--------|
| Colon | 2 | 62 | 2000 |
| Leukemia 1 | 2 | 72 | 7129 |
| Leukemia 2 | 3 | 72 | 7129 |
| Lung | 2 | 96 | 7129 |
| Lymphoma | 3 | 62 | 4026 |
| SRBCT | 4 | 83 | 2308 |

---

## 📈 Published Results (CIMB 2025)

| Dataset | Selected Genes | Accuracy |
|--------|----------------|----------|
| **Colon** | 22 genes | **98.39%** |
| **Leukemia 1** | 3 genes | **100%** |
| **Leukemia 2** | 7 genes | **100%** |
| **Lung** | 2 genes | **100%** |
| **Lymphoma** | 2–3 genes | **100%** |
| **SRBCT** | 7 genes | **100%** |

F-NRO demonstrates excellent stability and accuracy across all datasets while maintaining very small gene subsets.

---

## 📝 Citation

If you use this work, please cite:

```
Alkamli, S.; Alshamlan, H. Hybrid Gene Selection Algorithm
for Cancer Classification Using Nuclear Reaction Optimization (NRO).
Current Issues in Molecular Biology, 2025.
```

---

## 📜 License

This repository is provided for **academic and research purposes only**.
