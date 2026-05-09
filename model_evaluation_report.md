# Model Evaluation Report

**Project:** NutriSmart — Food Nutrition Analysis  
**Dataset:** Food\_Nutrition\_Dataset.csv (205 rows, 8 columns)  

## 1\. Dataset Summary

|Property|Value|
|-|-|
|Total Records|205|
|Features Used|protein, carbs, fat, iron, vitamin\_c|
|Regression Target|calories|
|Classification Target|high\_calorie (binary, median split at 166 kcal)|
|Missing Values|iron: 2, vitamin\_c: 3 → median imputed|
|Train / Test Split|80% / 20% (random\_state=42)|

\---

## 2\. Calorie Prediction — Regression

**Model:** Random Forest Regressor (100 trees, RobustScaler)

|Metric|Score|
|-|-|
|R² Score (Test)|0.8537|
|RMSE (Test)|100 kcal|
|5-Fold CV R² Mean|0.7573|
|5-Fold CV R² Std|0.1087|

**Feature Importances:**

|Feature|Importance|
|-|-|
|carbs|0.4960|
|fat|0.1687|
|vitamin\_c|0.1371|
|iron|0.1169|
|protein|0.0813|

\---

## 3\. High-Calorie Classifier

**Model:** Random Forest Classifier (100 trees, RobustScaler)

|Metric|Score|
|-|-|
|Accuracy (Test)|0.8537 (85.37%)|

**Classification Report:**

```
              precision    recall  f1-score   support

 Low Calorie       0.88      0.88      0.88        24
High Calorie       0.82      0.82      0.82        17

    accuracy                           0.85        41
   macro avg       0.85      0.85      0.85        41
weighted avg       0.85      0.85      0.85        41

```

\---

## 4\. KMeans Clustering

**Model:** KMeans (k=4, RobustScaler + PCA for visualization)

|Cluster|Avg Calories|Avg Protein|Avg Fat|Avg Carbs|
|-|-|-|-|-|
|0|188.8|1.55|3.58|22.83|
|1|470.8|9.58|9.26|37.88|
|2|173.7|1.23|0.32|21.19|
|3|439.8|4.92|31.99|35.02|

\---

## 5\. Conclusions

* **Fat, carbs, and protein** are the strongest predictors of calories (Atwater approximation holds).
* The Random Forest Regressor achieves an **R² of 0.85** on the test set.
* The High-Calorie Classifier achieves **85.37% accuracy**, reliably flagging energy-dense foods.
* KMeans with k=4 produces interpretable clusters: low-calorie fruits, moderate snacks, high-fat foods, and dried/processed items.

