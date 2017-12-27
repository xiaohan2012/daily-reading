# Representation Learning on Graphs: Methods and Applications

# framework

(typical) components:

- encoder: map node to low-dim vector
- decoder: accepts a set of node embeddings and decodes user-specified graph statistics from these embeddings
  - typical example: edge and weights (node proximity)
- pairwise proximity measures: 
  - it might not be "pairwise", maybe a set of nodes
- loss function

example: Table 1

# direct encoding

## matrix factorization

- the general form of loss function : `||Z^T Z - S||_2^2`
- consists of embedding loopup table, so the trainable parameter is just the embedding table
- proximity function captures tradeoff between first-order and higher-order proximity



## random walk

- non-deterministic
- more flexible because of the stochasticity and exact definition of random walk.

**deepwalk vs node2vec**

- similarities: proximity models probability, stochastic and asymmetric
  - negative sampling used in node2vec
- difference: for node2vec, parameter `p`/`q` to bias towards BFS/ DFS (community/local stuctural)

**LINE**

uses probabilistic encoder/decoder, however using deterministic proximities. 

**HARP**

learning initial embeddings to improve the downstream embedding learning by:

- coasen graph into supernodes
- learn embedding for supernodes and use that as initialization values

# generalized encoder-decoder arch

- parameter sharing (no just lookup table)
- using node attributes
- inductive (infer embedding for unknown nodes, evolving graphs) vs transductive (only embedding for nodes in the training set)

## 