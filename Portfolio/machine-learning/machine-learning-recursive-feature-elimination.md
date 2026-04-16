---
title: "Machine Learning"
permalink: /machine-learning/machine-learning-recursive-feature-elimination/
---

# Recursive Feature Elimination - Titanic Data

## Take Away

<div style="background-color: #f5f5f5; padding: 15px; border-radius: 8px;">

<p>
Determining the subset of most important features is a key challenge. Recursive Feature Elimination is a structured manner to progressively reduce the feature set. Using the  
<a href="NEED TO INSERT LINK" target="_blank">
Titanic Data
</a> containing features of passengers and their survival. Key take-outs are:
</p>
<ul>
  <li>take out</li>
  <li>take out</li>
  <li>take out</li>
  <li>take out</li>
</ul>
</div>

## Data
The [Titanic Dataset](NEED TO INSET LINK) contains 891 examples of passengers with a 38% survival rate. After dropping Passenger ID, Name and Ticket, the remaining 8 features are:

1. **Pclass** (integer) - passenger class
2. **Sex** (integer) - passenger gender
3. **Age** (float) - passenger age
4. **SibSp** (integer) - number of siblings/spouses aboard
5. **Parch** (integer) - number of parents/children aboard
6. **Fare** (float) - passenger fare
7. **Cabin** (character) - passenger cabin number
8. **Embarked** (character) - embarkation port

Target
9. **Survived** (integer) - 1 if passenger survived, 0 otherwise

## Modelling

## Preprocessing
To prepare for modelling, the following is undertaken:
 - Cabin is converted to an indicator variable, 1 if cabin is assigned and 0 otherwise
 - Sex is binary encoded, 1 for female and 0 for male
 - Missing values for age are imputed by Pclass * Sex
 - Missing values for Embarked imputed by mode, and the resultant feature is weight-of-evidence encoded

### Baseline Model
A baseline XGBoost model is built using all features. The Gini is 83% (train) and 70% (test).

<div style="display: flex; justify-content: center; gap: 20px; align-items: flex-start;">

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/recursive-feature-elimination/recursive-feature-elimination-beeswarm.png"
         alt="Beeswarm Plot" style="max-width: 100%; height: auto;">
    <figcaption>Beeswarm Plot</figcaption>
  </figure>

  <figure style="flex: 1; text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/recursive-feature-elimination/recursive-feature-elimination-feature-importance.png"
         alt="Feature Importance Plot" style="max-width: 100%; height: auto;">
    <figcaption>Feature Importance Plot</figcaption>
  </figure>

</div>

### Recursive Feature Elimination
Recursive Feature Elimination starts with a model of all available features and removes the p least important features. The value p>1 can be set to any integer value (say 5, 10, 50, ...) but for this toy example p=1.

The process selects these features at each step:
['Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Fare', 'Embarked', 'CabinAssigned']
['Pclass', 'Sex', 'Age', 'SibSp', 'Fare', 'Embarked', 'CabinAssigned']
['Pclass', 'Sex', 'Age', 'Fare', 'Embarked', 'CabinAssigned']
['Pclass', 'Sex', 'Age', 'Embarked', 'CabinAssigned']
['Pclass', 'Sex', 'Age', 'CabinAssigned']
['Pclass', 'Sex', 'Age']
['Pclass', 'Sex']
['Sex']

### Results
The results produce a variable selection profile, that compare the test and train Gini for the number of selected features.  This profile can be used to assess the best trade-off for the number of features in the model.


<div style="display: flex; justify-content: center; align-items: flex-start;">
  <figure style="text-align: center; margin: 0;">
    <img src="https://raw.githubusercontent.com/MarkThackham/MarkThackham.github.io/main/Portfolio/machine-learning/recursive-feature-elimination/recursive-feature-elimination-profile.png"
         alt="Bar Plot of Gini"
         width="800">
    <figcaption>Bar Plot of Gini</figcaption>
  </figure>
</div>

## Codebase
The codebase to implement this analysis is [here](https://github.com/MarkThackham/MarkThackham.github.io/blob/main/Portfolio/machine-learning/recursive-feature-elimination/machine-learning-recursive-feature-elimination.ipynb)

[← Back to Portfolio](/machine-learning/)

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
