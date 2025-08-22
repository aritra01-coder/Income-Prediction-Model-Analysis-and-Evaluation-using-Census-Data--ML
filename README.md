# Income-Prediction-Model-Analysis-and-Evaluation-using-Census-Data--ML


## 1. Introduction
This report summarizes a data analysis and machine learning project aimed at **predicting income levels** based on demographic and socioeconomic factors.  
Leveraging a comprehensive dataset derived from census data, we explored the characteristics influencing income and evaluated several classification algorithms to build a predictive model.  

**Goal:** Identify individuals likely to have an income exceeding **$50,000 annually**, which can inform:  
- Targeted marketing  
- Resource allocation  
- Customer segmentation  

---

## 2. Problem Statement
The core business problem is to predict whether an individual’s annual income is **greater than $50,000** (binary classification).  

This is crucial for businesses to:  
- Identify high-income individuals for **personalized product/service offerings**  
- Optimize sales and marketing strategies  
- Assess **market potential**  

**Challenges:**  
- Missing data  
- Severe imbalance in the target variable (majority earn ≤$50,000, minority earn >$50,000)  

---

## Dataset Description
The **Census Income KDD dataset** is a benchmark dataset for classification. It contains demographic and employment-related details with the goal of predicting whether a person earns more than $50,000.  

**Key Characteristics**:  
- **Instances:** 199,523  
- **Features:** 41  
- **Target Variable:** `Income` (<=50K, >50K)  

**Selected Features:**  

| Feature         | Description |
|-----------------|-------------|
| age             | Continuous. Age of the individual |
| workclass       | Categorical. Employment type (Private, Self-emp, Govt, etc.) |
| education       | Categorical. Highest education attained |
| education-num   | Continuous. Numerical representation of education |
| marital-status  | Categorical. Marital status |
| occupation      | Categorical. Type of job |
| relationship    | Categorical. Relationship to household |
| race            | Categorical. Race of the individual |
| sex             | Categorical. Gender |
| capital-gain    | Continuous. Income from capital gains |
| capital-loss    | Continuous. Income from capital losses |
| hours-per-week  | Continuous. Average weekly working hours |
| native-country  | Categorical. Country of origin |

---

## 3. Data Analysis Summary

### Key Findings
- **Missing Values:** `'?'` values in multiple columns handled via imputation (mode for categorical, median for numerical).  
- **Data Types:** Converted categorical to numerical via one-hot encoding.  
- **Class Imbalance:** ~94% ≤ $50K, ~6% > $50K → accuracy is misleading.  
- **Feature Relationships:** Certain attributes (e.g., education, marital status, capital gains) strongly influence income.  

### EDA Insights
- **Hours per Week:** Higher work hours correlated with higher income likelihood.  
- **Correlation Matrix:**  
  - Education, Capital Loss, Hours per week showed **moderate positive correlation** with income.  
  - Features like Education ↔ Hours per Week also correlated.  
- **Categorical Plots:** Categories like work class, capital gain, and marital status were key indicators of higher income.  

---

## 4. Methodology
Steps followed in model building:  
1. **Data Loading & Combination** – training and test sets merged for preprocessing.  
2. **Data Cleaning** – missing values imputed.  
3. **Feature Engineering** – categorical features → one-hot encoded.  
4. **Data Splitting** – stratified split to preserve imbalance ratios.  
5. **Model Selection:**  
   - Decision Tree  
   - Random Forest  
   - k-Nearest Neighbors (kNN)  
   - XGBoost  
6. **Evaluation Metrics:** Accuracy, Precision, Recall, F1-score (F1 prioritized due to imbalance).  

---

## 5. Model Evaluation and Selection

| Model           | Accuracy | Precision | Recall  | F1-score |
|-----------------|----------|-----------|---------|----------|
| Decision Tree   | 0.9351   | 0.2265    | 0.0188  | 0.0348   |
| Random Forest   | 0.9365   | 0.2646    | 0.0135  | 0.0256   |
| KNeighbors      | 0.9341   | 0.2434    | 0.0296  | **0.0528** |
| XGBoost         | 0.9378   | 0.4200    | 0.0057  | 0.0112   |

**Observations:**  
- High accuracy due to imbalance, but poor recall/F1 for minority class.  
- **KNeighbors** achieved the highest F1-score (0.0528) and was chosen as the best among evaluated models.  

---

## 6. Prediction on New Data
To demonstrate the model:  
- Two records were randomly selected.  
- Preprocessing applied consistently.  
- KNeighbors predicted their income (mapped back to labels `<=50K` or `>50K`).  

---

## 7. Conclusion
- Models built and evaluated: Decision Tree, Random Forest, kNN, XGBoost.  
- Severe **class imbalance** limited model performance.  
- **KNeighbors** performed best (based on F1-score).  
- Accuracy is misleading → metrics like Recall/F1 are more meaningful in this scenario.  

---

## 8. Business Implications

1. **Targeted Marketing**  
   - Identify high-income individuals for **premium product campaigns**.  
   - Efficient allocation of marketing budgets.  

2. **Resource Allocation**  
   - Direct sales/service efforts to higher-income segments.  
   - Improve ROI by focusing resources where returns are higher.  

3. **Customer Segmentation & Offerings**  
   - Refine segmentation to tailor **personalized products/services**.  
   - Better align offerings with high-income customers’ needs.  

4. **Assessing Market Potential**  
   - Identify **geographies or demographics** with higher concentrations of affluent customers.  
   - Useful for expansion and investment strategies.  

5. **Risk Assessment (Indirect)**  
   - Income predictions can support **credit scoring and loan approvals**.  
   - Provides proxy indicators of financial stability.  

---

📌 **Overall Impact**:  
Despite limitations, this project demonstrates the feasibility of applying machine learning to census income prediction. With better class balancing techniques (e.g., SMOTE, cost-sensitive learning), the models could become more effective for **real-world business applications**.
