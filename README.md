# Predicting Diabetes Risk Using Machine Learning

This project demonstrates the development, evaluation, and reflection on supervised learning models to predict diabetes risk based on physiological indicators. It was completed as a capstone project for Spring 2025.

**Author:** Jimena Ortiz

---

## Objectives

- Develop and compare machine learning models that classify diabetes risk using only 8 routinely collected health metrics.
- Explore the strengths and limitations of each approach, emphasizing clinical interpretability.
- Reflect critically on the implications of using predictive models in healthcare settings.

---

## Dataset Overview

**Source:** [Pima Indians Diabetes Dataset](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)  
- 768 patient records, all numeric features.
- Focuses on female Pima Indian patients, highlighting the importance of considering **population-specific data limitations**.

**Features:**
- Glucose
- Blood Pressure
- Skin Thickness
- Insulin
- BMI
- Diabetes Pedigree Function
- Age
- Pregnancies

**Target:**
- `Outcome`: 1 = Diabetes diagnosed, 0 = No diagnosis

**Why this dataset?**
> Its clean structure, accessibility, and relevance to clinical prediction tasks make it an excellent sandbox to examine how models learn physiological patterns.

---

## ⚙️ Preprocessing & Feature Engineering

- **Missing Values:** Zero values replaced with NaN and imputed with **median strategy** to maintain robustness against outliers.  
  > *Critical Insight:* While median imputation is practical, it risks introducing bias and masking true variance in patient data.
- **Scaling:** StandardScaler applied to ensure features contribute equally—a necessary step for distance-sensitive models.
- **Correlation Analysis:** Revealed strong Glucose correlation with diabetes diagnosis, informing model expectations and highlighting potential multicollinearity.

---

## Methodology & Models

Four classification algorithms were compared to surface strengths and trade-offs:

| Model                | Rationale                                                            |
|----------------------|-----------------------------------------------------------------------|
| Random Forest        | Handles nonlinearity, offers feature importance for interpretability |
| K-Nearest Neighbors  | Simple, distance-based, sensitive to scaling                         |
| Support Vector Machine | Effective with high-dimensional spaces and smaller datasets         |
| Logistic Regression  | Baseline probabilistic model, interpretable coefficients            |

**Evaluation Metrics:**
- Accuracy
- Precision
- Recall (Sensitivity)
- F1 Score
- ROC AUC

---

## Results & Interpretation

| Model               | F1 Score | ROC AUC |
|---------------------|----------|---------|
| **Random Forest**   | **0.75** | **0.84** |
| Logistic Regression | 0.71     | 0.81    |
| SVM                 | 0.68     | 0.79    |
| KNN                 | 0.65     | 0.77    |

- **Random Forest** demonstrated the best balance of sensitivity and precision—a critical factor in medical diagnosis where false negatives carry significant risk.
- **Feature Importance:** Glucose, BMI, and Age emerged as top predictors, aligning with established clinical knowledge.
- **PCA Visualization:** Showed partially separable clusters, validating that even 2 components retained meaningful variance.
- **Distribution Plots:** Highlighted clear thresholds in Glucose and BMI that clinicians might use as risk signals.

> *Unique Perspective:* Beyond numeric performance, Random Forest's ability to communicate feature contributions makes it a compelling choice for settings where model trust and transparency are non-negotiable.

---

## 🔍 Critical Reflection

This project underscored several important considerations:

**Strengths**
- Clean data and consistent preprocessing enabled reproducible results.
- Loop-based evaluation ensured fair, unbiased model comparisons.
- Visual tools (PCA, ROC, confusion matrix) supported interpretability.

**Limitations**
- The dataset’s narrow demographic limits external validity.
- No hyperparameter tuning—so reported metrics are conservative baselines.
- Median imputation, while effective, may not fully capture patient variability.

**Future Work**
- Integrate more diverse datasets to improve fairness and generalizability.
- Implement hyperparameter optimization pipelines.
- Build a clinician-facing dashboard to visualize individual risk scores.

---

## Ethical and Practical Implications

Machine learning models can play a transformative role in proactive healthcare, but they must be deployed thoughtfully:

- **Transparency:** Clinicians must understand why a model makes a given prediction.
- **Bias Awareness:** Algorithms trained on homogeneous populations can reinforce health inequities.
- **Complement, Not Replace:** Models should augment clinical judgment rather than override it.

> *Insight:* The goal is not to replace human expertise, but to equip it with data-driven foresight that can inform early interventions.

---

## How to Run

1. **Clone the repository:**

   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
