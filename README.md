# Wine Quality Prediction Using Machine Learning

## Project Overview

This project develops a Machine Learning classification model to predict wine quality based on its physicochemical properties.

The project covers the complete Machine Learning workflow, including data preprocessing, exploratory data analysis, feature analysis, model training, model evaluation, feature importance analysis, model persistence, and prediction on new wine data.

---

## Problem Statement

Wine quality depends on several chemical properties such as acidity, alcohol content, density, sulphates, and chlorides.

The objective of this project is to analyze these properties and build Machine Learning classification models that can predict the quality score of wine.

---

## Dataset

The project uses combined red and white wine quality data.

### Dataset Summary

| Attribute                 | Details   |
| ------------------------- | --------- |
| Original Records          | 6,497     |
| Duplicate Records Removed | 1,179     |
| Final Records             | 5,318     |
| Input Features            | 11        |
| Target Variable           | `quality` |
| Missing Values            | None      |

### Features

The model uses the following physicochemical properties:

* Fixed Acidity
* Volatile Acidity
* Citric Acid
* Residual Sugar
* Chlorides
* Free Sulfur Dioxide
* Total Sulfur Dioxide
* Density
* pH
* Sulphates
* Alcohol

**Target Variable:** `quality`

---

## Data Preprocessing

The following preprocessing steps were performed:

1. Combined the red and white wine datasets.
2. Inspected the dataset structure and data types.
3. Checked for missing values.
4. Identified and removed duplicate records.
5. Separated input features and target variable.
6. Performed a stratified train-test split.
7. Applied feature scaling for algorithms that require standardized features.

The final dataset contained **5,318 unique records**.

---

## Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the characteristics of the dataset and relationships between physicochemical properties and wine quality.

The analysis included:

* Descriptive statistics
* Target variable distribution
* Correlation analysis
* Quality-wise feature analysis
* Outlier detection
* Skewness analysis
* Feature relationships

### Key Findings

* Wine quality was highly imbalanced across the dataset.
* Quality levels **5 and 6** represented the majority of observations.
* **Alcohol** showed the strongest positive correlation with wine quality.
* **Density**, **volatile acidity**, and **chlorides** showed negative relationships with wine quality.
* Quality levels **3, 4, and 9** had very few observations.

---

## Machine Learning Models

The following classification algorithms were trained and evaluated:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. Balanced Random Forest
5. Tuned Random Forest
6. K-Nearest Neighbors (KNN)
7. Support Vector Machine (SVM)

---

## Model Performance

The models were evaluated on the test dataset using classification accuracy.

| Model                  | Test Accuracy |
| ---------------------- | ------------: |
| Random Forest          |    **57.33%** |
| Tuned Random Forest    |        56.20% |
| Balanced Random Forest |        55.17% |
| SVM                    |        53.85% |
| Logistic Regression    |        53.38% |
| KNN                    |        50.66% |
| Decision Tree          |        45.11% |

The Random Forest model achieved the highest test accuracy among the models evaluated in this project.

---

## Random Forest Evaluation

The Random Forest classifier achieved:

* **Test Accuracy:** 57.33%
* **Weighted F1-Score:** approximately 0.55
* **Macro F1-Score:** approximately 0.27

The model performed comparatively better on the majority classes, particularly quality levels 5 and 6.

The model had difficulty identifying rare quality classes because of the significant class imbalance in the target variable.

---

## Feature Importance

Feature importance was extracted from the trained Random Forest model.

| Feature              | Importance |
| -------------------- | ---------: |
| Alcohol              |     0.1290 |
| Density              |     0.1001 |
| Volatile Acidity     |     0.0962 |
| Total Sulfur Dioxide |     0.0923 |
| Chlorides            |     0.0891 |
| Free Sulfur Dioxide  |     0.0882 |
| Sulphates            |     0.0863 |
| Residual Sugar       |     0.0832 |
| pH                   |     0.0832 |
| Citric Acid          |     0.0768 |
| Fixed Acidity        |     0.0755 |

According to the Random Forest model, **alcohol** was the most important feature among the available input variables.

---

## Model Persistence

The trained Random Forest model was saved using Joblib.

```python
import joblib

joblib.dump(rfc, "wine_quality_random_forest.pkl")
joblib.dump(scaler, "wine_quality_scaler.pkl")
```

The saved model and scaler are included in this repository.

---

## New Wine Prediction

The saved Random Forest model was successfully used to predict the quality of a new wine sample.

### Sample Input

| Feature              |  Value |
| -------------------- | -----: |
| Fixed Acidity        |    7.0 |
| Volatile Acidity     |   0.30 |
| Citric Acid          |   0.30 |
| Residual Sugar       |    2.5 |
| Chlorides            |  0.045 |
| Free Sulfur Dioxide  |   30.0 |
| Total Sulfur Dioxide |  110.0 |
| Density              | 0.9940 |
| pH                   |   3.20 |
| Sulphates            |   0.55 |
| Alcohol              |   10.5 |

### Prediction

**Predicted Wine Quality: 6**

---

## Project Workflow

```text
Data Collection
      ↓
Data Cleaning
      ↓
Duplicate Removal
      ↓
Exploratory Data Analysis
      ↓
Feature & Target Separation
      ↓
Train-Test Split
      ↓
Feature Scaling
      ↓
Model Training
      ↓
Model Evaluation
      ↓
Model Comparison
      ↓
Feature Importance
      ↓
Model Saving
      ↓
New Wine Prediction
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Joblib
* Jupyter Notebook

---

## Repository Structure

```text
Wine-Quality-Prediction-repo/
│
├── README.md
├── Wine_Quality_Analysis.ipynb
├── requirements.txt
├── wine_quality_random_forest.pkl
└── wine_quality_scaler.pkl
```

---

## Limitations

* The target variable is highly imbalanced.
* Rare quality classes contain very few observations.
* The models have limited ability to identify these rare classes.
* Test accuracy of the evaluated models remained below 60%.
* Wine quality can depend on factors that are not represented by the available chemical features.

---

## Future Improvements

Possible improvements include:

* Applying advanced techniques for handling class imbalance.
* Performing feature engineering.
* Testing additional boosting algorithms.
* Performing more extensive hyperparameter optimization.
* Exploring regression approaches for predicting quality scores.
* Using a larger and more balanced dataset.
* Deploying the trained model using Streamlit or Flask.

---

## Conclusion

This project demonstrates an end-to-end Machine Learning classification workflow for Wine Quality Prediction.

The workflow covered data cleaning, exploratory data analysis, preprocessing, model training, model evaluation, feature importance analysis, model saving, and prediction on new data.

Among the evaluated models, the Random Forest classifier achieved the highest test accuracy of approximately **57.33%**.

The analysis also highlighted the impact of class imbalance, particularly for rare wine-quality classes. Feature importance analysis identified **alcohol, density, volatile acidity, total sulfur dioxide, and chlorides** as important features used by the Random Forest model.

Overall, the project provides practical experience in applying Machine Learning classification techniques to a real-world dataset and building a complete reproducible Machine Learning workflow.

