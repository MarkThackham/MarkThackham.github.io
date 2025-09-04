  ---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-pima-indians/
---

# Classification and SHAP Explanations

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Classification techniques applied to the 
<a href="https://archive.ics.uci.edu/dataset/34/diabetes" target="_blank">
Pima Indians Dataset
</a> assign probabilities a subject having diabetes. Key take-outs are:
</p>
<ul>
  <li>Nine classification techniques applied (including XGBoost and Logistic Regression)</li>
  <li>SHAP explanations show Glucose, Age and BMI strongly predict diabetes</li>
  <li>Hyperparameter tuning (Randomised CV and Optuna) increase predictiveness</li>
</ul>

</div>

## Data
The [Pima Indians Dataset](https://archive.ics.uci.edu/dataset/34/diabetes) contains data from female Pima Indians aged 21 years or older, a group with a notably high incidence of type 2 diabetes. The dataset contains nine columns: eight predictive features and one class label ("Outcome" or "diabetes"):

1. **Pregnancies** – Number of times pregnant  
2. **Glucose** – Plasma glucose concentration (2-hour oral glucose tolerance test)  
3. **Blood Pressure (BP)** – Diastolic blood pressure (mm Hg)  
4. **Skin Thickness** – Triceps skin fold thickness (mm)  
5. **Insulin** – 2-hour serum insulin (µU/ml)  
6. **BMI** – Body Mass Index (weight in kg/(height in m)²)  
7. **Diabetes Pedigree Function (DPF)** – A function measuring genetic predisposition to diabetes  
8. **Age** – Age in years  
9. **Outcome** – Binary label (0 = non-diabetic, 1 = diabetic)  

## Analysis

### Classification Techniques
These methods are used:
1. **XGBoost** – Gradient boosting algorithm optimized for speed and performance.  
2. **LightGBM** – Fast, memory-efficient boosting framework for large datasets.  
3. **Random Forest** – Ensemble of decision trees that improves stability and accuracy.  
4. **CatBoost** – Gradient boosting library with strong support for categorical features.  
5. **Logistic Regression** – Simple, interpretable linear model for binary classification.  
6. **Naive Bayes** – Probabilistic model based on Bayes’ theorem with independence assumptions.  
7. **K-Nearest Neighbours** – Instance-based method that classifies based on closest neighbors.  
8. **Support Vector Machine** – Finds optimal hyperplanes to separate classes with maximum margin.  
9. **Neural Network – Multilayer Perceptron** – Deep learning model that learns complex, non-linear patterns.  

### Hyperparameter Tuning Techniques
These methods are used to tune the XGBoost model:
1. **Randomised CV Grid Search** – Tests a random subset of hyperparameter combinations with cross-validation, making it faster than exhaustive grid search.  
2. **Optuna** – An advanced optimization framework that efficiently searches hyperparameters using techniques like Bayesian optimization.  

### SHAP Explanations
SHAP (SHapley Additive exPlanations) helps explain how machine learning models make predictions:  

- **Fair attribution** – assigns each feature a contribution to the prediction using Shapley values.  
- **Local + global insights** – explains both individual predictions and overall feature importance.  
- **Clear visualization** – tools like beeswarm plots show how features push predictions up or down.  

SHAP explanations show Glucose, Age and BMI strongly predict diabetes.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/pima-indians/pima_indians-shap_beeswarm.png"
         alt="SHAP Beeswarm"
         width="350">
    <figcaption>SHAP Beeswarm Plot</figcaption>
  </figure>

  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/pima-indians/pima_indians-shap_feature_importance.png"
         alt="SHAP Feature Importance"
         width="350">
    <figcaption>SHAP Feature Importance</figcaption>
  </figure>
</div>

### Results

Receiver-Operator Characteristic (ROC) curves for all models, as asell   

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/pima-indians/pima_indians-roc_curve.png"
         alt="SHAP Beeswarm"
         width="350">
    <figcaption>Receiver-Operator Characteristic (ROC) Curves</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here] (https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/pima-indians/machine-learning-pima-indians.ipynb)

[← Back to Machine Learning](/machine-learning/)