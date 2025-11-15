---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-sarimax-gdp/
---

# SARIMAX GDP

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Dataset 
<a href="https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand" target="_blank">
data
</a> contains things. Key take-outs are:
</p>
<ul>
  <li></li>
</ul>
</div>

## Data
The [Office of National Statistics](https://www.ons.gov.uk/) collate and estimate data 
<ul>
  <li>Gross Domestic Product (GDP) in  the  
  <a href="https://www.ons.gov.uk/economy/grossdomesticproductgdp/datasets/quarterlynationalaccounts" target="_blank">Quarterly National Accounts</a> </li>
  <li>Unemployment Rate (UnempRate) in  the  
  <a href="https://www.ons.gov.uk/employmentandlabourmarket/peopleinwork/employmentandemployeetypes/datasets/labourmarketstatistics" target="_blank">Labour Market Statistics</a> </li>
  </ul>
When merged by quarter, the dataset contains 218 examples of quarterly features spanning 1971Q1 to 2025Q2 (units in brackets):

1. **Quarter** (Date)
2. **Gross Domestic Product: chained volume measures: Seasonally adjusted £m** (Float)
3. **Unemployment rate (aged 16 and over, seasonally adjusted): %** (Float)


## Analysis

### Exploratory Data Analysis

#### Features
The response is GDP and we want a predictive timeseries model. SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous variables) is a time-series model that extends ARIMA (AutoRegressive Integrated Moving Average) by allowing seasonal patterns and by incorporating external predictors (exogenous variables) that influence the target series. It models both the internal dynamics of the series (AR, I, MA, seasonal terms) and the effect of outside factors to improve forecasting accuracy.

The avaliable data spans 1971Q1 to 2025Q2, with GDP and UnempRate plotted below.
<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/sarimax-gdp/sarimax_gdp-growth.png"
         alt="GDP_Timeseries"
         width="800">
    <figcaption>Gross Domestic Product</figcaption>
  </figure>
</div>

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/sarimax-gdp/sarimax_unemp-rate-growth.png"
         alt="UnemRate_Timeseries"
         width="800">
    <figcaption>Unemployment Rate</figcaption>
  </figure>
</div>

#### Augmented Dickey-Fuller Test
The Augmented Dickey-Fuller (ADF) test is a statistical test used to determine whether a time series is stationary or has a unit root (non-stationary). Stationarity means that the statistical properties of the series (mean, variance, autocorrelation) do not change over time. A stationary time series is easier to model and forecast because its behavior is consistent over time.

| Variable         | ADF Statistic | p-value   | Decision                               |
|------------------|--------------:|-----------|-----------------------------------------|
| GDPLevel         |    -0.322606  | 0.922241  | Do Not Reject H0 (Non-Stationary)       |
| GDPGrowth        |    -4.698089  | 0.000085  | Reject H0 (Stationary)                  |
| UnempRate        |    -2.267050  | 0.182815  | Do Not Reject H0 (Non-Stationary)       |
| UnempRateGrowth  |    -3.010712  | 0.033906  | Reject H0 (Stationary)                  |

The ADF test results indicate that both GDPLevel and UnempRate are non-stationary (fail to reject H0), while their growth rates (GDPGrowth and UnempRateGrowth) are stationary (reject H0). Therefore, we will model GDPGrowth as the response variable, using UnempRateGrowth as an exogenous predictor in the SARIMAX model.

#### Autocorrelation and Partial Autocorrelation
The Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots help identify the order of AR and MA components in time series models. The ACF plot shows the correlation of the series with its own lagged values, while the PACF plot shows the correlation of the series with its lagged values after removing the effects of shorter lags.

This is the ACF and PACF for GDP Growth
<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/sarimax-gdp/sarimax_gdp-acf-pacf.png"
         alt="ACF_PACF_GDP"
         width="800">
    <figcaption>Gross Domestic Product</figcaption>
  </figure>
</div>

This is the ACF and PACF for Unemployment Rate Growth.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/sarimax-gdp/sarimax_unemp-rate-acf-pacf.png"
         alt="ACF_PACF_UnempRate"
         width="800">
    <figcaption>Unemployment Rate</figcaption>
  </figure>
</div>

ACF and PACF for both GDP Growth and UnempRate Growth show significant spikes, suggesting the presence of AR() and MA() components.

## Modelling


### SARIMAX Model

The SARIMAX model is fitted to the training data (1971Q1 to 2018Q4) with the following parameters:
- Order: (1,0,1) - AR(1), I(0), MA(1)
- Seasonal Order: (2,0,0,4) - Seasonal AR(1), I(0), MA(1) with a seasonal period of 4 (quarterly data)
- Exogenous Variable: UnempRate Growth

### Results


## SARIMAX Results

### Model Setup

|                                  |                                  |
|----------------------------------|----------------------------------|
| **Dep. Variable:**               | GDPGrowth                        |
| **No. Observations:**            | 202                              |
| **Model:**                       | SARIMAX(1, 0, 1) x (2, 0, [], 4) |
| **Log Likelihood:**              | -437.565                         |
| **Date:**                        | Sat, 15 Nov 2025                 |
| **AIC:**                         | 889.130                          |
| **Time:**                        | 20:04:26                         |
| **BIC:**                         | 911.969                          |
| **Sample:**                      | 03-31-1975 to 06-30-2025         |
| **HQIC:**                        | 898.379                          |
| **Covariance Type:**             | opg                              |

---

### Coefficients

| Parameter         | Coef    | Std Err | z-value | P>|z| | [0.025 | 0.975]   |
|-------------------|--------:|--------:|--------:|------:|-------------------|
| intercept         | 0.6783  | 0.222   | 3.062   | 0.002 | 0.244 – 1.113     |
| UnempRateGrowth   | -0.1085 | 0.045   | -2.389  | 0.017 | -0.197 – -0.019   |
| ar.L1             | 0.8378  | 0.069   | 12.069  | 0.000 | 0.702 – 0.974     |
| ma.L1             | -0.3769 | 0.110   | -3.413  | 0.001 | -0.593 – -0.160   |
| ar.S.L4           | -0.6794 | 0.033   | -20.657 | 0.000 | -0.744 – -0.615   |
| ar.S.L8           | -0.2837 | 0.041   | -6.958  | 0.000 | -0.364 – -0.204   |
| sigma²            | 5.4503  | 0.155   | 35.179  | 0.000 | 5.147 – 5.754     |

---

### Diagnostics

| Test                        | Value     | Prob     |
|-----------------------------|-----------|----------|
| **Ljung-Box (L1) (Q):**     | 0.11      | 0.74     |
| **Jarque-Bera (JB):**       | 17012.62  | 0.00     |
| **Heteroskedasticity (H):** | 10.19     | 0.00     |
| **Skew:**                   | -2.16     | —        |
| **Kurtosis:**               | 48.79     | —        |



## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/sarimax-gdp/sarimax-gdp.ipynb)

[← Back to Machine Learning](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
