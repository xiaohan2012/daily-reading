# model 

- supervised component for 1st-order proximity
- unsupervised component for 2nd-order proximity

obj function: `reconstruction error + 1st order proximity + regularizer`
  - reconstruction is done via autoencoder architecture
  - 1st oder proximity: `|y_i - y_j|^2` (can use a different one)

- input `xi` for node `i`: the adjacency vector

# questions

- how to initialize the parameters?
  - (link)[https://datascience.stackexchange.com/questions/10926/how-to-deep-neural-network-weight-initialization]
  - [batch normalization](https://arxiv.org/abs/1502.03167)

# compared to LINE

- same: both preserves 1st and 2nd order proximity
- diff: a non-linear function to get the embedding instead of a linear one

# learned

most importantly:

- adding non-linearity using auto-encoder
- the result is impressive

- why preserving second order proximity? 
  - preserve global information (still vague, why?)
  - to fight the sparsity issue (in other words, if the graph is not sparse, no need for 2nd order proximity?)
- rethinking of 1st and 2nd order proximiy:
  - 1st-order: a node is similar to its neighbors
  - 2nd-order: a node predics all its neighbors
  - the term is still confusing
- deepwalk tends to preserve only 2nd-order proximity
- links indicate similarity but absence of links does not indicate disimilariy
  - asymmetry

for evaluation:

- another task: network reconstruction
  - decoder gives the reconstruction
- link prediction task:
  - hide a portion of observed links as test set and use the rest to train