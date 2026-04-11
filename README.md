Overview

This project develops a machine learning-based QSAR (Quantitative Structure–Activity Relationship) framework to predict the inhibitory potency of small molecules targeting the PD-1/PD-L1 immune checkpoint pathway, a critical mechanism in cancer immune evasion.

While antibody therapies exist, they are limited by cost, toxicity, and delivery challenges. This work explores data-driven discovery of small-molecule inhibitors using molecular descriptors and ensemble learning models.

The study compares model performance across:

A real-world dataset (ChEMBL) with high variability
A curated dataset (GitHub PD-L1) with standardized measurements

As shown in the report , dataset quality plays a central role in predictive performance.

🎯 Objectives
Predict PD-L1 inhibitory activity (pIC50) using molecular descriptors
Compare performance of ensemble ML models
Evaluate the impact of dataset quality on QSAR modeling
Identify key molecular features driving biological activity
📂 Project Structure
├── data/
│   ├── chembl_dataset.csv
│   ├── github_pdl1_dataset.csv
│
├── notebooks/
│   ├── data_preprocessing.ipynb
│   ├── descriptor_generation.ipynb
│   ├── model_training.ipynb
│
├── src/
│   ├── preprocessing.py
│   ├── descriptors.py
│   ├── models.py
│
├── results/
│   ├── figures/
│   ├── performance_tables.csv
│
├── README.md
└── requirements.txt
🧪 Dataset Description
1. ChEMBL Dataset
Source: Public bioactivity database
Initial records: ~1770 IC50 values
Final processed dataset: 738 unique molecules
Characteristics:
High variability
Experimental noise
Real-world complexity
2. GitHub PD-L1 Dataset
Source: Curated dataset from patent-derived compounds
Size: ~2044 molecules
Characteristics:
Cleaner distribution
More consistent activity values
Easier for models to learn
⚙️ Data Preprocessing

Key steps:

Convert IC50 → pIC50 (log transformation)
Remove duplicates using SMILES
Aggregate repeated measurements using median
Handle missing values using median imputation
Standardize molecular structures

This transformation reduces skewness and stabilizes variance, improving regression performance .

🧬 Descriptor Generation

Descriptors were generated using:

RDKit → 217 descriptors
Mordred → 1,613 descriptors
Feature Engineering Pipeline:
Combine descriptors → 1830 features
Remove:
Missing / infinite values

80% zero features

Apply variance filter (<0.1)
Remove highly correlated features (>0.9)

👉 Final feature matrix: (738, 161)

Descriptors capture:

Molecular weight
Hydrophobicity (LogP)
Surface area
Electronic properties
🤖 Models Used

Three regression models were trained:

Model	Description
Random Forest	Robust to noise, good baseline
Gradient Boosting	Sequential learning, reduces bias
XGBoost	Optimized boosting with regularization
Training Setup:
Train/Test split: 80/20
Libraries: scikit-learn, xgboost
Environment: Google Colab
📊 Evaluation Metrics
R² (Coefficient of Determination) → model fit
RMSE → penalizes large errors
MAE → average prediction error
📈 Results
ChEMBL Dataset (Noisy)
Model	RMSE	MAE	R²
Random Forest	0.72	0.524	0.476
Gradient Boosting	0.732	0.512	0.459
XGBoost	0.737	0.531	0.452

👉 Moderate performance due to dataset variability

GitHub Dataset (Curated)
Model	RMSE	MAE	R²
Random Forest	0.36	0.265	0.639
Gradient Boosting	0.368	0.270	0.625
XGBoost	0.356	0.257	0.648

👉 Significant improvement due to cleaner data

🔍 Key Insights
Dataset quality > model selection
XGBoost performs best on curated datasets
Random Forest is more stable on noisy data
Small subset of descriptors drives most predictions

Top contributing features:

Hydrophobicity (MolLogP)
Surface area (VSA descriptors)
Electronic properties (BCUT descriptors)
📉 Model Comparison to Literature
This study (best): R² ≈ 0.65
Tong et al.: R² ≈ 0.83

👉 Gap highlights need for:

Better feature engineering
Fingerprint-based representations
Model optimization
🚀 Future Work
Incorporate Morgan fingerprints
Compare with MACCS keys
Apply SHAP for interpretability
Improve hyperparameter tuning
Explore deep learning models
🧑‍💻 Technologies Used
Python
RDKit
Mordred
Scikit-learn
XGBoost
Pandas / NumPy
Matplotlib
👥 Authors
Binh Diep – Data preprocessing, modeling
Sai Charitha Gopa – Descriptor generation, analysis
Rishik Kondura – Literature review, documentation
📚 References
Tong et al., Discovery of Novel PD-L1 Inhibitors Using Machine Learning
ChEMBL Database (2024)
Kuttappan et al., ML-assisted virtual screening
💡 How to Run
# Clone repo
git clone https://github.com/yourusername/pdl1-qsar

# Install dependencies
pip install -r requirements.txt

# Run notebooks
jupyter notebook
🧠 Final Takeaway


