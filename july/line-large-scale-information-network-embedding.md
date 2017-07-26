
- why existing methods are not scalable?
- how is scalability improved?

- should we add weight to context words
  - for example, words connected by a longer random walk path tends to be less similar than words connected by a shorter path?


# main contribution

- explicit objective function (compared to deepwalk)
  - first-order proximity: nodes connected by direct link are similar
  - second-order proximity: nodes sharing a lot of common neighbors are similar
- 

# model

goal: find an embedding that preserves both first-order and second-order proximity
  - first-order proximity
  - second-order proximity

## first order proximity

- reweighting -- global wise: `\hat{p}(i, j) = w_ij / \sum_ij w_ij`
- model 
  - logistic function: `p(i, j)=1 / (1 + exp(-ui uj))`
  - `O1 = KL(\hat{p}, p)`

note:

- idea similar to graph factorization

## second order proximity

- `p(i | j)=exp(ui uj) / \sum_k exp(uk uj)` (probability that word j predicts word i)
- `\hat{p}(i | j) = w_ij / \sum_k w_kj`
- `O2 = KL(\hat{p}, p)`

comparison to deepwalk:

- similarity:
  - objective function in same form: `\sum_{something} p(i | j)`
- difference: context words
  - deepwalk: via random walk
  - line: neighbours

comparison to 1st-order proximity:

- 1st: `w_ij` reweighted globally
- 2nd: `w_ij` reweighted row-wise

## getting embedding

in this paper, train O1 and O2 separately and concatenate them

future work: minimizes `O1 + O2` jointly

# edge sampling

## motivation

stochastic gradient descent is usually used, however, because of the different weights of each edge, gradients diverge, thus  finding a good learning rate is impossible. 

## solution

unfold each edge into multiple binary edges by the weight.

in other words, sample the edges by weight for each mini-batch

# difference between deepwalk and line

- deepwalk: applies random walk
  - implicity objective function (random walk is random)
  - second order proximity by *depth* first search
- line
  - explict obj function
  - second order proximity by *breadth* first search (more reasonable)


it claims edge weights present high variance which compromises performance (**why?**)

# questions

- for 2nd-order proximity: why not define a separate 2nd-order matrix and use the same method of 1st-order proximity?
  - one question: which similarity method to define 2nd-order matrix? dot-product? cosine similarity?
- how to interpret different reweighting schemes (global and column-wise)?


# learned

- one approach for network embedding: graph factorization (spectral embedding for example) using adjacency matrix
  - only preserves first order proximity
  - however, it does not capture *global structure*
- same and diff between deepwalk and line
  - line: addition of first order proximity
  - similar def of second order proximity
    - both predict context words
    - but context words are defined differently
- doubting deepwalk: why context nodes via random walk are similar nodes? (not very intuitive)
- copying with edge weight: why weights poses challenges for training using SGD
  - different gradients need different learning rates