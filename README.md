# Loan-Approval-Predictio
This project predicts whether a loan application will be approved or rejected based on applicant details such as income, credit history, employment status, and loan amount. The model helps financial institutions automate and streamline the loan approval process, reducing manual effort and improving decision accuracy.


## Tools and Libraries Used
- **Python**  
- **Pandas, NumPy** – data manipulation  
- **Matplotlib, Seaborn** – visualization  
- **Scikit-learn** – machine learning models and evaluation  

---

## Dataset
- Contains applicant information such as:
  - CIBIL Score
  - Income
  - Loan Amount & Term
  - Assets (Residential, Commercial, Luxury, Bank)
  - Education Level
  - Self-Employment Status
  - Number of Dependents  
- Format: CSV (`loan_approval_dataset.csv`)  

> **Note:** `loan_id` column was removed as it is an identifier and does not contribute to prediction.

---

## Steps Followed

### 1. Data Cleaning
- Checked for missing/null values → none found.  
- Removed extra spaces in column names.  
- Dropped irrelevant identifier column (`loan_id`).  

### 2. Exploratory Data Analysis (EDA)
- **Target Distribution**: Checked approval vs rejection counts.  
- **Boxplots**:
  - **CIBIL Score** → strong positive correlation with approval.  
  - **Income** → median similar across classes; weak predictor alone.  
  - **Loan Amount & Assets** → moderate influence on approval.  
- **Correlation Heatmap**:
  - Strong correlations among asset-related features.  
  - CIBIL Score largely independent → strong predictive power.  

3. Data Preprocessing
Separated features (X) and target (y).

Identified categorical features (education, self_employed) and encoded using one-hot encoding.

Standardized numerical features with StandardScaler for stable model training.

4. Train-Test Split
Split dataset: 80% train, 20% test using stratified sampling to preserve class distribution.

5. Model Training: Logistic Regression
Trained baseline Logistic Regression model.

Model evaluation:

Accuracy = 0.9133 (91%).
Confusion Matrix : 

[[280  43]
 [ 31 500]]
 
True Positives (TP): 500 → approved correctly

True Negatives (TN): 280 → rejected correctly

False Positives (FP): 43 → risky loans approved

False Negatives (FN): 31 → good loans rejected

Classification Report


Class	Precision	Recall	F1-score	Support
0 (Rejected)	0.90	0.87	0.88	323
1 (Approved)	0.92	0.94	0.93	531
Accuracy	-	-	0.91	854

High recall for approved loans → low missed opportunities.

Balanced precision and recall for both classes → minimal risk and reliable predictions.

6. Feature Importance (Logistic Regression Coefficients)
Feature	Coefficient
cibil_score	4.091

loan_amount	1.321

bank_asset_value	0.180

luxury_assets_value	0.126

commercial_assets_value	0.093

residential_assets_value	0.044

self_employed_Yes	0.015

education_Not Graduate	-0.065

no_of_dependents	-0.076

loan_term	-0.859

income_annum	-1.595

Interpretation:

CIBIL Score → strongest positive influence on approval

Loan Amount & Assets → moderate positive effect

Income → slightly negative effect when combined with assets

Minor features (education, dependents, self-employment) → minimal influence

Key Insights
Credit history (CIBIL Score) dominates loan approval.

Applicant assets positively influence approval probability.

Income alone has weak influence — must be considered with assets.

Long loan terms slightly reduce approval likelihood.

Logistic Regression achieves 91% accuracy with balanced precision/recall.

Conclusion
The baseline Logistic Regression model provides a strong, interpretable prediction framework for loan approval decisions. It identifies key financial and credit factors influencing approvals and can serve as a foundation for deploying more advanced models, such as Random Forest or XGBoost, in the future.

