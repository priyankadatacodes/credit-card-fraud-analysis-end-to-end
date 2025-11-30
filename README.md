# **Credit Card Fraud Analysis — End-to-End **

**Author:** Priyanka  
**Tools Used:** Python, Pandas, NumPy, Matplotlib, Seaborn, SMOTE, XGBoost, Joblib  
**Dataset:** Kaggle Credit Card Fraud Dataset  

---

# **1. Problem Statement**

Credit card fraud is rare, hidden, and financially damaging.  
Banks need a robust system that can detect fraudulent transactions quickly and accurately.  
The purpose of this project is to analyze transaction behavior, identify fraud patterns, and build a data-driven detection system using machine learning.

---

# **2. Business Understanding**

Financial institutions aim to:

- Reduce financial loss caused by fraudulent activity  
- Detect suspicious transactions early  
- Minimize false alerts to avoid customer inconvenience  
- Strengthen risk monitoring and compliance  
- Understand fraud timing, behavior, and transaction patterns  

This project supports fraud risk teams by providing insights and predictive capabilities to enhance fraud prevention systems.

---

# **3. Business Objectives**

- Identify fraudulent transactions from historical data  
- Understand fraud behavior patterns  
- Minimize missed frauds by improving recall  
- Provide data and KPIs for risk dashboards  
- Build an interpretable, analyst-friendly ML model  

---

# **4. Data Understanding**

**Dataset Features**

- Total rows: 284,807  
- Fraud cases: 0.17%  
- Features include:  
  - `V1–V28`: PCA-transformed transaction behavior features  
  - `Amount`: Transaction value  
  - `Time`: Seconds elapsed since dataset start  
- Target variable:  
  - `Class` = 1 (Fraud)  
  - `Class` = 0 (Non-Fraud)

**Feature Engineering**

- Standardized:
  - `scaled_amount`  
  - `scaled_time`
- Derived business feature:
  - `Hour` extracted from `Time`

These features help capture real-world transaction behavior and hidden fraud signals.

---

# **5. Approach and Methodology**

1. **Data Cleaning**  
   - Removed duplicates  
   - Verified missing values  

2. **Feature Engineering**  
   - Scaled `Amount` and `Time`  
   - Added `Hour` for business interpretation  

3. **Exploratory Data Analysis**  
   - Fraud hour trends  
   - Amount distributions  
   - Fraud vs Non-Fraud differences  
   - Correlation patterns  

4. **Handling Class Imbalance**  
   - Applied SMOTE on training data only  

5. **Train-Test Split**  
   - Stratified split to preserve fraud ratio  

6. **Modeling**  
   - XGBoost classifier  
   - Uses PCA behavioral features + engineered features  

7. **Threshold Optimization**  
   - Improved recall by tuning classification threshold  

8. **Evaluation**  
   - Precision, Recall, F1 Score, ROC-AUC  
   - Confusion matrices for default and optimized thresholds  

9. **Reporting Outputs**  
   - Predictions  
   - KPIs  
   - Feature importance  
   - Power BI–ready CSVs  
   - Audit files  

---

# **6. Exploratory Data Analysis Insights**

## **6.1 Fraud Transactions by Hour**

Fraud is not random. It peaks during:

- Early morning (around 2 AM)  
- Midday (11 AM–12 PM)  
- Evening (5 PM–6 PM)

These hours represent either low user activity or high transaction volume, making fraud attempts easier.

---

## **6.2 Scaled Amount Distribution**

- Transaction amounts are highly right-skewed  
- Most transactions are small  
- Large transactions are rare  

Fraudsters commonly perform small test transactions before larger attempts.

---

## **6.3 Fraud vs Non-Fraud Amount Distribution**

- Genuine users show diverse spending patterns  
- Fraud amounts are more clustered  
- High-value fraud is less common  

Fraud behavior is more uniform than normal customer behavior.

---

## **6.4 Correlation Heatmap**

- PCA features (`V1–V28`) are largely independent  
- Engineered features contribute meaningful context  
- The fraud label (`Class`) has weak direct correlation with all features  

Fraud patterns are subtle and require ML-based detection.

---

# **7. Modeling Strategy**

**Model Chosen:** XGBoost Classifier  
Reasoning:

- Strong performance on tabular data  
- Captures complex behavioral fraud patterns  
- Efficient and interpretable  
- Works well with imbalanced datasets  

**Features Used:**

- PCA features (`V1–V28`)  
- `scaled_amount`  
- `scaled_time`  
- `Hour`

---

# **8. Model Evaluation**

Two evaluations were performed:

## **8.1 Default Threshold (0.5)**

- Acceptable precision  
- Lower recall (misses fraud cases)  
- Not ideal for banking fraud detection  

## **8.2 Optimized Threshold**

Using precision-recall curve analysis, an optimized threshold was selected.

Results:

- Significant improvement in recall  
- Better fraud detection rate  
- Slight increase in false positives (acceptable for risk teams)

**Metrics Exported:**

- Precision  
- Recall  
- F1 Score  
- ROC-AUC  
- Confusion Matrices  

---

# **9. Feature Importance Results**

Most influential features:

- Behavioral PCA components such as `V10`, `V12`, `V14`, `V17`  
- `scaled_amount`  
- `Hour`

These indicate fraud is driven by behavioral deviations rather than simple rules.

---

# **10. Business Impact**

This project provides:

- Improved fraud detection performance  
- Insights into fraud timing and behavior  
- Reduced monetary loss through early detection  
- Power BI–ready outputs for monitoring  
- Full audit trail for compliance  
- A model that supports analysts and fraud teams  

---

# **11. Deliverables**

The project outputs include:

- Plots (hour trends, distributions, correlation heatmap)  
- CSV files (predictions, KPIs, confusion matrices)  
- Balanced training dataset  
- Trained XGBoost model  
- Scalers  
- Row-level probabilities  
- Jupyter Notebook  
- Dashboard-ready outputs  

---

# **12. Final Summary**

This project demonstrates capability in:

- Handling real-world imbalanced data  
- Understanding fraud behavior  
- Applying ML for anomaly detection  
- Creating actionable business insights  
- Preparing reporting-ready outputs  
- Building an end-to-end fraud analysis pipeline  

It reflects how fraud analytics workflows operate in banking and fintech environments.

