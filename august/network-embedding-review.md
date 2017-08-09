- deepwalk: word2vec style network embedding
  - context nodes: retrieved by random walk (similar to depth-first search)

- line: 1st order proximity + context node prediction
  - difference to deepwalk: definition of context words (neighbors not nodes visited by random walk)
  - in other words, breadth-first search and BFS even further

- GraRap: embedding for different k-step adjacency matrix
  - 1-step adj: the original one, 2-step adj: multiplication of 1-step adj, ...
  - for each adj, derive embedding using SVD
  - concat the embedding


# proximity matrices differ

- deepwalk: not explicit but of random walk
- line: 1st order + 2nd order
- GraRap: higher order (more global)
- asymmetric-transitivity: katz, rooted pagerank, etc

reminder: as we define different co-occurence matrices for word embedding tasks

- different reweighting schemes
- mentioned in [this note](https://github.com/xiaohan2012/daily-reading/blob/master/july/word-embedding-by-sanjeev-arora.md)

# definition of "context nodes" differ

related to skip-gram approach

- deepwalk: just random walk (DFS)
- line: neighbors (BFS)
- node2vec: biased random walk (between DFS and BFS)

# edge direction

undirected vs directed:

- directed: *asymmetric* transitivity preserving, two embeddings per node
- undirected: most graphs, one embedding per node

# 

# learning objectives

## community structure

a separate objective term for modularity: *Community Preserving Network Embedding*

## semi-supervised 

usually there is a context prediction part in the objective

- Revisiting Semi-supervised Learning with Graph Embedding (some nodes are labeled): two objectives
  - context prediction (deepwalk style)
  - using embedding and supervised loss using multi-layer neural network

## supervised

- author identification: objective have two parts
  1. context prediction (but context defined by meta-path)
  2. ranking on authors w.r.t some paper (hinge loss)

## unsupervised

many other papers

# non-linear architecture

*Structural Deep Network Embedding*

- 2nd order proximity modeled using autoencoder (non-linear)
  - node's recontructs its neighbors
  - in contrast with line
  - works for homogeneous graph



# graph heterogeneity

metapath2vec:

- skip-gram style but defines neighbors differently
- the neighbors are sampled under the guidance of metapath
  - random walk needs to follow the type sequence encoded by the metapath

Heterogeneous Network Embedding via Deep Architectures: 

- representational learning with network regularization
  - text/image networks with links
- conceptually different from skip-gram-style methods

cane

- main component: attentive model for text representation learning
- node representation varies by its neighbor
  - uses attentive pooling
  - might be good for link prediction
- don't know why it's a good paper

# comparison

|                       | learning problem | network heterogenous? | with text modeling? | methodology                                      |
|-------------------------------------------:---------------------:-:-------------------:--------------------------------------------------|
| author-identification | supervised       | yes                   | no                  | skip-gram + ranking loss                         |
| CANE                  | unsupervised     | no                    | yes                 | skip-gram + attentive pooling                    |
| deep-architecture     | unsupervised     | yes                   | yes                 | representation learning with network regularizer |
| revisiting            | semi-supervised  | no                    | yes                 | skip-gram + labeled signal                       |
| metapath2vec          | unsupervised     | yes                   | no                  | skip-gram with guided random walk                |
| pte                   | semi-supervised  | no                    | yes                 | skip-gram on transformed graphs                  |
| our                   | supervised       | yes                   | yes                 |                                                  |


# thinking

- encoder-decoder architecture on heterogenous network
  - one encoder and multiple decoders (one decoder for one type of neighbor)

