# F-NRO: F-Score–Based Nuclear Reaction Optimization for Gene Selection  
### Official Implementation of the Method Published in *Current Issues in Molecular Biology (2025)*  
**“Hybrid Gene Selection Algorithm for Cancer Classification Using Nuclear Reaction Optimization (NRO)”**  
Alkamli & Alshamlan, 2025  

---

## 📌 Overview

This repository contains the official implementation of **F-NRO**, a hybrid gene-selection algorithm designed for high-dimensional microarray cancer datasets.  
F-NRO integrates:

- **F-Score filtering** for initial dimensionality reduction  
- **Nuclear Reaction Optimization (NRO)** as a metaheuristic search  
- **Linear SVM classification** evaluated with **Leave-One-Out Cross-Validation (LOOCV)**  

The framework effectively reduces thousands of genes to a small predictive subset while achieving **state-of-the-art accuracy** on six benchmark datasets.

According to the published paper, F-NRO achieves:

- **100% accuracy** on *five* datasets  
- **98.39% accuracy on Colon*  
- **Very compact gene subsets (2–22 genes)**  
- Competitive performance against 10 hybrid gene-selection algorithms  

---

## 📁 Repository Structure

```
F-NRO/
│
├── FNRO.py               # Full implementation of F-Score + NRO
│
├── Datasets/             # Microarray datasets in ARFF format
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

### **2. F-Score Filtering (Top 500 Genes)**
Before optimization, genes are ranked using the **ANOVA F-score**, and the **top 500 genes** are selected as input to NRO.  
This step removes noisy or irrelevant genes while preserving the most informative ones.

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

All datasets are included in **ARFF** format.

---

## 📈 Published Results (CIMB 2025)

The following results replicate Tables 2–7 from the publication.

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

## 🥇 Comparative Performance

As reported in **Table 8**, F-NRO was compared to:

- F-FSAPV  
- F-FF  
- Relief-MBO  
- mRMR-ABC  
- mRMR-PSO  
- Co-ABC  
- PCC-GA  
- HHO-GRASP  
- mRMR-GA  

### **F-NRO achieved:**

- ⭐ **Highest accuracy on 5 datasets**  
- ⭐ **Perfect accuracy on Leukemia1, Leukemia2, Lung, Lymphoma, and SRBCT**  
- ⭐ **Competitive subset sizes (2–22 genes)**  
- ⭐ **Strong consistency across 30 runs**  

This places F-NRO among the **top-performing hybrid gene-selection algorithms** in the field.

---

## ▶️ Running the Code

### Install dependencies
```bash
pip install numpy pandas scipy scikit-learn tqdm
```

### Run F-NRO
```bash
python FNRO.py
```

The script will:

- Load each ARFF dataset  
- Apply F-score filtering  
- Run NRO optimization  
- Evaluate using LOOCV  
- Output the best accuracy and selected gene subset  

---

## 📝 Citation

If you use this code, please cite:

```
Alkamli, S.; Alshamlan, H. Hybrid Gene Selection Algorithm
for Cancer Classification Using Nuclear Reaction Optimization (NRO).
Current Issues in Molecular Biology, 2025.
```
---

## 📜 License
This repository is released for academic and research purposes.

