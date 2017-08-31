# Sparse Local Embeddings for Extreme Multi-label Classification, NIPS, 2015

given training data $`\{x_i, y_i\}`$

## training

- learn local embedding $`z_i`$ (of lower dimension) for each $`y_i`$ by building knn graph
  - objective function?
- learn regressor so that $`z_i \approx V x_i`$ (projecting $`x_i`$ into the lower dimensional space


## prediction

for each new $`x`$, project it by $`V x`$ and find its nearest neighbors from $`z_1, \ldots, z_n`$ (and find $`y`$ and take the average?)

this is slow because it requires a linear scan. 

speeding-up: cluster $`(x_i, y_i)`$ into clusters and treat each cluster as one training data point. thus, it reduces training data size. 

also, it uses an ensemble of clustering to fight the following issue:

- clustering is usually unsable for high dim data