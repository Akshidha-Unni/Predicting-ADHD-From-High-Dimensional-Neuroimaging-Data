# Predicting-ADHD-Outcomes-And-Sex-From-High-Dimensional-Neuroimaging-Data
A robust multi-label classification pipeline for ADHD and sex prediction using fMRI connectome data with 19,000+ features. Combines preprocessing, feature selection, hyperparameter tuning, and ensemble learning for accurate and interpretable results.

### 🧠 **Problem Statement**
**Goal:** To predict both ADHD diagnosis and biological sex using functional MRI connectome data, which is inherently:
- Extremely high-dimensional (19,000+ features)
- Imbalanced (majority = male, non-ADHD)
- Multi-label (two target variables: ADHD_Outcome and Sex)

**Challenges addressed:**
- Identifying neural biomarkers of ADHD from fMRI matrices
- Disentangling ADHD and sex-based brain patterns
- Ensuring model robustness on small, imbalanced datasets
- Prioritizing interpretability and clinical relevance.

### 📦 **Dataset & Tools**
- 📊 Source: WiDS Datathon 2025
- 💽 Data files:
    - Functional MRI (connectomes)
    - Target labels (ADHD outcome, Sex)
    - Socioeconomic and survey responses

### 🛠️ **Methodology**
🔍 **1. Data Preprocessing**
- **Null Imputation:**
  
     - Categorical: sentinel value (-1)
     - Numeric: MICE (Multivariate Imputation by Chained Equations)  
     
- **Scaling:** StandardScaler applied to avoid feature magnitude bias
- **Imbalance Handling:** Used class_weight strategy to avoid oversampling risks

🔎 **2. Feature Selection**
- **Method:** Lasso-regularized Logistic Regression (SelectFromModel)
- **Why:** Preserves interpretability and handles high-dimensional, multi-label setting better than PCA/LDA

### 🧠 **Results **
- **Linear models (SVM, LR)** performed best — indicating brain-based ADHD differences are likely linearly separable.
- **Stacking** SVM & LR significantly improved generalization.

### 🧩 **Scientific Insights**
- **ADHD Prediction > Sex Prediction**: Functional brain differences linked to ADHD were more distinct than those related to sex.
- **Feature Relevance:** Lasso revealed key neuro-connectivity features as strong indicators — aligned with recent fMRI literature.

### 🚧 **Limitations**
- Low sample size (~1,200) vs high-dimensionality (~19k features)
- Class imbalance impacted minority class recall
- Tree-based models prone to overfitting due to sparse signal
