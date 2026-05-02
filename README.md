


# 🧬 Machine Learning-Based QSAR Modeling for PD-L1 Inhibitors

## 📌 Overview

This project presents a **machine learning-driven QSAR (Quantitative Structure–Activity Relationship) pipeline** to predict the inhibitory potency (**pIC50**) of small molecules targeting **PD-L1**, a critical immune checkpoint in cancer immunotherapy.

The workflow integrates:

* Multi-source molecular feature engineering
* Ensemble machine learning models
* SHAP-based interpretability



## 🎯 Objectives

* Predict **PD-L1 inhibitory activity (pIC50)** from molecular structure
* Compare multiple **feature representations** (descriptors + fingerprints)
* Evaluate different **ensemble ML models**
* Apply **SHAP** for feature importance and interpretability
* Build a **reproducible drug discovery pipeline**

---

## 🧪 Dataset

* Source: **ChEMBL database**
* Initial size: ~1,770 compounds
* Target: **PD-L1 (CD274)**
* Label: **pIC50 (−log10 IC50)**

### Data Preprocessing

* Removed duplicate molecules (SMILES-based)
* Validated chemical structures using RDKit
* Filtered PD-L1-specific records
* Removed missing values

📊 Final dataset: Clean, curated, and ready for modeling 

---

## ⚙️ Feature Engineering

Four types of molecular features were generated:

### 1. RDKit Descriptors

* Molecular weight, LogP, TPSA
* Hydrogen bond donors/acceptors
* Topological indices

### 2. Mordred Descriptors

* ~1800 2D descriptors
* Structural, electronic, geometric properties

### 3. MACCS Keys

* 167-bit structural fingerprints
* Interpretable substructure patterns

### 4. Morgan Fingerprints (ECFP4)

* 1024-bit circular fingerprints
* Captures local chemical environments

---

### 🔗 Feature Set Configurations

* Descriptors only (RDKit + Mordred)
* MACCS only
* Morgan only
* MACCS + Morgan
* All features combined

📌 Best performance achieved with **combined feature sets** 

---

## 🤖 Machine Learning Models

Three ensemble models were trained:

| Model                   | Type              | Key Strength                      |
| ----------------------- | ----------------- | --------------------------------- |
| Random Forest           | Bagging           | Robust, reduces variance          |
| Gradient Boosting (GBM) | Boosting          | Sequential learning               |
| XGBoost                 | Advanced Boosting | Regularization + high performance |

### Train/Test Split

* 80% training / 20% testing
* Fixed random seed for reproducibility

---

## 📊 Evaluation Metrics

* **RMSE** – penalizes large errors
* **MAE** – average prediction error
* **R²** – variance explained

📌 Benchmark:

* R² ≥ 0.60 → acceptable QSAR model
* R² ≥ 0.70 → strong model 

---

## 🚀 Key Results

### 🥇 Best Model

* **XGBoost (All Features + SHAP selection)**
* **R² ≈ 0.69**
* Competitive with literature benchmarks 

---

### 📈 Performance Insights

* Feature fusion > single feature sets
* Morgan fingerprints outperform MACCS alone
* XGBoost consistently best across configurations

📊 As shown in *Table I (page 6)*, combined features significantly improved model performance.

---

## 🔍 SHAP Interpretability

SHAP (Shapley Additive Explanations) was used to:

* Identify **top predictive features**
* Explain model decisions
* Improve interpretability

### 🔑 Key Findings

* Hydrophobicity (LogP-related descriptors) strongly influences activity
* Aromatic structures and ring systems are critical
* Molecular topology impacts binding affinity

📊 *Beeswarm plot (page 8)* shows how features shift predictions 

---

### 🎯 Feature Selection

* Top **50 SHAP-ranked features** selected
* Reduced dimensionality from thousands → 50
* Maintained or improved performance

📌 Result: Better interpretability + efficiency

---

## 📉 Error Analysis

### Observations:

* Higher errors at extreme pIC50 values
* Model performs best in mid-range (5.5–7.0)
* Outliers include:

  * Rare molecular scaffolds
  * Highly potent/weak compounds

📊 *Scatter plot (page 8)* shows prediction alignment with true values 

---

## 💡 Key Insights

* Combining descriptors + fingerprints is critical
* XGBoost is highly effective for QSAR tasks
* SHAP provides **chemically meaningful interpretation**
* Small feature subsets can retain predictive power

---

## 🧠 Business / Scientific Impact

This pipeline:

* Accelerates **early-stage drug discovery**
* Supports **PD-L1 inhibitor design**
* Bridges **AI predictions with medicinal chemistry insights**

---

## 🛠️ Tech Stack

* Python
* RDKit
* Mordred
* Scikit-learn
* XGBoost
* SHAP
* Pandas / NumPy / Matplotlib

---

## 🔮 Future Work

* Incorporate **3D molecular descriptors**
* Use **Graph Neural Networks (GNNs)**
* Expand dataset size for better generalization
* Ensemble models (stacking RF + XGB)

---

## 📂 Project Structure (Suggested)

```
├── data/
├── notebooks/
├── src/
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── models.py
│   └── shap_analysis.py
├── results/
├── README.md
└── requirements.txt
```

---

## 👤 Authors

* **Binh Diep**
* Sai Charitha Gopa
* Rishik Kondura

Long Island University – Spring 2026

---

## 📚 References

See full IEEE paper for detailed references:


---

## ⭐ Key Takeaway

> Combining **multi-feature molecular representations + XGBoost + SHAP interpretability** creates a powerful and practical QSAR pipeline for real-world drug discovery.

---

