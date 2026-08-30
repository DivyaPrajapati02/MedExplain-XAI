# MedExplain-XAI 🫀🔬

## Explainable AI for Heart Disease Prediction Using Machine Learning

MedExplain-XAI is a machine learning and Explainable Artificial Intelligence (XAI) project developed to predict the presence of heart disease using clinical patient data and to provide interpretable explanations for model predictions.

The project follows an end-to-end machine learning workflow, including data preprocessing, exploratory data analysis, feature preparation, model development, performance evaluation, and SHAP-based explainability.

The primary objective is not only to build an accurate predictive model but also to understand how different clinical features influence the model's predictions.

---

##  Project Objective

The main objectives of MedExplain-XAI are:

- Develop machine learning models for heart disease prediction.
- Preprocess and analyze clinical patient data.
- Compare the performance of multiple classification algorithms.
- Select the best-performing model based on evaluation metrics.
- Apply Explainable AI techniques to understand model behavior.
- Identify the clinical features that have the greatest influence on predictions.
- Provide both global and individual-level explanations using SHAP.

---

##  Dataset

The project uses the **Cleveland Heart Disease dataset** from the UCI Machine Learning Repository.

The dataset contains clinical information about patients and includes **303 observations and 13 input features** after preprocessing.

### Features Used

- `age` — Age of the patient
- `sex` — Sex
- `cp` — Chest pain type
- `trestbps` — Resting blood pressure
- `chol` — Serum cholesterol
- `fbs` — Fasting blood sugar
- `restecg` — Resting electrocardiographic results
- `thalach` — Maximum heart rate achieved
- `exang` — Exercise-induced angina
- `oldpeak` — ST depression induced by exercise
- `slope` — Slope of the peak exercise ST segment
- `ca` — Number of major vessels
- `thal` — Thalassemia

The original target variable contains multiple disease severity levels. For this project, it was converted into a binary classification target:

- `0` → No heart disease
- `1` → Heart disease

The resulting target distribution contains:

- **164** observations without heart disease
- **139** observations with heart disease

---

##  Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the structure and characteristics of the dataset.

The analysis included:

- Dataset information
- Missing value analysis
- Target distribution analysis
- Feature distributions
- Correlation analysis
- Examination of clinical variables

Missing values were identified in the `ca` and `thal` features and handled during preprocessing.

---

##  Machine Learning Models

Four classification algorithms were developed and compared:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. XGBoost

The dataset was divided into training and testing sets using an **80:20 stratified split**.

### Data Split

- Training samples: **242**
- Testing samples: **61**
- Input features: **13**

Standardization was applied to the features used by Logistic Regression, while tree-based models were trained using the original feature values.

---

##  Model Performance

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

### Results

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 86.89% | 81.25% | 92.86% | 86.67% | 95.13% |
| Decision Tree | 73.77% | 67.65% | 82.14% | 74.19% | 74.40% |
| **Random Forest** | **91.80%** | **87.10%** | **96.43%** | **91.53%** | **95.78%** |
| XGBoost | 86.89% | 79.41% | 96.43% | 87.10% | 93.07% |

###  Best Model

**Random Forest** achieved the strongest overall performance.

Key results:

- **Accuracy:** 91.80%
- **Precision:** 87.10%
- **Recall:** 96.43%
- **F1-Score:** 91.53%
- **ROC-AUC:** 95.78%

The high recall indicates that the model correctly identified a large proportion of observations belonging to the heart disease class.

---

##  Explainable AI with SHAP

To improve model interpretability, **SHAP (SHapley Additive exPlanations)** was applied to the selected Random Forest model.

SHAP helps explain how individual features contribute to machine learning predictions.

### Global Explanation

The SHAP summary plot provides an overall view of feature contributions across the testing dataset.

It helps identify:

- Which clinical features have the greatest influence on predictions.
- How feature values influence model output.
- The direction and magnitude of feature contributions.

### Feature Importance

Mean absolute SHAP values were calculated to produce an overall ranking of feature importance.

This provides a simplified view of which clinical variables have the greatest influence on the Random Forest model.

### Individual Explanation

An individual patient SHAP explanation was also generated.

The SHAP waterfall plot demonstrates how individual clinical features contribute toward or away from the model's prediction for a specific patient.

This provides **case-level interpretability** in addition to global model explanations.

---

##  Project Visualizations

### Model Performance Comparison

The project includes a visual comparison of the four machine learning models based on Accuracy, F1-Score, and ROC-AUC.

**File:** `model_performance_comparison.png`

### SHAP Summary Plot

Provides a global explanation of feature contributions across the testing dataset.

**File:** `shap_summary_random_forest.png`

### SHAP Feature Importance

Shows the overall ranking of features based on their mean absolute SHAP values.

**File:** `shap_feature_importance.png`

### Individual Patient Explanation

Shows the contribution of individual features to a specific patient prediction.

**File:** `individual_patient_shap.png`

---

## Project Structure

```text
MedExplain-XAI/
│
├── MedExplain-XAI.ipynb
├── model_results.csv
├── model_performance_comparison.png
├── shap_summary_random_forest.png
├── shap_feature_importance.png
└── individual_patient_shap.png

