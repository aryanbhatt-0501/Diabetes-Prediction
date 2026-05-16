# 🩺 Diabetes Prediction with Machine Learning

A supervised classification pipeline that predicts the onset of Type 2 diabetes using the **Pima Indians Diabetes Dataset**. Compares **Logistic Regression** and **Linear Discriminant Analysis (LDA)** with full EDA, leakage-free preprocessing, model evaluation, and coefficient-based feature importance.

---

## 📊 Results

| Model | Accuracy | F1 Score | AUC |
|---|---|---|---|
| Logistic Regression | ~78% | ~0.67 | ~0.84 |
| Linear Discriminant Analysis | ~77% | ~0.66 | ~0.83 |

> Both models perform comparably. Logistic Regression edges ahead on AUC and offers cleaner probability calibration.

---

## 📁 Project Structure

```
diabetes-prediction/
├── diabetes_prediction_improved.ipynb   # Main notebook
├── diabetes_prediction.ipynb   # Practice notebook
├── diabetes.csv                # Dataset (Pima Indians, UCI)
├── requirements.txt            # Package dependencies
└── README.md
```

---

## 🔍 Notebook Sections

### 1. Imports & Setup
Reproducible environment with a fixed `random_state` throughout.

### 2. Exploratory Data Analysis
- **Correlation heatmap** — pairwise feature relationships, with `Glucose` showing the strongest correlation with outcome (r = 0.47)
- **Per-feature histograms** — class-separated distributions revealing separability
- **Boxplots by outcome** — median/spread comparison across diabetic vs. non-diabetic groups
- **Medical context** — physiological explanation of why Glucose, BMI, Age, and DiabetesPedigreeFunction are meaningful predictors

### 3. Preprocessing
- Stratified 80/20 train/test split
- `StandardScaler` **fit only on training data** — no data leakage

### 4. Model Training & Evaluation
- Logistic Regression (`max_iter=1000`)
- Linear Discriminant Analysis
- Confusion matrices, precision/recall/F1, and ROC curves with AUC for both models

### 5. Feature Importance
Coefficients extracted via `model.coef_` for both classifiers, ranked and visualised. Glucose, BMI, and DiabetesPedigreeFunction consistently rank highest — consistent with clinical literature.

---

## 🧬 Why These Features Matter

| Feature | Medical Relevance |
|---|---|
| **Glucose** | Primary biomarker for diabetes diagnosis. Fasting glucose ≥ 126 mg/dL meets WHO diagnostic threshold. |
| **BMI** | Proxy for adipose tissue. Obesity (BMI ≥ 30) drives insulin resistance via chronic inflammation. |
| **Age** | β-cell function declines with age; risk rises sharply after 45. |
| **DiabetesPedigreeFunction** | Quantifies genetic heritability — estimated at 40–80% for Type 2 diabetes. |
| **Insulin / BloodPressure** | Elevated fasting insulin reflects β-cell overcompensation; hypertension amplifies metabolic syndrome risk. |

---

## ⚙️ Setup & Usage

**1. Clone the repo**
```bash
git clone https://github.com/your-username/diabetes-prediction.git
cd diabetes-prediction
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Run the notebook**
```bash
jupyter notebook diabetes_prediction.ipynb
```

> The dataset (`diabetes.csv`) must be in the same directory as the notebook. It can be downloaded from [Kaggle](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database) or the [UCI ML Repository](https://archive.ics.uci.edu/ml/datasets/diabetes).

---

## 🧰 Tech Stack

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4+-orange?logo=scikit-learn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-2.1+-150458?logo=pandas&logoColor=white)
![seaborn](https://img.shields.io/badge/seaborn-0.13+-4c72b0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

---

## 📚 Dataset

**Pima Indians Diabetes Database**
- Source: National Institute of Diabetes and Digestive and Kidney Diseases
- 768 samples, 8 features, binary outcome (diabetic / non-diabetic)
- Originally from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/diabetes)

---
