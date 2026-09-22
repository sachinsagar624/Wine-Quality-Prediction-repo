# Wine Quality Prediction using Machine Learning
## Project Overview
This project focuses on predicting wine quality using Machine Learning classification algorithms based on the chemical properties of wine.
The project follows a complete Machine Learning workflow, including data cleaning, exploratory data analysis, preprocessing, model training, evaluation, feature importance analysis, model saving, and prediction on new data.
---

## Dataset
The dataset contains chemical properties of red and white wines.

### Dataset Information
* Original records: 6,497
* Duplicate records removed: 1,179
* Final records: 5,318
* Input features: 11
* Target variable: `quality`
* Missing values: None

### Features
The dataset contains the following input features:
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

Target:----[ `quality`]


## Data Preprocessing
The following preprocessing steps were performed:
1. Combined the red and white wine datasets.
2. Checked the dataset structure and data types.
3. Checked for missing values.
4. Identified and removed duplicate records.
5. Separated features and target variable.
6. Performed stratified train-test splitting.
7. Applied StandardScaler for models requiring feature scaling.
The final dataset contained **5,318 unique records**.


## Exploratory Data Analysis
Exploratory Data Analysis was performed to understand the dataset and identify relationships between wine properties and quality.
The analysis included:
* Quality distribution
* Descriptive statistics
* Correlation analysis
* Feature relationships with wine quality
* Outlier detection
* Skewness analysis
* Group-wise analysis by wine quality

### Key Findings
* The target variable was highly imbalanced.
* Quality levels 5 and 6 contained most of the observations.
* Alcohol showed the strongest positive correlation with wine quality.
* Density, volatile acidity, and chlorides showed negative relationships with wine quality.
* Quality levels 3, 4, and 9 had very few observations.
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


## Model Performance
The models were evaluated using test accuracy.

| Model                  | Test Accuracy |
| ---------------------- | ------------: |
| Random Forest          |        57.33% |
| Tuned Random Forest    |        56.20% |
| Balanced Random Forest |        55.17% |
| SVM                    |        53.85% |
| Logistic Regression    |        53.38% |
| KNN                    |        50.66% |
| Decision Tree          |        45.11% |
The Random Forest classifier achieved the highest test accuracy among the models evaluated in this project.


## Random Forest Evaluation
The Random Forest model achieved:
* Test Accuracy: **57.33%**
* Weighted F1-score: approximately **0.55**
* Macro F1-score: approximately **0.27**

The model performed better on the majority classes, particularly quality levels 5 and 6.
However, it had difficulty predicting rare classes such as quality levels 3, 4, and 9 because of the highly imbalanced target distribution.

## Feature Importance
Feature importance was extracted from the Random Forest model.

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

## Model Saving
The trained Random Forest model was saved using Joblib.
joblib.dump(rfc, "wine_quality_random_forest.pkl")
The scaler was also saved:
joblib.dump(scaler, "wine_quality_scaler.pkl")
These files are included in this repository for model reuse.

## New Wine Prediction
The saved Random Forest model was tested with a new wine sample.

Example input:
Fixed Acidity: 7.0
Volatile Acidity: 0.30
Citric Acid: 0.30
Residual Sugar: 2.5
Chlorides: 0.045
Free Sulfur Dioxide: 30.0
Total Sulfur Dioxide: 110.0
Density: 0.9940
pH: 3.20
Sulphates: 0.55
Alcohol: 10.5
``

### Prediction
**Predicted Wine Quality: 6**


## Project Workflow
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

## Technologies Used
* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Joblib
* Jupyter Notebook

## Project Files
Wine-Quality-Prediction/
│
├── Wine_Quality_Analysis.ipynb
├── wine_quality_random_forest.pkl
├── wine_quality_scaler.pkl
└── README.md
```

## Limitations
The dataset contains a significant class imbalance. Because some wine-quality classes have very few observations, the model has limited ability to identify these rare classes.
The test accuracy of 57.33% also indicates that wine quality is difficult to predict accurately using only the available chemical properties.
---

## Future Improvements

Possible improvements include:
* Handling class imbalance using advanced sampling techniques.
* Trying advanced boosting algorithms.
* Hyperparameter optimization with suitable cross-validation.
* Feature engineering.
* Comparing regression-based approaches with classification.
* Using a larger and more balanced dataset.
* Deploying the model as a web application using Streamlit or Flask.
---
## Conclusion
This project demonstrates a complete Machine Learning classification workflow for Wine Quality Prediction, starting from data cleaning and exploratory analysis through model training, evaluation, feature importance analysis, model saving, and prediction on new data.
Among the evaluated models, Random Forest achieved the highest test accuracy of approximately **57.33%**.
The project also demonstrates the challenges caused by class imbalance and shows that rare wine-quality classes are more difficult for the model to predict.
Overall, this project provides practical experience in applying Machine Learning techniques to a real-world classification problem.
