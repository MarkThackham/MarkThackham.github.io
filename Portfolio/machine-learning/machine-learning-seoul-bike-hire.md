---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-seoul-bike-hire/
---

# Seoul Bike Hire2

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Dataset 
<a href="https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand" target="_blank">
Seoul Bike Sharing Demand
</a> qqqq
</p>
<ul>
  <li>xx</li>
</ul>

</div>

## Data
The [Seoul Bike Sharing Demand Dataset](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand) contains hourly counts of bike rentals in Seoul across a full year, along with weather data (temperature, humidity, wind speed, visibility, dew point, solar radiation, rainfall, snowfall), temporal features (hour, date, season), and holiday / functional day indicators. It can be used to predict the number of bikes rented in a given hour, based on both environmental and calendar variables. The dataset contains 8,760 examples and 13 features (units in brackets):

1. **Date** (Date)
2. **Rented Bike** (Integer)
3. **Hour** (Integer)
4. **Temperature** (C)
5. **Humidity** (%)
6. **Wind speed** (m/s)
7. **Visibility** (10m)
8. **Dew point temperature** (C)
9. **Solar Radiation**	(Mj/m2)
10. **Rainfall** (mm)
11. **Snowfall** (cm)
12. **Seasons**	(Categorical)
13. **Holiday**	(Binary)
14. **Functioning Day**	(Binary)

## Analysis

### Exploratory Data Analysis

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-hour.png"
         alt="Cap1"
         width="700">
    <figcaption>Cap1</figcaption>
  </figure>
</div>


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

Receiver-Operator Characteristic (ROC) curves for all models, as well as the results for Optuna and Random Grid Search CV.   

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/pima-indians/pima_indians-roc_curve.png"
         alt="SHAP Beeswarm"
         width="350">
    <figcaption>Receiver-Operator Characteristic (ROC) Curves</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/pima-indians/machine-learning-pima-indians.ipynb)

[← Back to Machine Learning](/machine-learning/)