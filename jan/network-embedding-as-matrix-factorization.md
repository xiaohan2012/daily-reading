# Network Embedding as Matrix Factorization: Unifying DeepWalk, LINE, PTE, and node2vec

# LINE

proof used the following:

- merge term `x_i^T y_j` into `z_{ij}`
- taking derivative and making it equal to 0 because of the minimization problem
- assuming value indpendence among all `z_{ij}` if embedding dimension is large

# PTE

essentially extension of LINE, which uses the same fatorimization method as LINE

factorizing over three bipartite graphs:

- word word
- word  document
- word label

note that:

- can be used a baseline for our extreme multi-label classification problem
- the learning is done on bipartite graphs


# Deep walk

factorization over `\log \sum_{r=1}{T} P^r D^{-1}`

where `T` is the window size and `P` is the transition probability. 

## effect on eigen values

as `T` increases, it smoothes out small eigen values while keeping large ones. 


haven't checked the proof

# node2vec

based second order random walk.

- second order means the probability dependson three nodes

