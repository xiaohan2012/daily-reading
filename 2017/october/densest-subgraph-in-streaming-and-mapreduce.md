# Densest Subgraph in Streaming and MapReduce

motivation: densest subgraph detection in the streaming setting

why streaming? graph is too big to store in memory. 

in the streaming model, input can be read sequentilly in a number of passes. 

the goal is to minimize the number of passes needed. 

# variants

- undirected
- directed
- large graph (contain at least $`k`$ nodes): NP-hard

# algorithm for undirected

"peeling" approach:

- the current set of nodes is $`S`$, initially $`S=V`$
- at each step, remove nodes with degree smaller than $`2(1+\epsilon)\rho(S)`$
  - $`\rho`$ controls the trade off between fast convergence and high density
  - if $`\rho`$ is large, it converges faster and tend to have lower density
- if $`\rho(S) > S_best`$, update $`S_best`$

notations:

- nodes to remove from $`S`$: $`A(S)`$

## theorem: approximation ratio

the algorithm gives $`2(1+\epsilon)`$-approximation. 

proof: refer to paper

## theorem: convergence ratio

the algorithm converges within $`O(\log_{1/\epsilon})`$

proof sketch: 

at each iteration, $`|A(S)| > \frac{\epsilon}{1+\epsilon} |S|`$

# optimization

## memory

node degree is recorded. it's essentially counting the freqeuncy that nods appear in edges. *min-count sketch* can be used

## mapreduce for distributed computation

assume there is a server that tracks the current $`S`$. 

initially, duplicate the edge $`(u, v)`$ to $`(v, u)`$ (undirected). 

three operations

- density calculating: just count the edges and edges (like word count)
- node degree: like term frequency count, term is node, document is edge
- node/egde removal: essentially a filter op, mark nodes to remove/removed by `$` and remove edges in which at least one endpoint is marked with `$`
  - need some global hash table?
