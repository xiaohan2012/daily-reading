# Revisiting Semi-Supervised Learning with Graph Embeddings

essentially, graph embedding + graph-based semi-supervised learning

- can incorporate input features
- applies to transductive and inductive settings

# related work

## graph-based semi-supervised learning

general form `\sum_{i \in L} l(y_i, f(x_i)) + \sum_{ij \in E} a_ij |f(x_i) - f(x_j)|^2`

- `L`: labeled node
- `y`: true label
- `f`: predicted label function
- `l`: loss function
  - different papers have different definition of `l`
- `a_ij`: weight between `i` and `j`

# model

objective function consists of two parts:

- unsupervised part using skip-gram
- supervised part using neural network, with input:
  - feature space
  - embedding (also as parameter): only for transductive setting

refer to **Figure 2**

## skip-gram: context sampling

corresponds to the skip-gram part:

- sampling positive and negative pairs
- positive mean node and its context
- negative means two-fold:
  1. node and non-context node
  2. nodes of different labels (to inject supervised information)
     - however, is it necessary because we have the supervised objective
- sampling controlled by two ratio parameters

two softmax layers:

1. one for skipgram
2. one for label prediction

## supervised part

a multi-layer neural network

## indutive learning

embedding is derived from a hidden layer with the input feature as input (Figure 2(b))


# questions

- objective function of skipgram: 
  - cross entropy in this paper?
  - sigmoid (in this paper) and softmax (are they equivalent somehow?)
- sampling procedure
  - why inject label information if there is supervised part?

# learned

- transductive vs inductive:
  - transductive: can only predict labels of instances observed in the graph
  - inductive: also able to predict *unseen* instances
- review of graph-based semi-supervised learning
- implementation of skipgram:
  - instead of enumerating all (word, context) pairs
  - we can also sample using some ratio parameter
  - for example with probability 0.2, we sample a positive pair (within context window) and with proba 0.08 we take a negative pair
- an architecture that incorporates supervised learning and input feature (trivial)
- this can be an ICML paper?