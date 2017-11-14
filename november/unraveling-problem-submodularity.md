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

denote:

- the degree of node $`v`$ at time $`t`$ as $`\deg_t(v)`$
- $`X = \{(u_i, t_i)\}_{i=1,\ldots,n}`$

then, 

`$``$math
P(X \mid G) = \prod_{i=1,\ldots,n}\begin{cases}\frac{1}{\deg_{t_i}(u_i)} \prod\limits_{t_j \in nt_G(u_i), t_j < t_i} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ if } t_i \neq \infty\\ \prod\limits_{t_j \in nt_G(u_i), t_j \neq \infty} (1 - \frac{1}{\deg_{t_j}(u_i)}) & \text{ otherwise} \end{cases}
`$``$

$`nt_G(u_i)`$: all unique times that $`u_i`$'s neighbors are infected

# monotonicity check

we next check whether $`\delta(S)`$ is a monotonic function w.r.t. $`S`$. 

first, it's easy to see the bijection between $`X_S`$ and $`X_{S+e}`$

for each $`X \in X_{S+e}`$ and the corresponding $`X \in X_S`$ 

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

$``$`$math
P(t(v) \mid X^{'}, G) =  \frac{1}{\deg_{t(v)}(v)} (1 - \frac{1}{\deg_{t(u)}(v)})  \prod\limits_{t \in nt_{G}(v), t < t(u)} (1 - \frac{1}{\deg_{t}(v) + 1})
`$``$

note that $`nt_{G^{'}}(v) = nt_G(v) \cup \{t(u)\}`$

for the second case, it's possible that $`P(t(v) \mid X^{'}, G) > P(t(v) \mid X^{'}, G^{'})`$ because of the additional term $`(1 - \frac{1}{\deg_{t(u)}(v)})`$ in $`P(t(v) \mid X^{'}, G)`$

So $`P(X \mid G)`$ is neither monotone increasing or decreasing w.r.t the edges being added. 

## submodularity

Cosider two sets of edges to add based on $`S`$

$`A=S \text{ and } B=S+\{f\}`$

and for an arbitrary edge $`e=(a, u)`$ and $`f=(b, v)`$. 

we want to check the relationship between 

$`f(A+\{e\}) - f(A)`$ and $`f(B+\{e\}) - f(B)`$

next we consider a speicific cascade $`X \in X_{A}`$. 

it can be seen that $`X \in X_{A+e}, X_B, X_{B+e}`$ as well and for each pair of $`\{X_A, X_{A+e}, X_B, X_{B+e}\}`$, there is bijective relation.

denote:

- $`X^{'}=\{(w, t) \in X \mid w \neq u, w \neq v\}`$
- graphs corresponds to adding $`S`$, $`S+e`$, $`S+\{e, f\}`$, $`S+f`$ as $`G, G_e, G_{ef}, G_f`$ respectively.

and we need to consider:

$`\Delta_f(S, e, f) = P(X \mid G_e) - P(X \mid G) - (P(X \mid G_{ef}) - P(X \mid G_f))`$

using the result from monotonicity part, we have the following:

$`P(X \mid G) = P(X^{'} \mid G) P(t_u \mid G) P(t_v \mid G)`$

and simiarly for other terms. 

note that for brevity, we denote $`P(t_u \mid X^{'}, G)`$ by $`P(t_u \mid G)`$. 


**lemma**: $`P(X^{'} \mid G) = P(X^{'} \mid G_e) = P(X^{'} \mid G_{ef}) = P(X^{'} \mid G_f)`$

**lemma**: $`P(x_u \mid G_{ef}) = P(x_u \mid G_{e})`$, where $`e=(a, u), f = (b, v)`$ and $`u \neq v`$

then using the above lemmas

`$``$math
\Delta_f(S, e, f) = P(X^{'} \mid G) (P(t_u \mid G_e) P(t_v \mid G_e) - P(t_u \mid G) P(t_v \mid G) - (P(t_u \mid G_{ef}) P(t_v \mid G_{ef}) - P(t_u \mid G_f) P(t_v \mid G_f)))
`$``$
removing the common factor $`P(X^{'} \mid G)`$, we have:

`$``$math
\Delta_f(S, e, f) \propto P(t_u \mid G_e) P(t_v \mid G) - P(t_u \mid G) P(t_v \mid G) - P(t_u \mid G_e) P(t_v \mid G_f) + P(t_u \mid G) P(t_v \mid G_f)) 
`$``$
by grouping the first two and last two terms, we have:


`$``$math
\begin{aligned}
  \Delta_f(S, e, f) & \propto \left[P(t_u \mid G_e) - P(t_u \mid G)\right] P(t_v \mid G) - \left[P(t_u \mid G_e) - P(t_u \mid G)\right] P(t_v \mid G_f)\\
  & = \left[P(t_u \mid G_e) - P(t_u \mid G)\right] \left[P(t_v \mid G) - P(t_v \mid G_f)\right]
\end{aligned}
`$``$

using the monotonicity propert, the function is neither submodular or supermodular. 

if the non-monotonicity proof is wrong, what to think next:

- what if $`u = v`$?

