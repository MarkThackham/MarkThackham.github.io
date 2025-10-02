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

Only the square metres, neighbourhood, and property type features are retained for modelling, with neighbourhood and property type one-hot encoded into binary features.

## Modelling

### Models
Three models are trained:
1. Linear Regression (square metres, neighbourhood, and property type)
2. Linear Regression (square metres, square metres squared, neighbourhood, and property type)
3. XGBoost (square metres, neighbourhood, and property type)

### Results

These plots show the predicted vs actual prices for the three models on both the training and test sets.  The XGBoost model performs best, with predictions closely aligned to actual prices.

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-OLS.png"
         alt="Cyclical Days" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Days</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-OLS2.png"
         alt="Cyclical Hours" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Hours</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/london-houseprice/london-house-price-XGBoost.png"
         alt="Cyclical Months" style="max-width: 100%; height: auto;">
    <figcaption>Cyclical Encoding - Months</figcaption>
  </figure>

</div>

This table shows the RMSE and R² for the three models on both the training and test sets.  The XGBoost model performs best, with the lowest RMSE and highest R² on both sets.

| Model   | Split |  RMSE    |   R²    |
|---------|-------|----------|---------|
| OLS     | Train | 203,923  | 0.9471  |
| OLS     | Test  | 196,788  | 0.9471  |
| OLS2    | Train | 203,134  | 0.9475  |
| OLS2    | Test  | 200,161  | 0.9452  |
| XGBoost | Train |  44,327  | 0.9975  |
| XGBoost | Test  |  58,683  | 0.9953  |

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/london-houseprice/machine-learning-London House Data.ipynb)

[← Back to Machine Learning](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
