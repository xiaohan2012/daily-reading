

# deepwalk vs node2vec

- different style of random walk
- deepwalk: pure random
- node2vec: biased

# line vs deepwalk

why line gives better performance?

# grarep

- aims to capture global structural information
- define differnt adjacency matrix by the number of "hops".
  - for example, hop-2 network of `A`is defined by `A*A`.
- get embedding from each hop-k matrix
- concatenate the embedding

# Community Preserving Network Embedding

- preserves both local and community structure: modularized non-negative matrix fatorization
- objective function consists of:
  - NMF part (local structural info)
  - modularity (global community structure)
  - a term connecting the above two parts
    - via "community representation matrix" (embedding for each community)

in spirit with line, new adj matrix is defined to be 1st-order adj + 2nd-order adj
- 2nd-order adj: cosine similarity of neighborhood vectors

with theoretical guarantee (some math here)

# Non-transitive Hashing with Latent Similarity Components Mingdong

# Asymmetric Transitivity Preserving Graph Embedding Mingdong

