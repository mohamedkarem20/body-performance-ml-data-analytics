# 🏋️‍♂️ Body Performance Analytics & Intelligent Classification System

A complete machine learning project analyzing the **Body Performance** dataset, aimed at understanding the relationship between physical fitness indicators and athletic performance, and building predictive models to classify performance level and forecast a physical capability.

**Course:** Introduction to AI and ML

**Team Members:**
- Muhammad Sleem (Team Leader)
- Eissam Mahmoud
- Hazem Khalid
- Muhammad Kamal
- Muhammad Karem

---

## 📋 Project Overview

This project works with the **Body Performance Dataset**, which contains measurements from individuals undergoing physical fitness evaluation (age, gender, body fat percentage, blood pressure, grip strength, flexibility, muscular endurance, etc.), and solves two main tasks:

1. **Classification** → Predicting the performance `class` (A / B / C / D)
2. **Regression** → Predicting `broad jump_cm` (broad jump distance)

The project goes beyond simply training models — it covers a full workflow starting from understanding the raw data and ending with comparing models and selecting the best one based on evidence.

---

## 🎯 Project Goals

- Understand physical fitness indicators and the relationships between them
- Build classification models to predict performance class
- Build regression models to predict physical capabilities
- Compare multiple machine learning algorithms and select the most suitable one

---

## 📁 Project Structure

```
AI Project/
├── Codes/                          # Project notebooks (several development versions)
│   ├── body_performance_ml_project.ipynb
│   ├── body_performance_ml_project_v2.ipynb
│   ├── body_performance_ml_project_v3.ipynb
│   ├── body_performance_ml_project_v3_named.ipynb
│   ├── body_performance_ml_project_v4.ipynb        # ← Latest / final version
│   └── body_performance_ml_project_enhanced.ipynb
│
├── ML EDA/                         # Detailed cell-by-cell explanation of the EDA
│   ├── ML EDA Final Version (Hazem).ipynb
│   ├── README_EDA_EXPLANATION_AR.md   # Full explanation in Arabic
│   └── README_EDA_EXPLANATION_EN.md   # Same explanation in English
│
├── EDA ALternative/
│   └── EDA.ipynb                   # Alternative version of the exploratory analysis
│
├── EDA-output/                     # All plots generated during the analysis
│   ├── correlation_heatmap.png
│   ├── distributions_histogram.png
│   ├── outliers_boxplot.png
│   ├── categorical_distributions.png
│   ├── scatter_plots.png
│   ├── cm_KNN_k=9.png
│   ├── cm_Decision_Tree.png
│   ├── cm_SVM_RBF.png
│   ├── cm_XGBoost.png
│   ├── cm_Neural_Network.png
│   ├── comparison_classification.png
│   ├── reg_eval_Linear_Regression.png
│   ├── reg_eval_Neural_Network.png
│   ├── reg_eval_XGBoost.png
│   ├── comparison_regression.png
│   ├── nn_classifier_learning_curve.png
│   ├── nn_epoch_learning_curve.png
│   ├── xgb_feature_importance.png
│   ├── xgb_regression_eval.png
│   ├── radar_constellation_map.png
│   └── speed_vs_accuracy.png
│
├── Data-set/
│   └── bodyPerformance.csv         # 13,394 rows × 12 columns
│
├── Dashboard/
│   ├── Body_Performance_Dashboard.html
│   └── BodyPerformance_Dashboard.html
│
└── Report-Presntation/
    ├── Body_Performance_ML_Project_Report.docx
    ├── Team_Project_Report.docx / .pdf
    ├── Body_Performance_ML_Presentation.pptx / .pdf
    └── Body_Performance_ML_Presentation_Updated.pptx
```

---

## 🗂️ Dataset Description

File: `Data-set/bodyPerformance.csv`
**Size:** 13,394 rows × 12 columns

