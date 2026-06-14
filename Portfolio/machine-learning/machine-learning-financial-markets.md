---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-financial-markets/
---

# Financial Markets - Indices and Returns

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Financial Index Data from <a href="https://uk.finance.yahoo.com/" target="_blank"> Yahoo Finance 
</a> can be downloaded into Python using the yfinance package. Investigating key stock market indicies from te USA, Europe and Asia, key take-outs are:
</p>
<ul>
  <li>aaaaaaa</li>
  <li>b</li>
  <li>c</li>
</ul>
</div>

## Data
The yfinance PYthon package can download data directly from [Yahoo Finance](href="https://uk.finance.yahoo.com/). Data from 1984 to 2026 for these indices have been downloaded and returns analysed:


## Discussion

## Selected Indices

## USA
* **S&P 500**: A market-capitalization-weighted index tracking 500 of the largest publicly traded companies in the United States.
* **Dow Jones**: A price-weighted index of 30 prominent blue-chip companies listed on US stock exchanges.
* **NASDAQ**: A technology-heavy index that includes many of the world's largest software, hardware, and internet companies.
* **Russell 2000**: A market-cap-weighted index that tracks the performance of 2,000 small-cap companies in the US.

## Europe
* **FTSE 100**: An index representing the 100 most highly capitalized companies listed on the London Stock Exchange.
* **DAX**: A blue-chip stock market index consisting of 40 major German companies trading on the Frankfurt Stock Exchange.
* **CAC 40**: A benchmark French stock market index that tracks the 40 most significant stocks among the 100 largest on the Euronext Paris.
* **Euro Stoxx 100**: A broad index tracking 100 blue-chip companies from across the Eurozone.

## Asia
* **ASX 200**: An index comprising the 200 largest companies listed on the Australian Securities Exchange by float-adjusted market capitalization.
* **Nikkei 225**: A price-weighted index for the Tokyo Stock Exchange, consisting of 225 large, blue-chip Japanese companies.
* **Hang Seng**: A free-float-adjusted market-capitalization-weighted stock market index in Hong Kong.
* **Shanghai Stock Exchange**: A benchmark index representing all stocks (A and B shares) traded on the Shanghai Stock Exchange.

## Time Series Data Characteristics

The analysis for each index is divided into two core components:

* **Price Index Data**:
    * **Long-term Growth**: Represents the raw index value, demonstrating growth trends over four decades.
    * **Non-Stationarity**: Displays non-stationary behavior, characterized by long-term trends and shifts in mean value over time.
    * **Drawdowns**: Clearly illustrates significant historical market events such as the 2000 Dot-com crash, 2008 Financial Crisis, and the 2020 COVID-19 pandemic.

* **Returns Data**:
    * **Stationarity**: Returns (percentage changes) are generally stationary, fluctuating around a consistent mean (usually close to zero), making them suitable for statistical modeling.
    * **Volatility Clustering**: Exhibits periods of high variance (erratic swings) followed by periods of relative stability (heteroskedasticity).
    * **Fat Tails**: Shows a tendency for extreme events to occur more frequently than predicted by a normal (Gaussian) distribution, indicating higher tail risk.

## Results

USA

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA S&P 500.png" alt="S&P 500 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA S&P 500.png" alt="S&P 500 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_USA S&P 500.png" alt="S&P 500 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA Dow Jones.png" alt="Dow Jones Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA Dow Jones.png" alt="Dow Jones Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_USA Dow Jones.png" alt="Dow Jones Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA NASDAQ.png" alt="NASDAQ Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA NASDAQ.png" alt="NASDAQ Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_USA NASDAQ.png" alt="NASDAQ Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_USA Russell 2000.png" alt="Russell 2000 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_USA Russell 2000.png" alt="Russell 2000 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_USA Russell 2000.png" alt="Russell 2000 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>


Europe

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe FTSE 100.png" alt="FTSE 100 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe FTSE 100.png" alt="FTSE 100 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Europe FTSE 100.png" alt="FTSE 100 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe DAX.png" alt="DAX Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe DAX.png" alt="DAX Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Europe DAX.png" alt="DAX Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe CAC 40.png" alt="CAC 40 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe CAC 40.png" alt="CAC 40 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Europe CAC 40.png" alt="CAC 40 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Europe Euro Stoxx 100.png" alt="Euro Stoxx 100 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Europe Euro Stoxx 100.png" alt="Euro Stoxx 100 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Europe Euro Stoxx 100.png" alt="Euro Stoxx 100 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>


Asia  
<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia ASX 200.png" alt="ASX 200 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia ASX 200.png" alt="ASX 200 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Asia ASX 200.png" alt="ASX 200 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Nikkei 225.png" alt="Nikkei 225 Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Nikkei 225.png" alt="Nikkei 225 Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Asia Nikkei 225.png" alt="Nikkei 225 Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start; margin-bottom: 20px;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Hang Seng.png" alt="Hang Seng Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Hang Seng.png" alt="Hang Seng Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Asia Hang Seng.png" alt="Hang Seng Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Index_Asia Shanghai Stock Exchange.png" alt="Shanghai Stock Exchange Index" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Returns_Asia Shanghai Stock Exchange.png" alt="Shanghai Stock Exchange Returns" style="max-width: 100%; height: auto;"></figure>
  <figure style="flex: 1; text-align: center; margin: 0;"><img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/financial-markets/Histogram_Asia Shanghai Stock Exchange.png" alt="Shanghai Stock Exchange Returns Histogram" style="max-width: 100%; height: auto;"></figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://nbviewer.org/github/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/financial-markets/financial-markets.ipynb)

[← Back to Portfolio](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
