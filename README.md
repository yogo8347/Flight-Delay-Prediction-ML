# Flight Delay Prediction ✈️⏰

This project analyzes and predicts **flight delays** using real-world airline data and machine learning.  
It combines **exploratory data analysis (EDA), feature engineering, class balancing (SMOTE), classification, regression, and SHAP explainability** to understand and forecast delays.

---

## 📌 Project Overview
Flight delays create operational inefficiencies for airlines and stress for passengers.  
By predicting delays, airlines can:
- Optimize scheduling & reduce costs.
- Improve passenger experience.
- Enhance reliability of the air travel ecosystem.

This project uses airline performance data to:
1. Analyze delay causes and seasonal patterns.  
2. Build classification models to predict **if a flight will be delayed**.  
3. Build regression models to estimate **how long a delay might last**.  
4. Explain model predictions using **SHAP values**.  

---

## 🛠 Methodology

### 🔹 Data Loading & Preprocessing
- Loaded U.S. airline on-time performance dataset.  
- Handled missing values in operational columns.  
- Created **month_year** identifiers for temporal trends.  

### 🔹 Exploratory Data Analysis (EDA)
- Analyzed delay causes: **Late Aircraft, Carrier, NAS, Weather, Security**.  
- Found that **73% of delays are controllable** (aircraft turnaround & carrier inefficiencies).  
- Seasonal spikes in delays observed (especially post-COVID).  
- Airport-specific and carrier-specific delay profiles studied.  

### 🔹 Feature Engineering
- **Targets**:
  - `is_delayed` → Binary classification target.  
  - `avg_arrival_delay` → Regression target (minutes).  
- Created features:
  - Delay per flight metrics (carrier, weather, NAS, aircraft).  
  - Cancel & divert rates.  
  - Seasonal flags (`is_winter`, `is_peak_month`).  
  - Time cyclic encoding (`month_sin`, `month_cos`).  
- One-hot encoded categorical variables (airport, carrier).  

### 🔹 Class Balancing
- Target (`is_delayed`) was **imbalanced** (19% delayed flights).  
- Applied **SMOTE** to balance training data.  

### 🔹 Model Training
**Classification Models**  
- Logistic Regression, Decision Tree, KNN, Random Forest, Gradient Boosting, XGBoost, LightGBM.  
- Best: **Gradient Boosting (F1 = 0.88, ROC-AUC = 0.80)**.  

**Regression Models**  
- Linear Regression, Decision Tree, KNN, Random Forest, Gradient Boosting, XGBoost, LightGBM.  
- Best: **XGBoost Regressor (MAE = 3.10 min, R² = 0.36)**.  

### 🔹 Explainability (SHAP)
- **Classification**: Winter months, number of arriving flights, and airport features strongly influence predictions.  
- **Regression**: Late Aircraft & Carrier delays increase delay durations; higher traffic volume surprisingly reduces average delays.  

---

## 📊 Results
- **Best Classifier**: Gradient Boosting → Accurately predicts whether a flight will be delayed.  
- **Best Regressor**: XGBoost → Estimates average delay duration within ~3 minutes error.  
- **SHAP** confirms operational inefficiencies (late aircraft & carrier) dominate delays.  

---
