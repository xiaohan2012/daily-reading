# sampling steiner tree from transitive closure

# problem in general

sampling a steiner tree $`T`$ with probability proportional to $`\prod\limits_{e \in T} w(e)`$

we can easily adapt our current problem (from `\exp^{\sum\limits_{e \in T} c(e)}`) plugging in `w(e) = \exp^{-c(e)}`

# algorithm overview

sampling an steiner tree can be done in the following steps:

1. construct a transitive closure $`G^{'}`$ on original graph $`G`$
2. sample a spanning tree $`T^{'}`$ from $`G^{'}`$
   - assuming we know some algorithm to sample spanning tree on undirected and weighted graph
3. reconstruct the steiner tree $`T`$ from the $`T^{'}`$ on $`G`$ to minimize the probability difference between $`T`$ and $`T^{'}`$

# notation

- $`G=(V, E)`$, edge weight $`w: E \rightarrow R`$
- terminals $`X`$
- for each edge $`\mathbb{e}`$ in transitive closure, denote its corresponding edges in $`G`$ as $`E(\mathbb{e})`$
- transitive closure $`G^{'}=(X, E^{'})`$, new edge weight $`w^{'}: E^{'} \rightarrow R`$
  - $`w^{'}(\mathbb{e}) = \prod\limits_{e \in E(\mathbb{e})} w(e)`$
  - in other words, transitive closure is constructed by product of edge weights (not summation in the usual case)


# reconstruction problem

given a sampled spanning tree $`T^{'}`$ and its reconstructed steiner tree $`T`$, denote the probability of sampling $`T^{'}`$ and $`T`$ from their corresponding graphs:


$`P(T^{'}) \propto \prod\limits_{\mathbb{e} \in T^{'}} \prod\limits_{e \in E(\mathbb{e})} w(e)`$

$`P(T) \propto \prod\limits_{e \in T} w(e)`$

ideally, if we can upper-bound the the "difference" $`d(T^{'}, T)`$ for every $`T^{'}`$ using some reconstruction algorithm, then we can bound the distance between 1)  the  probability distributions produced by tha above algorithm 2) the desired  probability distributions. 

define the "distance" between $`T^{'}`$ and $`T`$ as

$`d(T^{'}, T)=\frac{P(T^{'})}{P(T)}`$.

the problem is:

given $`T^{'}`$ in $`G^{'}`$, reconstruct $`T`$ from $`T^{'}`$ in $`G`$ such that $`d(T^{'}, T)`$ is minized. 

by "reconstruction", it means creating a mapping from edges in $`T^{'}`$ to edge subset in $`G`$. 
Specifically, we map $`f \in T^{'}`$ to $`E(f) \subseteq E`$ s.t $`\prod\limits_{e \in E(f)} w(e) = w^{'}(f)`$ 


