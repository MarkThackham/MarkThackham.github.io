---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-london-houseprice/
---

# London House Price Prediction

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Dataset 
<a href="https://www.kaggle.com/datasets/oktayrdeki/houses-in-london" target="_blank">
London House Price Data
</a> zzz. Key take-outs are:
</p>
<ul>
  <li>zz</li>
  <li>zz</li>
  <li>zz</li>
</ul>
</div>

## Data
The [London House Price Data](https://www.kaggle.com/datasets/oktayrdeki/houses-in-london) contains 1,000 examples of prices for London houses, together with 15 features:

1. **Neighborhood** (Categorical)  
2. **Bedrooms** (Integer)  
3. **Bathrooms** (Integer)  
4. **Square Meters** (Integer)  
5. **Building Age** (Years, Integer)  
6. **Garden** (Binary: 0 = No, 1 = Yes)  
7. **Garage** (Binary: 0 = No, 1 = Yes)  
8. **Floors** (Integer)  
9. **Property Type** (Categorical)  
10. **Heating Type** (Categorical)  
11. **Balcony** (Binary: 0 = No, 1 = Yes)  
12. **Interior Style** (Categorical)  
13. **View** (Categorical)  
14. **Materials** (Categorical)  
15. **Building Status** (Categorical)  
16. **Price** (Integer, Currency)  

## Analysis

### Exploratory Data Analysis

#### Response
The response is house price. The histograms below shows the distribution of house prices, which is right-skewed.  A log transformation normalises the distribution.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-histogram.png"
         alt="Distribution of House Prices"
         width="800">
    <figcaption>Distribution of House Prices</figcaption>
  </figure>
</div>

#### Features

The plot shows the distribution of house prices by neighbourhood.  Neighbourhoods vary widely in price, with some areas (e.g., Chelsea, Westminster) having significantly higher prices than others (e.g., Shoreditch, Greenwich).

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-neighborhood.png"
         alt="Distribution of House Prices by Neighbourhood"
         width="800">
    <figcaption>Distribution of House Prices by Neighbourhood</figcaption>
  </figure>
</div>

The plot below shows the relationships between the 14 remaining features and house price. 

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-features.png"
         alt="Relation between Features and House Price"
         width="800">
    <figcaption>Relation between Features and House Price</figcaption>
  </figure>
</div>

Feature importance is assessed using the R² from univariate, with square metres, neighbourhood, and property type being the most important features.  

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-rsq.png"
         alt="Feature Importance"
         width="800">
    <figcaption>Feature Importance</figcaption>
  </figure>
</div>


## Modelling

### Preparation
Machine learning models need categorical features numerically encoded.  Cyclical encoding accounts for features that repeat in cycles (like hour of day). For example, Hour 0 and Hour 23 are close in time, which cyclic encoding reflects. Cyclical encoding maps a periodic feature \( v \ = the value (e.g., 0–23 for hours)) with period \( N \ = the total number of categories (e.g., 24 for hours) ) onto a circle:

$$
x_{\sin} = \sin\left(\frac{2\pi v}{N}\right)
$$

$$
x_{\cos} = \cos\left(\frac{2\pi v}{N}\right)
$$

The below plots show the cyclical encoding for DayOfWeek, Hour and Month.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-days.png"
         alt="Cyclical Days" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Days</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-hours.png"
         alt="Cyclical Hours" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Hours</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-features-cyclic-months.png"
         alt="Cyclical Months" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Months</figcaption>
  </figure>

</div>

The Seasons (Spring, Summer, Autumn, Winter) and Holiday (Yes, No) categorical features are one-hot encoded into binary features.

### Modelling
The dataset is split into training (80%) and test (20%) sets.  The below plot shows RMSE for XGBoost models trained on individual features, displaying univariate predictive power.  

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-feature-rmse.png"
         alt="Bike Rentals Histogram"
         width="800">
    <figcaption>RMSE by Individual Feature</figcaption>
  </figure>
</div>

### Results
A final XGBoost model is trained on all features. The table below shows the RMSE and R² for both training and test sets, indicating good model performance without overfitting.

| Metric     |  Value |
|------------|-------:|
| Train RMSE | 169.56 |
| Test RMSE  | 198.06 |
| Train R2   |  0.9311 |
| Test R2    |  0.9001 |

The predicted vs residuals and predicted vs actual plots show good agreement between predicted and actual values, with no obvious patterns in the residuals.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-residuals-actual-vs-predicted.png"
         alt="Bike Rentals Histogram"
         width="800">
    <figcaption>Predicted vs Residuals and Predicted vs Actual Plots</figcaption>
  </figure>
</div>

These plots show the feature importance from the final XGBoost model, using both gain and SHAP values.  Temperature, Hour, and Solar Radiation are the most important features.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-shap-beeswarm.png"
         alt="SHAP Beeswarm"
         width="350">
    <figcaption>SHAP Beeswarm Plot</figcaption>
  </figure>

  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/seoul-bike-hire/seoul-bike-hire-count-shap-summary.png"
         alt="SHAP Feature Importance"
         width="350">
    <figcaption>SHAP Feature Importance</figcaption>
  </figure>
</div>



## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/seoul-bike-hire/machine-learning-seoul-bike-hire.ipynb)

[← Back to Machine Learning](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
