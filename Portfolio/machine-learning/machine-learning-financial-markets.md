---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-financial-markets/
---

# Financial Markets - Indices and Returns

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
The
<a href="https://www.kaggle.com/datasets/oktayrdeki/houses-in-london" target="_blank">
dataset
</a> contains 1,000 examples of prices for London houses. Key take-outs are:
</p>
<ul>
  <li>Square meters, neighbourhood, and property type the strongest predictors of house prices.</li>
  <li>House prices are critically dependent on location, with significant variations across different neighbourhoods.</li>
  <li>Property type also influences prices, with detached houses typically fetching higher prices.</li>
</ul>
</div>

## Data
The [London House Price Data](https://www.kaggle.com/datasets/oktayrdeki/houses-in-london) contains 1,000 examples of prices for London houses, together with 15 features:



### Results

These plots show the predicted vs actual prices for the three models on both the training and test sets.  The XGBoost model performs best, with predictions closely aligned to actual prices.


USA

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA S&P 500.png" alt="S&P 500 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA S&P 500.png" alt="S&P 500 Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA Dow Jones.png" alt="Dow Jones Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA Dow Jones.png" alt="Dow Jones Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA NASDAQ.png" alt="NASDAQ Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA NASDAQ.png" alt="NASDAQ Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA Russell 2000.png" alt="Russell 2000 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA Russell 2000.png" alt="Russell 2000 Returns" style="max-width: 100%; height: auto;"></figure>
</div>




Europe

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe FTSE 100.png" alt="FTSE 100 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe FTSE 100.png" alt="FTSE 100 Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe DAX.png" alt="DAX Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe DAX.png" alt="DAX Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe CAC 40.png" alt="CAC 40 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe CAC 40.png" alt="CAC 40 Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe Euro Stoxx 100.png" alt="Euro Stoxx 100 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe Euro Stoxx 100.png" alt="Euro Stoxx 100 Returns" style="max-width: 100%; height: auto;"></figure>
</div>



Asia

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia ASX 200.png" alt="ASX 200 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia ASX 200.png" alt="ASX 200 Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Nikkei 225.png" alt="Nikkei 225 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Nikkei 225.png" alt="Nikkei 225 Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Hang Seng.png" alt="Hang Seng Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Hang Seng.png" alt="Hang Seng Returns" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Shanghai Stock Exchange.png" alt="Shanghai Stock Exchange Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Shanghai Stock Exchange.png" alt="Shanghai Stock Exchange Returns" style="max-width: 100%; height: auto;"></figure>
</div>


## Codebase
The codebase to implement this analysis is [here](https://nbviewer.org/github/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/financial-markets/financial-markets.ipynb)

[← Back to Portfolio](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
