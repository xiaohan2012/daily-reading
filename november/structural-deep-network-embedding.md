# Structural Deep Network Embedding

main idea:

1. use autoencoder to tackle non-linearity challenge
2. 1st order similarity is captured via edges
3. 2sd order similarity is captured via neighboring nodes
   - to deal with sparsity   
   - **intuition**: nodes with similar neighbors should be similar to each other

# 

- first order proximity defined by edge weight $`s_{i,j}`$
- second order proximity by the similarity between neighbor vector $`\mathbb{s}_i`$ and reconstructed vector
  - this is the autoencoder part

## 2nd order proximity

goal: minimize reconstructed error of autoencoder

however, treat zero and non-zero entries corresponding to $`s_{i,j}`$ differently.
- controlled by parameter $`\beta`$

## 1st order proximity

minimize the distance between $`y_i^{(K)}`$ and $`y_j^{(K)}`$ if $`(i, j) \in E`$ 

- $`y_i^{(K)}`$: the inner most representaton of the auto-encoder


# optimization

- derivative w.r.t decoder params, $`\hat{W}^{(k)}`$ depends on $`L_{2nd}`$ and $`L_{reg}`$
- derivative w.r.t encoder params, $`W^{(k)}`$ depends on $`L_{2nd}`$, $`L_{reg}`$ and $`L_{1st}`$ 

## misc

- sigmoid is used for activation function
- pretraining is used, can we play with parameter initialization or train using residual network?
- table 3 gives the architecture
- for 20-newsgroup: tfidf is used and cosine similarity
  - kNN graph or?


# questions

- what's batch? edges or nodes?

# comments

- graph size is 80k maximum
- the time compleixty is quite large, we consider $`n`$ nodes and each node has maximum $`n`$ neighbors, (so quadratic, $`n^2`$?)

  