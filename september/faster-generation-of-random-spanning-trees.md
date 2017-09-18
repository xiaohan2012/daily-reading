connection between electrical networks and random walk on graphs

$`\delta`$-random spanning tree: random spanning tree from distribution within multiplicative $`(1+\delta)`$ of uniform. 

- multiplicative $`(1+\delta)`$ of uniform: $`(1-\delta) / N \ge \text{Pr}(T) \le (1+\delta) / N`$




# intutition

think of broder's algorithm, 

- $`\Delta(mn)`$: edges in random walk, essentially cover time
- $`O(n)`$: edges used to construct the tree

this comparison indicates a lot of waste of edges. 

in practice, some regions are covered very quickly, and a lot of time are spent on them. how we avoid this?

one option is to **shortcut** the random walk, so that the easily covered regions are skipped once they are covered

# basic idea

1. identify subgraphs $`D_i, \ldots, D_k`$ s.t. each $`D_i`$ has relatively small cover time inside itself. 
2. based on the subgraphs, identify the cross edges $`C`$ that connect them, $`|C|`$ is much smaller
3. then, when we run the markov chain $`X`$, if subgraph $`D_i`$ is covered, then we shortcut $`X`$ by removing all trajectories of $`X`$ inside $`D_i`$
   - so that it directly transits to other subgraphs without staying inside $`D_i`$?

# $`(\phi, \gamma)`$-decomposition

$`(D_1, \ldots, D_k, S, C)`$

![](figs/faster-generation-partition-def.png)

- $`D_1, \ldots, D_K`$: subgraphs
- $`S`$: remaining nodes, $`V \setminus \cup_i V(D_i)`$
- $`C`$: crossing edges w.r.t $`D_i`$
- $`C(D_i)`$: edges in $`C`$ incident to $`D_i`$
- $`U(D_i)`$: nodes in $`D_i`$ that are incident to some edge in $`C`$

![](figs/faster-generation-partition-def.png)

comment:

1. make sure that number of cut-edges are small so that the super graph is sparse
2. makes sure each $`D_i`$ can be covered quickly by upper-bounding the diameter
   - can use the result by Aleliunas that the cover time is at most $`O(|E|\gamma)`$, where $`\gamma`$ is the diameter
3. $`D_i`$ is "denser" compared to $`C(D_i)`$
   - useful for proof of lemma 6 (let's see)

## properties

denote $`\tau`$ as the cover time, then 

**Fact 4**: $`E[\tau]=O(mn)`$, 

because $`\gamma \le n`$, using Aleliunas' result. 

denote:

-  $`Z`$: \#times that $`X`$ visits some edge in $`C`$
-  $`Z_i`$: \#times that $`X`$ visits some edge in $`E(D_i)`$

so $`\tau=\sum_i Z_i + Z`$

**Fact 5**: $`E[Z]=O(\phi mn)`$

- $`\tau_i`$: first time when we reach some node in $`U(D_i)`$ after $`D_i`$ is covered
- $`Z_i^{*}`$: \#times some edge in $`D_i`$ are traversed *until* $`D_i`$ is covered
  - equivalent to: the minimum edge traversal time in $`D_i`$ required to cover $`D_i`$


**lemma 6**:

$`E[Z_i^{*}]=O(|E(D_i) \gamma(D_i)|)`$

similar to Aleliunas' result but proof is different. because $`X`$ is short-cut. 


# algorithm

after $`\tau_i`$, 