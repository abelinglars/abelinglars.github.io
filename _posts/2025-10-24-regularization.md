---
layout: post
title: "L1 and L2 Regularization in Machine Learning"
date: 2025-10-24
toc: true
---

## What is Regularization
Machine Learning models are trained on training data and their performance
evaluated on test data. When models predict well on training data but worse on
test data, this is called **overfitting**. The model _remembers_ the training data
with its particularities of random variation, instead of finding a pattern
that generalizes to unseen data. {% include img.html src='overfitting_1.png' alt='Image showing overfitting' caption='Model fits training data well but is too complicated to be useful' %}
{% include img.html src='overfitting_2.png' alt='Model fit with test data' caption='Residualse are larger for test data than for training data' %}
To mitigate overfitting, one can use regularization during model training to
reduce model complexity and therefore make the model a bit less accurate on
training data but more generalizable across datasets.

{% include img.html src='overfitting_3.png' alt='Regularized, less complex model' caption='Regularization leads to a less complex model that has a higher loss on training data but generalizes better across datasets by capturing more generalizable patterns' %}

## How does it work?
Regularization works by adding a penalty term to the objective
function. The penalty is proportionate to the size of the weights and therefore
higher weights lead to a larger penalty term and a higher loss. When adjusting weights during trainings, lower values for the weights are preferreed as they lead to a lower loss. Lower weights
means that the model is less sensitive to changes in the predictor values and
therefore leads to more stable predictions across different datasets.

## Use cases
When we have a lot of parameters, say more than individual samples, then a good
way to reduce model complexity is to use Ridge regression to eliminate features
from the model. When we are trying to reduce the variance of our model (less overfitting).
In some cases feature selection.

## Types of Regularizations
### L1 (Lasso) Regularization
In Lasso (least absolute shrinkage) regularization we add the **sum of the
absolute values** of the weights as a penalty term and scale it by the lambda
paramater.
$$ \lambda*(\Sigma| \beta |) $$
### L2 (Ridge) Regularization
In ridge regression, we add the squared sum of the weights to the models objective function
$$ \lambda*(\Sigma\beta)^2 $$
## In practice
### How do we find the optimal lambda?
The lambda value determines the degree to which large coefficients are penalized. When it is 0, there is no penalty applied, but if it is to high, the coefficients will approach 0 and the model will underfit. The optimal value can be found using cross validation with different values for lambda.
