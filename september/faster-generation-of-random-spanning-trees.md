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

after $`\tau_i`$, the steps inside $`D_i`$ is useless. 

for example, after $`\tau_i=j`$, $`k`$ steps are spent inside $`D_i`$, $`X_j, \ldots, X_{j+k}`$ and the chain leaves via edge some $`(u, u^{'}) \in C(D_i)`$. 

which means, after $`\tau_i`$, once we have entered $`D_i`$ through $`v`$, we can shortcut the $`X_j, \ldots, X_{j+k}`$ and immediately leave by some edge $`e \in C(D_i)`$, the question is how to compute:

$`\text{Pr}_v(e)`$

the probabiliy of leaving via edge $`e`$ if entering $`D_i`$ via $`v`$. 

denote the new chain as $`\~{X}`$

**lemma 7**: if we know $`P_v(e)`$, then it takes $`O(\phi mn)`$ to pre-process $`\~{X}`$ and $`O(l)`$ to process a chain $`\~{X}`$ of length $`l`$

proof idea: $`e`$ can be sampled in polynomial time. and it takes $`O(|V(D_i)||C(D_i)|)`$ to build the same table. $`|C(D_i)| \le \phi m`$ and $`|V(D_i)| \le n`$

**lemma 8**: given $`(\phi, \gamma)`$ decomposition and $`P_v(e)`$, we can find a random arborescence in $`O(m(\gamma + \phi n))`$ time. 

time decomposes into two parts:

- $`m\gamma`$: sum of cover time inside each $`D_i`$ (lemma 6)
- $`\phi mn`$: by fact 5

## computing $`P_v(e)`$

**lemma 9** we can compute an $`(1+\epsilon)`$-approximation of $`P_v(e)`$ in $`O(\phi m^2 \log 1/\epsilon)`$ time

basic idea: connection between random walk and eletrical network. 

construct graph $`D^{'}`$ such that:

- add $`u^{'}`$ to $`D`$
- a dummy node $`u^{*}`$ is added to $`D`$ (to replace $`(_, w^{'}) \in C(D)`$)
- connect $`(w, _) \in C(D)`$ to the dummy node $`u^{*}`$

then $`P_v(u, u^{'})`$ is the proba of random walk starting on $`v`$ that hits $`u^{'}`$ before $`u^{*}`$

**some magic behind**: $`P_v(e)`$ is equal to the voltage on $`v`$ if we set $`vol(u^{'})=1`$ and $`vol(u^{*})=0`$

solving this approximately uses $`O(|E(D^{'})|\log 1/\epsilon)`$ time. 

we have $`C`$ edges and $`k`$ $`D_i`$s. total time $`O(\sum_i |C||E(D_i^{'})|\log 1/\epsilon)=O(\phi m^2 \log 1/\epsilon)`$

note that $`|E(D^{'})|=|E(D)| + |C(D)| \le 2|E(D)|`$ (using **property 3** of the decomposition)

**lemma 10** given $`(\phi, \gamma)`$ decomposition and $`(1+\epsilon)`$-approximation of $`P_r(e)`$, we can generate a $`\delta`$-random arborescence in time $`O(m(\gamma + \phi n))`$ in expectation, where $`\epsilon \le \delta / mn`$

the distortion is at most $`(1+\epsilon)^{mn} \le 1+\epsilon mn \le 1 + \delta`$

## finding decomposition quickly

ball-growing technique in Leighton and Rao [15]: there exists a $`(\phi, O(1/\phi))`$ decomposition using time $`O(m)`$

if we set $`\phi=1/n^{1/2}`$, then running time is $`O(m^2/\sqrt{n} \log 1/\delta)`$

# $`O(m/\sqrt{n} \log 1/\delta)`$ time