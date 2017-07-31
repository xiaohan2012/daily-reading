# spectral graph theory part 1

[video](https://www.youtube.com/watch?v=01AqmIU9Su4&t=3046s)

# eigen values: perspective 1

another way to denote the kth smallest eigen value of matrix `M`:

`\lambda_k =  min_x (x^T M x / x^T x)`

s.t. `x` is orthnogonal to the previous `k-1` eigen vectors. 

# eigen values: perspective 2

`\lambda_k =  min_{k-dim space S} max_{x in S} (x^T M x / x^T x)`

this decouples the dependency among eigen vectors

in this view, if a graph has at least `k` connected components.

then subspace `S` can be `a_1 x_{C1} + ... + a_k x_{Ck}`

where for `x_{Ci}`, entries are 1 if it corresponds to a node in `ith` cluster and 0 otherwise.

then `\lambda_k = 0`. 

# largest eigen value `\lambda_n`

following perspective 2, the  min operator can be dropped because it works on n dimensional space and there is only one n dimensional space.

thus, the problem becomes a maximization problem.

in other words, it's the maximum-cut problem (without normalization).

it can be shown that `\lambda_n <= 2`.

- if a graph is bipartite, equality holds.
- however, the other direction does not hold.
  - e.g, a bipartite subgraph and another non-bipartite graph


# middle case: between 0 and `\lambda_n`

the smallest non-zero eigen value is the lower bound on the uniform sparsest cut
  - `\lambda_2 <= USC(G) <= \sqrt(8 \lambda_2) <= \sqrt(8 USC(G))`


uniform sparsest cut: min E(S, V-S) / (|S|x|V-S|)

interpretation:

- if this value is quite small, then the graph is easily separable



