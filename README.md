# 🚢 Titanic Survival Prediction — Logistic Regression

![Python](https://img.shields.io/badge/Python-3.13-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-orange)
![Accuracy](https://img.shields.io/badge/Accuracy-76%25-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## 📌 Project Overview

Binary classification project to predict whether a Titanic passenger survived or not, using **Logistic Regression**. The model was trained on cleaned Titanic data and achieves **76% accuracy** on the test set.

---

## 📁 Dataset

- **Source:** Titanic dataset (seaborn built-in)
- **Rows:** 775 (after cleaning)
- **Target:** `survived` (0 = No, 1 = Yes)
- **Class Balance:** ~59% Not Survived / ~41% Survived

---

## 🔧 Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.13 | Core language |
| Pandas | Data manipulation |
| Scikit-Learn | Model training & evaluation |
| Matplotlib / Seaborn | Visualization |

---

## 🗂️ Features Used

| Feature | Type | Description |
|---|---|---|
| `pclass` | Numeric | Passenger class (1, 2, 3) |
| `sex` | Encoded | female=0, male=1 |
| `age` | Numeric | Age in years |
| `siblings_spouses` | Numeric | # of siblings/spouses aboard |
| `parents_children` | Numeric | # of parents/children aboard |
| `fare` | Numeric | Ticket fare |
| `embarked_Q` | One-Hot | Embarked from Queenstown |
| `embarked_S` | One-Hot | Embarked from Southampton |

> ℹ️ `embarked` was one-hot encoded (not label encoded) to avoid introducing false ordinal relationships between ports.

---

## ⚙️ Workflow

```
Raw Data
   ↓
Drop irrelevant columns (class, who, adult_male, embark_town, alive, alone)
   ↓
Encode categorical columns (LabelEncoder for sex, get_dummies for embarked)
   ↓
Train-Test Split (80/20)
   ↓
StandardScaler
   ↓
Logistic Regression (max_iter=1000)
   ↓
Evaluate (Accuracy, Confusion Matrix, Classification Report)
   ↓
Feature Importance via Coefficients
   ↓
New Passenger Predictions
```

---

## 📊 Model Performance

| Metric | Class 0 (Not Survived) | Class 1 (Survived) |
|---|---|---|
| Precision | 0.81 | 0.70 |
| Recall | 0.81 | 0.70 |
| F1-Score | 0.81 | 0.70 |
| **Accuracy** | | **76%** |

### Confusion Matrix

```
                Predicted 0    Predicted 1
Actual 0            77              18
Actual 1            18              42
```

---

## 🔍 Feature Importance (Coefficients)

| Feature | Coefficient | Impact |
|---|---|---|
| `sex` | -1.11 | 🔴 Strongest — males had much lower survival |
| `pclass` | -0.91 | 🔴 Higher class number = lower survival |
| `age` | -0.56 | 🔴 Older passengers less likely to survive |
| `siblings_spouses` | -0.40 | 🟡 Larger family = lower survival |
| `embarked` | -0.17 | 🟡 Minor effect |
| `parents_children` | -0.04 | ⚪ Negligible |
| `fare` | +0.07 | 🟢 Higher fare = slightly better survival |

---

## 🧪 Sample Predictions on New Passengers

| Passenger | Survived | Survival % |
|---|---|---|
| 1st class female, age 29 | ✅ Yes | 95.6% |
| 3rd class male, age 22 | ❌ No | 11.0% |
| 2nd class female, age 15 | ✅ Yes | 82.3% |
| 1st class male, age 45 | ❌ No | 41.3% |
| 3rd class female, age 8 | ❌ No | 48.3% |
| 2nd class male, age 35 | ❌ No | 34.1% |
| 1st class female, age 60 | ✅ Yes | 81.5% |
| 3rd class male, age 30 | ❌ No | 11.0% |
| 2nd class male, age 25 | ❌ No | 32.6% |
| 3rd class female, age 18 | ✅ Yes | 68.6% |

> 📌 Key insight: `sex` and `pclass` were the dominant survival factors — consistent with the historical "Women and children first" evacuation protocol.

---

## 💡 Key Learnings

- Logistic Regression works well for binary classification with interpretable coefficients
- One-hot encoding is critical for nominal categorical variables (vs label encoding)
- Even a 1st class male had only 41% survival probability — class alone wasn't enough
- 3rd class female child was borderline (48.3%) — highlights class inequality on the Titanic


---

## 👤 Author

**Vikas Ajay Vishwakarma**
BSc IT | Aspiring Data Scientist
🔗 [GitHub](https://github.com/codewithvikas96-ui)
