# Extreme Multi-label Loss Functions for Recommendation, Tagging, Ranking & Other Missing Label Applications, KDD 2016

# extreme multilabel learning vs traditional multilabel learning

- large label space
  - Wikipedia: more than a million tags/labels
- logarithmic time prediction, training at scale

- predicting relevant labels is more important than predicting irrelevant ones
  - because relevant labels are much fewer than irrelevant labels
- missing label problem
  - missing $`\neq`$ irrelevant
  - a challenge for training and evaluation
- a good prediction should capture infrequent (tail) labels

# overview 

contributions:

- a loss function
- a fast learning algorithm

propensity scored loss function: precision@k, nDCG@k: unbiased estimates (vs biased estimates)

# hamming loss is not good enough because

1. *relevant labels*: it gives equal importance to predict relevant and irrelevant labels (same penalty)
   - however, it's more important to predict the relevant ones
2. **missing label**: it treats missing label as irrelevant, which is not true
3. **tail labels**: they are harder to predict, need to give more importance on such label examples

counterparts:

- squareloss [17]
- recall [38]
- average discounted gain [26]

ground truth labels are missed **uniformly** at random

# propensity scored losses

## label notations

1. $`y^{*} \in \{0, 1\}^L`$: the ground truth label
1. $`y \in \{0, 1\}^L`$: the observed label
  - missing labels (1) are 0
1. $`\hat{y} \in \{0, 1\}^L`$: predictions

## propensity

probability of a label $`l`$ being observed  for data point $`i`$.

$`p_{il} = P(y_{il} = 1 \mid y_{il}^{*}=1)`$

$`P(y_{il} = 0 \mid y_{il}^{*}=1)=0`$ by convention (the case of mislabel)


## propensity scored loss functions

1. $`\mathcal{L}^{*}(y^{*}, \hat{y})`$: measuring the loss for $`\hat{y}`$ against ground truth $`y^{*}`$ (impossible in practice becaue $`y^{*}`$ is unobtainable)
1. $`\mathcal{L}(y^{*}, \hat{y})`$: measuring against observed ground truth

propensity scored loss functions:

1. decompose over labels
1. computed over only relevant labels

propensity scored version:

1. $`\mathcal{L}^{*}(y^{*}, \hat{y}) = \sum\limits^L_{l: y_l=1} \mathcal{L}^{*}_l(1, \hat{y}_l)`$
1. $`\mathcal{L}(y^{*}, \hat{y})=\sum\limits^L_{l: y_l=1} \mathcal{L}_l(1, \hat{y}_l) / p_l`$ ($`i`$ dropped for convenience)
   - **note**: the $`p_l`$ term

in this way, we value over relevant variables?

## theorems 

**4.1**: $`\mathcal{L}(y^{*}, \hat{y})`$ is an unbiased estimator for $`\mathcal{L}^{*}(y^{*}, \hat{y})`$.

this means we can use $`\mathcal{L}`$ as the loss function for a learning problem, instead of the unobtainable $`\mathcal{L}^{*}`$


# IR evaluation methods

https://web.stanford.edu/class/cs276/handouts/EvaluationNew-handout-6-per.pdf

- precision@k
- nDCG@k
- Hamming Loss