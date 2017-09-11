https://homes.cs.washington.edu/~tqchen/pdf/BoostedTree.pdf

- simpler model -> smaller variance in future predictions -> more **stable** prediction

# key elements of supervised machine learning

- mode:, e.g, 
  - linear regression
  - logistic regression: $`\frac{1}{1+e^{-\hat{y}}}`$ (for binary classification)

- parameters: $`\Theta`$, things we learn from data

- objective function: $`L(\Theta) + \Omega(\Theta)`$
  - $`L`$: training loss function, square/logistic/hinge loss
  - $`\Omega`$: regularization, $`l1`$, $`l2`$ norm, controls the complexity of models

- minimize **bias**: minimizing $`L`$ gives better fitting of training data, which is hopefully close the underlying (true) distribution
  - reminds me of *unbiased* estimator

- minimize **variance**: minimizing $`\Omega`$ gives simpler model, which has lower variance for prediction (or more stable)

logistic loss (two forms depending on space of $`y`$)

- if $`y \in \{-1, 1\}`$, then $`\log (1 + e^{-y f(x)})`$
- if $`y \in \{0, 1\}`$, then $`y \log (1+e^{-\hat{y}}) + (1-y) \log (1+e^{\hat{y}})`$

## examples

- ridge regression: $`\sum\limits_{i=1}^{n} ||y_i - w^Tx_i||^2 + \lambda ||w||^2`$
  - linear model, square loss, $`l2`$ regularization
- lasso regression: $`\sum\limits_{i=1}^{n} ||y_i - w^Tx_i||^2 + \lambda |w|`$
  - linear model, square loss, $`l1`$ regularization
- logistic regression: $`\sum\limits_{i=1}^{n} L_{logreg}(y_i, w^Tx_i) + \lambda ||w||^2`$
  - linear model, logistic loss, $`l2`$ regularization


# tree ensemble methods

advantages:

- invariant to scaling of inputs, no need to feature normalization
- learn higher order interactions between features (path in the tree)
  - for example, $`(is-male) and (age < 15) and (has-a-computer)`$ (3rd-order interaction)	

## in context of model and parameters

Model:

$`\hat{y} = \sum\limits_{k=1}{K} f_k(x)`$

- $`f_k`$ is the regression tree
- another perspective: $`f_k`$ is a function that takes in attributes and outputs score

Parameters: $`\Theta=\{f_1, \ldots, f_K\}, f_i \in \mathcal{F}`$, $`\mathcal{F}`$ all regression trees (function space)

## bias and variance perspective

model: $`\hat{y} = \sum\limits_{k=1}{K} f_k(x)`$

objective: $`\sum\limits_{i=1}^{n} l(y_i, \hat{y_i}) + \sum\limits_{k=1}^K \Omega(f_k)`$

common heuristics used for decision tree and correspondence to objective:

- split by information gain -- training loss $`\sum_i l(y_i, \hat{y_i})`$
- pruning: regularization defined by number of tree nodes
- max depth: constraint of size of $`\mathcal{F}`$
- smoothing on leaf values: $`l2`$ regularization on leaf values

in other words, *loss+regularization formula* applies to tree/function learning as well. 

# additive training (boosting)

[related to adaboost](../august/boosting.md)

idea: learn a list of predictors sequetially, each each predictor is learned such that the **residual** from previous rounds is minimized. 


notations:

- $`f_t(x_i)`$: $`t`$th predicion on $`i`$th example
- $`\hat{y}^{t}_i=\sum\limits_{i=1}^{t-1} f_{t-1}(x_1)`$: predictions accumulated from previous $`t`$ rounds
- in other words, $`\hat{y}^{t}_i = \hat{y}^{t-1}_i + f_t(x_i)`$

## goal

minimize the error at step $`i`$ :

$`\sum\limits_{i=1}^n l\left(y_i , \hat{y}^{(t-1)}_i + f_t(x_i) \right) + \Omega(f_t) + constant`$

if considering square loss:

![](figs/boosting-tree-residual.png)

## taylor expansion of loss

motivation: simpler form of the loss, easier to optimize?

![](figs/boosting-tree-taylor-expansion.png)

note:

- $`f(x + \Delta x)`$ corresponds to $`l(y_i, \hat{y}^{(t-1)}_i + f_t(x_i))`$
  - $`x \rightarrow \hat{y}^{(t-1)}_i `$
  - $`\Delta x \rightarrow f_t(x_i)`$

## new objective

![](figs/boosting-tree-new-objective.png)

**BP 23**

# questions

- why use boosting? and the form is different from adaboost?
- why use taylor expansion?


## example: 

http://blog.kaggle.com/2017/01/23/a-kaggle-master-explains-gradient-boosting/