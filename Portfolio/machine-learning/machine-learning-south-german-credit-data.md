---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-credit-data/
---

# German Credit Data

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Dataset 
<a href="https://www.kaggle.com/datasets/kabure/german-credit-data-with-risk" target="_blank">
German Credit Data
</a> contains contains funded retail credit applications. Key take-outs are:
</p>
<ul>
  <li>take-out 1 → description 1</li>
  <li>take-out 2 → description 2</li>
  <li>take-out 3 → description 3</li>
  <li>take-out 4 → description 4</li>
</ul>
</div>

## Data
The [German Credit Dataset](https://www.kaggle.com/datasets/kabure/german-credit-data-with-risk) contains 1,000 examples of funded retail credit applications a bad-rate of 30%. The 20 features span: product (3); financial (3); behavioural (3); and borrower(11) features.

Product Features
1. **duration** (months) - loan duration
2. **purpose** (categorical) - loan purpose
3. **instalment_rate** (categorical) - instalment amount band

Financial Features
4. **amount** (float) - loan amount
5. **savings** (categorical)- savings band
6. **status** (categorical) - savings account amount band

Behavioural Features
7. **credit_history** (categorical) - credit history
8. **number_credits** (categorical) - number of credits`
9. **other_instalment_plans** (categorical) - other loans

Borrower Features
10. **age** (years) - customer age
11. **employment_duration** (categorical) - employment duration
12. **present_residence** (categorical) - residence duration
13. **other_debtors** (categorical) - guarantor
14. **people_liable** (categorical) - number borrowers
15. **housing** (categorical) - owner/renter
16. **job** (categorical) - job title
17. **telephone** (binary) - telephone
18. **personal_status_sex** (categorical) - gender and marital status
19. **property** (categorical) - assets
20. **foreign_worker** (binary) - foreign worker

Target
21. **bad_flag** (float) - good bad flag

## Analysis

### Exploratory Data Analysis

#### Response
The response is whether the granted loan defaults. The bar plot below shows the frequency of loan outcomes.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-count-goods-bads.png"
         alt="Distribution of Loan Outcome"
         width="800">
    <figcaption>Distribution of Loan Outcome (Good or Bad)</figcaption>
  </figure>
</div>

#### Features - Continuous

The stratified KDE (Kernel Density Estimate) plots below provide insights into the distribution of numerical features(`duration`, `amount`, `age`) stratified by the target variable (`bad_flag`). 

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-numeric-features.png"
         alt="Continuous Features"
         width="800">
    <figcaption>Continuous Features</figcaption>
  </figure>
</div>

Here are the key observations:

1. Duration
- The distribution of `duration` for both good and bad credit risks shows that longer durations are more common among bad credit risks.
- There is a noticeable peak for bad credit risks at higher durations, indicating that longer loan durations might be associated with higher credit risk.

2. Amount
- The distribution of `amount` for both good and bad credit risks shows that higher loan amounts are more common among bad credit risks.
- There is a noticeable peak for bad credit risks at higher loan amounts, suggesting that larger loan amounts might be associated with higher credit risk.

3. Age
- The distribution of `age` for both good and bad credit risks shows that younger individuals are more common among bad credit risks.
- There is a noticeable peak for bad credit risks at lower ages, indicating that younger age might be associated with higher credit risk.

Overall, the stratified KDE plots suggest that longer loan durations, higher loan amounts, and younger ages are associated with higher credit risk. These insights can be useful for understanding the characteristics of high-risk loans and individuals.

#### Features - Discrete

The plots below show the relation between higher bad rate and each categorical feature.
- **status** → smaller balances or no checking account
- **credit_history** → past delays or critical account status
- **purpose** → repairs, business, domestic appliances
- **savings** → lower or unknown savings values
- **employment_duration** → shorter duration or unemployed
- **instalment_rate** → smaller instalment amount
- **personal_status_sex** → divorced/separated men
- **other_debtors** → applications with co-applicants
- **present_residence** → very little signal
- **other_instalment_plans** → bank or store card
- **housing** → owners
- **number_credits** → 6 or more
- **job** → very little signal
- **people_liable** → very little signal
- **telephone** → no
- **foreign_worker** → no

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-categorical-features.png"
         alt="Categorical Features"
         width="800">
    <figcaption>Categorical Features</figcaption>
  </figure>
</div>

## Modelling

### Univariate

### Correlation

### Modelling
The dataset is split into training (80%) and test (20%) sets.  There ar 10 models evaluated:

- XGBoost
- LightGBM
- CatBoost
- Random Forest
- Logistic Regression
- Naive Bayes
- K-Nearest Neighbours
- Support Vector Machine
- Neural Network (Multilayer Perceptron)
- Linear Discriminant Analysis

### Results
XXX

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-gini.png"
         alt="Bar Plot of Gini"
         width="800">
    <figcaption>Bar Plot of Gini</figcaption>
  </figure>
</div>

XXXX

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-roc-curve.png"
         alt="ROC Curve"
         width="800">
    <figcaption>ROC Curve</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/credit-data/machine-learning-german-credit-data.ipynb)

[← Back to Portfolio](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
