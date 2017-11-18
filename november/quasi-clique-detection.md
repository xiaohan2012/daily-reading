# quasi clique detection based on core decomposition

**questions:**

what are the patterns for pseudo-clique?  


can we detect such pseudo-cliques?  
if we can detect them, can we determine how many edges to add in so that nodes in it increase core number by 1? (multi-edge case)


# one missing edge case

given a `n`-node quasi-clique with one edge `(1, n)` missing.

1. it's a `(n-2)`-core, 
2. `\degp(1)=\degp(n)=n-2` for other nodes, `2, \ldots, n-1`, `\degp` values are `n-3, n-4, \ldots, 0`

by adding an edge between `(1, n)`, the new `\degp` becomes `n-1, n-2, \ldots, 1, 0`

# `k` missing edge case

consider the graph `(a, c), (b, d), (b, c), (a, d)`, the `\degp` is

`2, 1, 1, 0`

compare it to 

`3, 2, 1, 0`

the hamming distance is 2, which is exactly the number of edges we need to add.

# number of edges to add

is just the hamming loss between the two `\degp` vectors