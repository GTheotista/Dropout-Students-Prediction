# **Dropout Students Prediction**

**Tools:** Python  
**Visualizations:** Matplotlib, Seaborn  
**Dataset:** [UCI Predict Students Dropout and Academic Success](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

---

## **Table of Contents**
- [Step 0: Business Problem Understanding](#step-0-business-problem-understanding)
- [Step 1: Data Understanding & Preprocessing](#step-1-data-understanding--preprocessing)
- [Step 2: Modeling](#step-2-modeling)
- [Step 3: Conclusion](#step-3-conclusion)
- [Step 4: Recommendations](#step-4-recommendations)
- [Step 5: Business Impact](#step-5-business-impact)
- [Step 6: Limitations](#step-6-limitations)
- [Step 7: Next Steps](#step-7-next-steps)

---

## **Step 0: Business Problem Understanding**

### Context
Student retention is a major challenge for higher education institutions. Student dropouts result in revenue loss, lower graduation rates, and a negative impact on institutional reputation.

### Problem Statement
- **Student Perspective:** Students face academic, financial, or personal difficulties that may lead to dropping out. Early identification helps provide targeted support.  
- **Institutional Perspective:** Universities need a reliable model to predict which students are at risk to design proactive retention strategies.

### Goals
1. Build a machine learning model to classify students as Dropout or Non-Dropout.  
2. Identify key academic, socio-demographic, and financial factors affecting dropout.  
3. Provide actionable insights to support early intervention programs.

---

## **Step 1: Data Understanding & Preprocessing**

- **Source:** Dataset obtained from [UCI Repository](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success).  
- **Content:** Includes demographic, academic, and financial information of students, with the target variable indicating Dropout or Non-Dropout.

### Key Preprocessing Steps
- **Categorical Reduction:** Grouped rare categories (e.g., Nationality into Portuguese vs Others).  
- **Feature Scaling:** Used RobustScaler for features with heavy outliers (grades and enrolled units).  
- **Encoding:** Applied One-Hot Encoding to categorical variables.  
- **Feature Selection:** Removed redundant and low-variance features to reduce noise and improve generalization.

### Insights from Data Exploration
- Students with low grades and failed curricular units in the first semester are more likely to drop out.  
- Tuition payment status and scholarship information show a strong relationship with retention.  
- Non-standard admission modes (Over 23, Change Course, Others) correlate with higher dropout rates.

---

## **Step 2: Modeling**

- **Models Tested:** Logistic Regression, Random Forest, XGBoost, LightGBM.  
- **Evaluation Metrics:** Accuracy, ROC-AUC, Precision, Recall, F1-Score.  
- **Class Imbalance Handling:** Compared standard model vs. ROS, SMOTE, and Class Weights.

### Multicollinearity Check
- Performed Variance Inflation Factor (VIF) analysis.  
- Dropped features with VIF > 10 to avoid multicollinearity and improve model stability.

### Best Model
- **Standard Logistic Regression** was selected as the final model.

### Performance (Test Set)
- Accuracy: ~0.85  
- ROC-AUC: ~0.90  
- Recall: ~0.94 (captures most dropouts, aligning with the project goal).

### Key Predictors
- Curricular Units 2nd Semester (Approved).  
- Application Mode (Others, Over 23, Change Course).  
- Tuition Fees Up to Date and Scholarship Holder.  
- Previous and Admission Qualification Grades.

---

## **Step 3: Conclusion**

- Standard Logistic Regression achieves a strong balance between recall and generalization without resampling.  
- Academic performance, admission mode, and financial status are the strongest predictors of dropout risk.  
- The model achieves high recall (~0.94), enabling early intervention for at-risk students.

---

## **Step 4: Recommendations**

### Academic Affairs
- Track students with failed or low grades early and implement mentoring programs.  
- Provide tailored orientation for students entering via Over 23, Change Course, or Other application modes.

### Financial Department
- Offer payment plans and financial counseling for students flagged as debtors.  
- Integrate tuition payment status into an early-warning risk dashboard.

### Student Services
- Flag at-risk students for academic, financial, and psychological support.  
- Build a dashboard with updated risk scores every semester.

### Institutional Policy
- Retrain the model annually to maintain performance.  
- Collect additional behavioral and socio-economic features (attendance, engagement).

---

## **Step 5: Business Impact**

- With recall around 0.94, the model captures most at-risk students, enabling timely intervention.  
- Supports data-driven decision making to optimize academic and financial resource allocation.  
- Contributes to lowering dropout rates and improving institutional retention.

---

## **Step 6: Limitations**

- Non-academic factors (psychological, social, personal) are not included.  
- Dataset covers only one period, which may affect generalization to future cohorts.  
- Predicts only binary dropout status without estimating when dropout might occur.

---

## **Step 7: Next Steps**

- **Deployment:** Build an API or dashboard to integrate predictions into the student management system.  
- **Retraining:** Update and retrain the model every semester or academic year.  
- **Feature Expansion:** Add real-time behavioral and socio-economic indicators for better accuracy.
