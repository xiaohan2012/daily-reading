# introduction

the unraveling process described by Francesco

# property

we consider edge addition version, the goal is to minimize the spread case (assuming some dummy node, $`r`$)

- $`S`$: set of edges added
- $`e=(u, v)`$: edge to add

the spread $`\delta(S)=\sum\limits_{X \in X_S} P(X) R(r, X)`$

- $`X_S`$: set of all possible cascades
- $`X`$: one cascade
- $`P(X)`$: probability of such cascade
- $`R(r, X)`$: number of nodes reachable from $`r`$ in $`X`$

## monotonicity

first, it's easy to see the bijection between $`X_S`$ and $`X_{S+e}`$

for each $`X^{'} \in X_{S+e}`$ and the corresponding $`X \in X_S`$

- if $`v`$ is infected
  - 
- if $`v`$ is not infected

**think about the above**

cannot take time into account because otherwise bijection is lost. 

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

