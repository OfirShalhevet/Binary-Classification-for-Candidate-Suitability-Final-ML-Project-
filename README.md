# Machine Learning Final Project – Candidate Hiring Prediction

**Author:** Ofir Shalhevet  
**Date:** August 2024  

---

## Objective
The goal of this project was to build a **binary classification model** that predicts whether a job candidate is suitable (1) or unsuitable (0) for hiring, based on structured features.  

The work included the full ML pipeline: **data exploration, preprocessing, feature engineering, model training, and evaluation**.

---

## Data & Preprocessing
- **Data Cleaning**: removed rows with excessive missing values, handled outliers (Winsorization).  
- **Feature Engineering**:  
  - Converted categorical variables (e.g., country → continent, sex → binary).  
  - Constructed new features, such as a ratio of years of experience and variable B.  
  - Designed a **stack experience score** by weighting programming languages according to industry popularity.  
- **Encoding & Scaling**:  
  - One-Hot Encoding for unordered categories.  
  - Ordinal Encoding for ordered features like education.  
  - MinMaxScaler for normalization.  

---

## Models Tested
Several algorithms were compared:  
- **K-Nearest Neighbors (KNN)** – stable with AUC ≈ 0.81 (best at k=14).  
- **Naive Bayes** – worked decently but weaker on mixed data.  
- **Decision Tree** – good interpretability but prone to overfitting.  
- **Random Forest** – best performance after hyperparameter tuning with Grid Search.  

---

## Final Model – Random Forest
- **Validation Accuracy:** ~0.82  
- **AUC:** ~0.868  
- **Overfitting check:** train accuracy slightly higher, mitigated using PCA and tuning.  
- **Calibration:** applied `CalibratedClassifierCV (sigmoid)` → improved probability reliability (AUC ≈ 0.8644).  
- **Feature Importance:**  
  - `stack_experience` → most significant predictor  
  - `D`, `previous salary`, `education`, `years of experience` also important  

---

## 📊 Evaluation
- **Confusion Matrix results:**  
  - True Positive Rate (TPR): ~88.5%  
  - True Negative Rate (TNR): ~64.1%  
  - False Positive Rate (FPR): ~18.4% (most critical error)  
  - False Negative Rate (FNR): ~11.5%  
- Balanced performance with reliable probability outputs after calibration.  

---

## 📂 Repository Contents
- `notebook_ml.ipynb` – Full notebook with preprocessing, training, and evaluation  
- `report_ml.pdf` – Detailed report with methodology and results  
- `README.md` – Project overview  

---

## Future Work
- Explore ensemble boosting methods (XGBoost, LightGBM).  
- Address fairness & bias in hiring predictions.  
- Refine feature engineering with additional socio-economic indicators.  
- Deploy as an **interactive web application** or API for candidate screening.  

---

✨ This project demonstrates end-to-end machine learning development, combining data preprocessing, model experimentation, and deployment-oriented improvements.
