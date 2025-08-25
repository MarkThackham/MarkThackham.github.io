---
title: "Machine Learning Details"
permalink: /machine-learning/machine-learning-pima-indians/
---

# Machine Learning Details

## Take Away


## Introduction
This notebook applies classification techniques on the [Pima Indians Dataset](https://archive.ics.uci.edu/dataset/34/diabetes) dataset.

The dataset originates from a study by the National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK). It contains data from female Pima Indians aged 21 years or older, a group with a notably high incidence of type 2 diabetes, making it a valuable resource for predictive modeling and health research 

It is widely used for binary classification tasks—predicting diabetes or no diabetes based on diagnostic and demographic input features

The dataset contains nine columns: eight predictive features and one class label ("Outcome" or "diabetes"):

1. **Pregnancies** – Number of times pregnant  
2. **Glucose** – Plasma glucose concentration (2-hour oral glucose tolerance test)  
3. **Blood Pressure (BP)** – Diastolic blood pressure (mm Hg)  
4. **Skin Thickness** – Triceps skin fold thickness (mm)  
5. **Insulin** – 2-hour serum insulin (µU/ml)  
6. **BMI** – Body Mass Index (weight in kg/(height in m)²)  
7. **Diabetes Pedigree Function (DPF)** – A function measuring genetic predisposition to diabetes  
8. **Age** – Age in years  
9. **Outcome** – Binary label (0 = non-diabetic, 1 = diabetic)  

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


[← Back to Machine Learning](/machine-learning/)