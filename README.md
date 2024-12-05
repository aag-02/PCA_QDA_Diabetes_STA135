# PCA_QDA_Diabetes_STA135

This project focuses on predicting the onset of diabetes in female Pima Indians using historical medical data. The dataset, sourced from the `mlbench` package in R, consists of medical diagnostic measurements from women of Pima Indian descent. This analysis aims to explore diabetes prevalence and its predictors within this high-risk group.

---

## Dataset Overview
The Pima Indians Diabetes dataset includes:
- **8 Predictor Variables**: Medical measurements such as glucose levels, BMI, blood pressure, and more.
- **1 Target Variable**: Indicating the presence of diabetes.

The dataset was converted from R to a CSV file for analysis in Python.

### Data Challenges
- **Missing Data**: Biologically implausible zero values were found in several columns, likely representing missing data.
  - Sparse columns (e.g., `glucose`, `mass`, `pressure`) were imputed with median values.
  - Columns with extensive zeros (`triceps`, `insulin`) underwent iterative imputation for better accuracy.

### Key Findings from Data Exploration
- **Correlations**: Glucose and BMI showed strong correlations with diabetes outcomes.
- **Class Imbalance**: A higher proportion of non-diabetic cases compared to diabetic ones.
- **Feature Distributions**: Higher glucose and BMI levels were observed in diabetic individuals.

---

## Methodology
### 1. Principal Component Analysis (PCA)
PCA was employed to reduce dimensionality while preserving data variability:
- **Standardization**: Features were standardized to avoid bias from varying scales.
- **Component Selection**:
  - Retained components explaining ~80% of variance.
  - Used cumulative explained variance, scree plots, and parallel analysis to determine the optimal number of components.
- **Results**:
  - The first three components were selected as they captured meaningful patterns while avoiding noise.

### 2. Quadratic Discriminant Analysis (QDA)
QDA was chosen for classification due to the dataset’s nonlinear relationships:
- **Feature Preparation**: Used the retained principal components as inputs.
- **Model Evaluation**:
  - Split data into training (70%) and testing (30%) subsets.
  - Applied stratified 5-fold cross-validation for generalizability.

---

## Results
### PCA Findings
- **Explained Variance**: The first three principal components explained 61% of variance, balancing statistical robustness and data representation.
- **Loadings**: Component loadings provided insights into variable contributions to variance.

### QDA Performance
- **Accuracy**: 73.16% on the test dataset.
- **Cross-Validation**: Average accuracy of 73.5% with a standard deviation of 1.4%.
- **Confusion Matrix**:
  - True Positives: 46 diabetic cases correctly identified.
  - True Negatives: 123 non-diabetic cases correctly identified.
  - Sensitivity: 57.5%
  - Specificity: 81.46%

The model showed a tendency to prioritize specificity over sensitivity, which could be critical in medical contexts where false negatives are more impactful.
