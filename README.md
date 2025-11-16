[README.md](https://github.com/user-attachments/files/23571425/README.md)
# Dementia Risk Prediction using Non-Medical Variables

## 📌 Project Overview

This project was developed for the **ModelX Hackathon** with the goal of building a binary classification model that predicts whether an individual is at **risk of dementia**, using **only non-medical variables**. The model outputs:

- A **probability score (0–100%)**
- A risk label: **"At risk"** or **"Not at risk"**

The project includes full data preprocessing, feature selection, model building, and evaluation phases, and follows responsible AI practices.

---

## 📂 Dataset

Data used was sourced from the **National Alzheimer’s Coordinating Center (NACC)**. The original dataset included hundreds of variables from multiple visit records.

Key preprocessing steps:
- Filtered to **latest visit per subject**
- Selected **non-medical variables** only
- Target variable: **`DEMENTED`** (1 = dementia, 0 = no dementia)

---

## 🔍 Features Used (Post Feature Engineering)

Final non-medical features included:
```
"NACCAGE", "SEX", "HISPANIC", "RACE", "EDUC", "MARISTAT",
"NACCLIVS", "INDEPEND", "RESIDENC", "HANDED", "INRELTO",
"INLIVWTH", "INVISITS", "INCALLS", "TOBAC30", "TOBAC100",
"SMOKYRS", "PACKSPER", "QUITSMOK", "ALCOCCAS", "ALCFREQ"
```

These cover demographics, social and living context, and lifestyle information such as smoking and alcohol history.

---

## 🧼 Data Preprocessing

- **Special codes** like `-4`, `-5`, `88`, `99` were replaced with `NaN`
- **Missing values** were imputed using `SimpleImputer` with the `mean` strategy
- **Categorical encoding** was applied using `LabelEncoder`
- **Standard scaling** was applied for models sensitive to feature magnitudes

---

## 🤖 Model Training & Evaluation

Several models were tested including Logistic Regression, Random Forest, and XGBoost. The final model selected was based on:

- Best **F1-Score**
- Good **Precision-Recall Balance**
- Ability to predict "At Risk" individuals with high sensitivity

### ✅ Evaluation Metrics

| Metric     | Value  |
|------------|--------|
| Accuracy   | ~89%   |
| Precision  | 0.81   |
| Recall     | 0.85   |
| F1-Score   | 0.83   |

### 🔍 Confusion Matrix
```
                Predicted
                0      1
Actual   0    25242   2280
         1    1739    9779
```

---

## 🎯 Risk Classification Threshold

From the precision-recall curve analysis:

- **Probability ≥ 60%**: **"At risk"**
- **Probability < 60%**: **"Not at risk"**

---

## 🧪 Predicting New Data

The notebook contains a `predict_dementia_risk()` function that:
- Accepts a dictionary of user input
- Preprocesses it similarly to training data
- Outputs probability and risk classification

Example:
```python
prob, label = predict_dementia_risk(input_dict=new_patient, ...)
print(f"Risk: {prob}% - {label}")
```

---

## 📁 Repository Structure

```
📄 dementia_risk_model_final.ipynb
📄 README.md
📄 T69_report.docx
📄 Data Dictionary.pdf
```

---

## 🚀 Future Improvements

- Deploy model via a web app using Streamlit or Flask
- Use SHAP/LIME for interpretability
- Incorporate feedback for continuous improvement
