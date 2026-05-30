---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-south-german-credit-data/
---

# South German Credit Data

## Key Takeaways

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
The 
<a href="https://archive.ics.uci.edu/dataset/522/south+german+credit" target="_blank">
South German Credit Dataset
</a> contains funded retail credit applications. Key takeaways are:
</p>
<ul>
  <li>Gini Coefficient, Information Value (IV), and Weight-of-Evidence (WoE) are helpful measures for classification modelling.</li>
  <li>Hierarchical Clustering of features can identify related features.</li>
  <li>Current and recent credit performance are the most powerful predictors of default risk.</li>
  <li>XGBoost performs best out of the 10 models assessed.</li>
</ul>
</div>

## Data
The [South German Credit Dataset](https://archive.ics.uci.edu/dataset/522/south+german+credit) contains 1,000 examples of funded retail credit applications with a bad rate of 30%. The 20 features span product (3), financial (3), behavioural (3), and borrower (11) characteristics. This is an updated dataset from the older German Credit Data.

**Product Features**
1. **duration** (months) - loan duration
2. **purpose** (categorical) - loan purpose
3. **instalment_rate** (categorical) - instalment amount band

**Financial Features**
4. **amount** (float) - loan amount
5. **savings** (categorical) - savings band
6. **status** (categorical) - checking account amount band

**Behavioural Features**
7. **credit_history** (categorical) - credit history
8. **number_credits** (categorical) - number of credits
9. **other_instalment_plans** (categorical) - other loans

**Borrower Features**
10. **age** (years) - customer age
11. **employment_duration** (categorical) - employment duration
12. **present_residence** (categorical) - residence duration
13. **other_debtors** (categorical) - guarantor
14. **people_liable** (categorical) - number of borrowers
15. **housing** (categorical) - owner/renter
16. **job** (categorical) - job title
17. **telephone** (binary) - telephone
18. **personal_status_sex** (categorical) - gender and marital status
19. **property** (categorical) - assets
20. **foreign_worker** (binary) - foreign worker

**Target**
21. **bad_flag** (float) - good/bad flag

## Analysis

### Exploratory Data Analysis

#### Response
The response variable indicates whether the granted loan defaults. The bar plot below shows the frequency of loan outcomes.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-count-goods-bads.png"
         alt="Distribution of Loan Outcome"
         width="400">
    <figcaption>Distribution of Loan Outcome (Good or Bad)</figcaption>
  </figure>
</div>

#### Features - Continuous

The stratified KDE (Kernel Density Estimate) plots below provide insight into the distribution of numerical features (`duration`, `amount`, `age`) stratified by the target variable (`bad_flag`). 

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-numeric-features.png"
         alt="Continuous Features"
         width="800">
    <figcaption>Continuous Features</figcaption>
  </figure>
</div>

Here are the key observations:

1. **Duration:** The distribution of `duration` indicates that longer durations are more common among bad credit risks. There is a noticeable peak for bad credit risks at higher durations, suggesting extended loan terms are associated with elevated risk.
2. **Amount:** Higher loan amounts are more common among bad credit risks. A noticeable peak at higher loan amounts suggests that larger requests carry a higher risk of default.
3. **Age:** Younger individuals represent a larger portion of bad credit risks. There is a clear peak at lower ages, indicating that younger applicants might be associated with higher credit risk.

Overall, the stratified KDE plots suggest that longer loan durations, higher loan amounts, and younger ages correlate with higher credit risk. These insights are useful for understanding the core characteristics of high-risk applications.

#### Features - Discrete

The list below highlights which specific categories within each discrete feature are associated with higher default rates:
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
- **telephone** → no telephone
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
The Gini coefficient and Information Values (IV) were calculated for each feature. The values are tabulated below:

| Feature | IV | Gini |
|---|---:|---:|
| status | 0.67 | 0.42 |
| credit_history | 0.29 | 0.25 |
| savings | 0.20 | 0.20 |
| duration | 0.18 | 0.22 |
| purpose | 0.17 | 0.22 |
| property | 0.11 | 0.17 |
| employment_duration | 0.09 | 0.16 |
| age | 0.09 | 0.15 |
| housing | 0.09 | 0.14 |
| amount | 0.07 | 0.14 |
| other_instalment_plans | 0.06 | 0.10 |
| personal_status_sex | 0.04 | 0.10 |
| foreign_worker | 0.04 | 0.03 |
| other_debtors | 0.03 | 0.05 |
| instalment_rate | 0.03 | 0.09 |
| number_credits | 0.01 | 0.05 |
| job | 0.01 | 0.04 |
| telephone | 0.01 | 0.04 |
| present_residence | 0.00 | 0.03 |
| people_liable | 0.00 | 0.00 |

### Feature Clustering
By applying hierarchical clustering to the features (using Ward's Linkage and Euclidean Distance) and cutting the distance at 12.4, the features form the clusters visualized below. Ultimately, 3 main clusters are identified, alongside 5 independent features that do not cluster with any others.

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-feature-clustering-dendrogram-cut-12.4.png"
         alt="Dendrogram"
         width="800">
    <figcaption>Dendrogram</figcaption>
  </figure>
</div>

### Correlation
The Spearman Rank correlation matrix below shows which feature pairs are highly correlated. The most correlated pairs are:
 - "Amount" and "Duration"
 - "Credit History" and "Number of Credits"
 - "Housing" and "Property"
 - "Telephone" and "Job"

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-correlation-matrix.png"
         alt="Correlation Matrix"
         width="800">
    <figcaption>Correlation Matrix</figcaption>
  </figure>
</div>

### Modelling Process
The dataset was split into training (70%) and test (30%) sets. There are 10 models evaluated:

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
The 10 models were trained and evaluated with no further hyperparameter tuning. The best performing models are:
 - XGBoost
 - LightGBM

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-gini.png"
         alt="Bar Plot of Gini"
         width="800">
    <figcaption>Bar Plot of Gini</figcaption>
  </figure>
</div>

<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/credit-data/credit-data-roc-curve.png"
         alt="ROC Curve"
         width="800">
    <figcaption>ROC Curve</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis can be found [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/credit-data/machine-learning-south-german-credit-data.ipynb).

## Codebase
The codebase to implement this analysis can be found [here](https://nbviewer.org/github/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/credit-data/machine-learning-south-german-credit-data.ipynb).


## Codebase
The codebase to implement this analysis can be found [here](https://colab.research.google.com/github/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/credit-data/machine-learning-south-german-credit-data.ipynb).

[← Back to Portfolio](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>