| Column | Description |
|---|---|
| `age` | Age |
| `gender` | Gender (M/F) |
| `height_cm` | Height in centimeters |
| `weight_kg` | Weight in kilograms |
| `body fat_%` | Body fat percentage |
| `diastolic` | Diastolic blood pressure |
| `systolic` | Systolic blood pressure |
| `gripForce` | Grip strength |
| `sit and bend forward_cm` | Flexibility test |
| `sit-ups counts` | Number of sit-ups |
| `broad jump_cm` | Broad jump distance (regression target) |
| `class` | Performance class A/B/C/D (classification target) |

---

## 🔬 Methodology (Workflow)

1. **Understanding the raw data** — exploring columns and values
2. **Quality review** — missing values, duplicates, logical errors
3. **Selective cleaning** — removing only impossible values and duplicates, while keeping genuine outliers in performance metrics
4. **Distribution and relationship analysis** — histograms, correlation heatmap, scatter plots
5. **Feature engineering**
6. **Preparing data for modeling**
   - Merging classes B and C into a single class `BC` (since they overlap heavily in every metric), reducing the problem to three well-separated classes: A (high), BC (mid), D (low)
   - Removing outliers in blood pressure only (using the IQR rule), treating them as measurement noise, while keeping outliers in performance metrics since they represent real high-performing athletes
7. **Training baseline models**
8. **Testing the impact of engineered features**
9. **Cross-validation** and stability testing across different data splits
10. **Visual interpretation of results** and model comparison

---

## 🤖 Models Used

### Classification (Predicting Performance Class)
| Model |
|---|
| K-Nearest Neighbors (KNN) |
| Decision Tree |
| Support Vector Machine (SVM - RBF Kernel) |
| XGBoost Classifier |
| Neural Network (MLP) |

### Regression (Predicting Broad Jump Distance)
| Model |
|---|
| Linear Regression |
| Neural Network (MLP Regressor) |
| XGBoost Regressor |

---

## 🏆 Key Results

| Task | Models Trained | Best Performer |
|---|---|---|
| Classification | KNN, Decision Tree, SVM, XGBoost, Neural Network | **XGBoost / SVM (RBF)** |
| Regression | Linear Regression, Neural Network, XGBoost | **XGBoost Regressor** |

**Key Findings:**
- **XGBoost** led both tasks, benefiting from the regularization built into gradient boosting
- The **Neural Network** converged steadily with no signs of overfitting
- Epoch-tracking learning curves confirmed smooth learning for both classifiers and regressors
- **SVM (RBF)** remained a close rival to XGBoost on classification
- The most influential features were **grip force (gripForce)** and **sit-ups counts**

**Recommendations:**
1. Deploy XGBoost for production fitness classification and regression
2. Use the Neural Network as a secondary option where gradient boosting is unavailable
3. Collect richer training data and explore SHAP for model explainability
4. Consider ensemble stacking of XGBoost + Neural Network for peak performance

---

## 📊 Dashboard

The project includes an interactive HTML dashboard (`Dashboard/`) for visually exploring the analysis results without running any code.

---

## 📄 Reports & Presentations

The `Report-Presntation/` folder contains:
- The full project report (Word/PDF)
- The project presentation (PowerPoint/PDF)

---

## ⚙️ Setup & Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

### How to Run
1. Open one of the notebooks in `Codes/` (the latest and most complete version is `body_performance_ml_project_v4.ipynb`)
2. Make sure `Data-set/bodyPerformance.csv` exists at the relative path used in the code
3. Run the cells in order from top to bottom

---

## 📌 Note on Multiple Notebook Versions

The `Codes/` folder contains several development versions of the same project (v2, v3, v3_named, v4, enhanced) reflecting successive improvement stages. **The `v4` version is the latest and most complete.**

For a detailed, cell-by-cell explanation of the EDA logic, see:
- `ML EDA/README_EDA_EXPLANATION_AR.md` (Arabic)
- `ML EDA/README_EDA_EXPLANATION_EN.md` (English)

---

## ✅ Project Status

The project is complete across all stages: data cleaning, exploratory data analysis, model training, hyperparameter tuning, cross-validation, and visual evaluation.
