---

## **Report (reports/report.md)**
```markdown
# **Fraud Detection Model Report**

## **1. Problem Statement**
Detect fraudulent transactions while minimizing false negatives (missed fraud).

## **2. Data Overview**
- **284,807 transactions** (492 frauds → 0.17% imbalance)
- **Features**: Time, Amount, V1-V28 (PCA-transformed)

## **3. Methodology**
### **Preprocessing**
- Scaled `Amount` (RobustScaler)
- Split into **70-30 train-test**
- Applied **SMOTE oversampling** to balance classes

### **Models Tested**
| Model               | Recall | Precision | F1-Score |
|---------------------|--------|-----------|----------|
| Logistic Regression | 0.72   | 0.81      | 0.76     |
| Random Forest       | 0.92   | 0.85      | 0.88     |
| XGBoost             | 0.89   | 0.87      | 0.88     |

## **4. Key Findings**
- **Random Forest** performed best (Recall **92%**)
- **SMOTE** improved minority class detection
- **Feature V14** most important for fraud detection

## **5. Recommendations**
- Deploy **Random Forest** with threshold tuning
- Monitor **false positives** to avoid customer friction
- Retrain monthly with new fraud patterns
