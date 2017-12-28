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

- parameter sharing (no just lookup table): 
  - without it, it means linear memory consumption (as is in the lookup table case)
  - parameter sharing can act as regularization
- using node attributes
- inductive (infer embedding for unknown nodes, such as in evolving graphs) vs transductive (only embedding for nodes in the training set)

## neighborhood autoencoder method

main idea:

- learning encoder/decoder s.t. `decode(encode(s_i)) \approx s_i`
- `s_i` is the neighborhood vecctor

note that in this case, parameter is shared. 

example: 

**SDNE** KDD 2016

`s_i` is just from the adjacency matrix

**DNGR** AAAI 2016

[Deep Neural Networks for Learning Graph Representations](https://www.aaai.org/ocs/index.php/AAAI/AAAI16/paper/view/12423)


`s_i` is pointwise mutual information of two nodes co-occuring on random walks

**drawbacks**:

- scalability: because input dimension is `O(V)`, intractable for large graphs
  - can we use feature hashing for this


## neighborhood aggregation and convolutional encoders

- relies on node features/attributes
- generate embedding by aggragating information from neighbors

main idea (Algorithm 1):

- parameters to learn: `K` aggregation functions, combination function and `K` weight matrices
- with the above function, each node will have an hidden embedding `h_v^i` at level `i=1,\ldots,K`

1. initially at `i=1`, node's embedding is their attribute vectors
2. at `i>1`, node `v` first gather its' neighborhood embedding using the `i`th aggregation function and neighbors embedding from `i-1`the level, `h_u^{i-1}`, `u \in N(v)`
3. then its embedding `h_v^i` is computed by using combination function and weight matrix `W_i`.
4. interpolation can be added using `h_v^{i-1}`

the main differences lie in:

- aggregation functions: max-pooling, vector average, etc
- combination functions: concatenation, average, etc


## task specific supervision

just add another supervised term in the loss function

## different node/edge types

example: knowledge graph, user-content graph (recommender system), etc

common approaches:

- for node types: different encoders
- for edge types: type-specific matrices (bilinear form `z^T A_{\tau} z`), where `\tau` is the type index. 

for knowledge graph, the application can be predict missing relations. 

## multi-layer graphs

common approach: adding penalty `||z_i^{G_1} - z_i^{G_2}||^2`.

- however, if there are many layers, then this becomes quadratic. 

## strutural roles

example: barbell graph

interesting view of "proximity"

example methods:

- node2vec
- struct2vec
- graphwave








