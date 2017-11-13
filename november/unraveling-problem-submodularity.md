# introduction

let's consider the unraveling process described previously, in which nodes attempt to leave once some of its neighbors left. 

- the details about the process is [here (first section)](http://193.166.24.212/anchored.pdf)

also, we consider the  edge addition version. 

the goal is to minimize the spread size by adding edges. 

# some notations

- $`S`$: set of edges added
- $`e=(u, v)`$: edge to add

the spread $`\delta(S)=\sum\limits_{X \in X_S} P(X) R(r, X)`$

- $`X_S`$: set of all possible cascades
- $`X`$: one cascade, (a set of time-stamped nodes)
- $`P(X)`$: probability of such cascade
- $`R(r, X)`$: number of nodes reachable from $`r`$ in $`X`$, where $`r`$ is a dummy node connected to all other nodes to initialize the cascade

## probability of a cascade

denote $`X`$ as $`\{(u_i, t_i)\}_{i=1,\ldots,n}`$, then

```math
P(X \mid G) = \prod_{i=1,\ldots,n}\begin{cases}\frac{1}{\deg_{t_i}(u_i)} \prod\limits_{t_j \in nt_G(u_i), t_j < t_i} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ if } t_i \neq \infty\\ \prod\limits_{t_j \in nt_G(u_i), t_j \neq \infty} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ otherwise} \end{cases}
```

$`nt_G(u_i)`$: all unique times that $`u_i`$'s neighbors are infected

# monotonicity check

we next check whether $`\delta(S)`$ is a monotonic function w.r.t. $`S`$. 

first, it's easy to see the bijection between $`X_S`$ and $`X_{S+e}`$

for each $`X \in X_{S+e}`$ and the corresponding $`X \in X_S`$ 

denote:

- the degree of node $`v`$ at time $`t`$ as $`\deg_t(v)`$

consider the following case:

$`v`$ is infected and $`t(v) - t(u) > 1`$:

in other words, infection via $`(u, v)`$ fails (because if it succeeds, then $`t(v) - t(u) = 1`$ holds)

denote:

- $`X^{'} = X-\{t(v)\}`$: all nodes with timatemps without $`(v, t(v))`$
- $`G^{'}=G+\{e\}`$: the new graph with $`e`$ aded

then according to the cascade definition

$`P(X \mid G) = P(X^{'} \mid G) P(t(v) \mid X^{'}, G)`$

$`P(X \mid G^{'}) = P(X^{'} \mid G^{'}) P(t(v) \mid X^{'}, G^{'})`$

it's obvious that $`P(X^{'} \mid G) = P(X^{'} \mid G^{'})`$ using the definition of cascade

next, we need to compare the remaining terms:

- $`P(t(v) \mid X^{'}, G) = \frac{1}{\deg_{t(v)}(v)} \prod\limits_{t \in nt_G(v), t < t(v)} (1 - \frac{1}{\deg_{t}(u_i)})`$
- $`P(t(v) \mid X^{'}, G^{'}) = \frac{1}{\deg_{t(v)}(v)} \prod\limits_{t \in nt_{G^{'}}(v), t < t(v)} (1 - \frac{1}{\deg_{t}(u_i) + 1})`$

and there are two cases to consider:

**first**, if $`nt_{G}(v) = nt_{G^{'}}(v)`$, then $`P(t(v) \mid X^{'}, G) < P(t(v) \mid X^{'}, G^{'})`$

**second**, if $`nt_{G}(v) \subset nt_{G^{'}}(v)`$, then 

```math
P(t(v) \mid X^{'}, G) =  \frac{1}{\deg_{t(v)}(v)} (1 - \frac{1}{\deg_{t(u)}(v)})  \prod\limits_{t \in nt_{G}(v), t < t(u)} (1 - \frac{1}{\deg_{t}(v) + 1})
```

note that $`nt_{G^{'}}(v) = nt_G(v) \cup \{t(u)\}`$

for the second case, it's possible that $`P(t(v) \mid X^{'}, G) > P(t(v) \mid X^{'}, G^{'})`$ because of the additional term $`(1 - \frac{1}{\deg_{t(u)}(v)})`$ in $`P(t(v) \mid X^{'}, G)`$

So $`P(X \mid G)`$ is neither monotone increasing or decreasing w.r.t the edges being added. 

## submodularity

