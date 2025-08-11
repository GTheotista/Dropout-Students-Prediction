# Student Dropout Prediction

**Tools:** Python  
**Visualizations:** Matplotlib, Seaborn  
**Dataset:** [Predict Students Dropout and Academic Success](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

---

## I. Business Problem Understanding

Student retention is a critical challenge for higher education institutions. When students drop out before graduation, it results in financial loss and negatively affects institutional reputation and graduation rates. Early identification of at-risk students enables timely interventions to improve retention.

### Problem Statement
- **Student Perspective:** Many students face academic, financial, or personal challenges that can lead to dropout. Identifying them early allows the institution to provide support and prevent attrition.  
- **Institutional Perspective:** Universities need a predictive model to classify students into Dropout vs Non-Dropout to design proactive strategies that reduce attrition and improve graduation rates.

### Goals
1. Develop a machine learning model to predict student dropout.  
2. Identify key socio-demographic, academic, and financial factors that contribute to dropout.  
3. Provide actionable insights to support early intervention strategies.  

### Business Impact
- Best model can identify most students at risk of dropping out.  
- Enables early academic and financial interventions, reducing dropout rates and improving retention.  
- Supports data-driven resource allocation and policy planning.

---

## II. Data Understanding & Preprocessing

### Dataset Source
[UCI Machine Learning Repository – Predict Students Dropout and Academic Success](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

### Key Steps
- **Data Cleaning & Mapping:** Converted numeric codes to meaningful labels (e.g., marital status, application mode, parental occupation).  
- **Feature Grouping:** Grouped low-frequency categories such as rare admission modes into "Others".  
- **Handling Outliers:** Applied RobustScaler to heavy-tailed numerical features (grades and enrolled/approved curricular units).  
- **Encoding:** Applied One-Hot Encoding for categorical features.  
- **Multicollinearity Check:** Removed features with VIF > 10 to reduce collinearity.  
- **Target Variable:** Converted into binary classes (Dropout vs Non-Dropout).  

---

## III. Modeling

### Algorithms Tested
- Logistic Regression  
- Random Forest  
- XGBoost  
- LightGBM  

### Best Model
- **Logistic Regression (Standard)**  

### Performance (Test Set)
- Accuracy: ~0.87  
- ROC-AUC: ~0.91  
- Recall: ~0.95 (able to capture most dropouts)

### Key Predictors
- Curricular Units 2nd Semester (Approved)  
- Curricular Units 2nd Semester (Grade)  
- Curricular Units 1st Semester (Approved)  
- Application Mode (Others, Over 23, Change Course)  
- Previous Qualification (Secondary Education)  

---

## IV. Conclusion and Recommendations

### Conclusion
- Logistic Regression provided the best balance of generalization and recall (~0.95).  
- Academic performance (approved units and grades) is the most influential factor.  
- Admission pathway and previous qualifications significantly affect dropout risk.

### Recommendations
- **Academic Affairs:**  
  - Monitor students with low first-semester approvals.  
  - Offer mentoring programs to improve course completion.  
  - Provide tailored support for students in non-standard admission modes (Over 23, Change Course).  

- **Financial Department:**  
  - Identify students with unpaid tuition and provide counseling or payment plans.  
  - Integrate tuition fee status into the risk detection dashboard.  

- **Student Services:**  
  - Use the model to proactively flag at-risk students for academic, financial, and psychological support.  
  - Build a dashboard to display updated risk scores each semester for planning interventions.  

---

## V. Next Steps
- Retrain the model annually to maintain accuracy.  
- Integrate socio-economic and behavioral features such as attendance and engagement.  
- Deploy the model as an API or dashboard within the student management system.  
