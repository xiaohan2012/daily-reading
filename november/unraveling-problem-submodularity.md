# introduction

the unraveling process described by Francesco

# property

we consider edge addition version, the goal is to minimize the spread case (assuming some dummy node, $`r`$)

- $`S`$: set of edges added
- $`e=(u, v)`$: edge to add

the spread $`\delta(S)=\sum\limits_{X \in X_S} P(X) R(r, X)`$

- $`X_S`$: set of all possible cascades
- $`X`$: one cascade, (a set of time-stamped nodes, or a *DAG*)
- $`P(X)`$: probability of such cascade
- $`R(r, X)`$: number of nodes reachable from $`r`$ in $`X`$

## probability of a cascade

denote $`X`$ as $`\{(u_i, t_i)\}_{i=1,\ldots,n}`$, then

$`P(X \mid G) = \prod_{i=1,\ldots,n}\begin{cases}\frac{1}{\deg_{t_i}(u_i)} \prod\limits_{t_j \in nt(u_i), t_j < t_i} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ if } t_i \neq \infty\\ \prod\limits_{t_j \in nt(u_i), t_j \neq \infty} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ otherwise} \end{cases}`$

$`nt(u_i)`$: all unique times that $`u_i`$'s neighbors are infected

## monotonicity

first, it's easy to see the bijection between $`X_S`$ and $`X_{S+e}`$

for each $`X^{'} \in X_{S+e}`$ and the corresponding $`X \in X_S`$ 

denote:

- $`e=(u, v)`$
- the degree of node $`v`$ at time $`t`$ as $`\deg_t(v)`$

there are the following cases:

1) **$`v`$ is infected**:

denote:

- $`X^{'} = X-\{(t(v))\}`$

then

$`P(X \mid G) = P(X^{'} \mid G) P(t(v) \mid X^{'}, G)`$

$`P(X \mid G + e) = P(X^{'} \mid G+e) P(t(v) \mid X^{'}, G+e)`$

it's obvious that $`P(X^{'} \mid G) = P(X^{'} \mid G+e)`$

next, we need to compare the remaining terms:

- $`P(t(v) \mid X^{'}, G) = \frac{1}{\deg_{t(v)}(v)} \prod\limits_{t \in nt(v), t < t(v)} (1 - \frac{1}{\deg_{t}(u_i)})`$
- $`P(t(v) \mid X^{'}, G+e) = \frac{1}{\deg_{t(v)}(v)} \prod\limits_{t \in nt(v), t < t(v)} (1 - \frac{1}{\deg_{t}(u_i) + 1})`$



in other words, infection via $`(u, v)`$ fails.

then, $`P(X^{'}) = P(X)(1-p(u \rightarrow v))`$

1.2)

2) **$`v`$ is not infected**:



**think about the above**


two subcases:

- (1) if there exists some of $`v`$'s neighbors $`\{u^{'}\}`$ are infected at the same time as $`u`$

$`P(X)=P(X - \text{ attempt  on } v \text{ at time } t(u)) \frac{\deg{v}_u-1}{\deg{v}_u}`$

and 

$`P(X^{'})=P(X^{'} - \text{ attempt  on } v \text{ at time } t(u)) \frac{\deg{v}_u}{\deg{v}_u}+1`$

- (2) no such node $`u^{'}`$ exists, then $`P(X^{'}) = P(X) \frac{\deg{v}_u-1}{\deg{v}_u}`$
  - $`\deg{v}_u`$ is the degree of node $`v`$ when $`u`$ is removed


in both cases, $`P(X^{'}) \ge P(e)P(X)`$

so $`\delta(S)`$ is monotonically decreasing

## submodularity


consider two sets $`S`$ and $`S+f`$, now we add edge $`e`$

simplest case: if for both $`e=(u, v)`$ and $`f=(x, y)`$, 

$`v(y)`$ is not attempted by nodes besides $`u(x)`$. this corresponds to the (2) case. 

