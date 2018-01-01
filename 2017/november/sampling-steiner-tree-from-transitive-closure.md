# sampling steiner tree from transitive closure

# problem in general

sampling a steiner tree $`T`$ with probability proportional to $`\prod\limits_{e \in T} w(e)`$

we can easily adapt our current problem (from $`\exp\left(\sum\limits_{e \in T} -c(e)\right)`$) plugging in $`w(e) = \exp\left(-c(e)\right)`$

# notation

- $`G=(V, E)`$, edge weight $`w: E \rightarrow R`$
- for each edge $`f`$ in transitive closure, given some reconstruction algorithm, denote its corresponding edges in $`G`$ as $`E(f)`$
- transitive closure $`G^{'}=(X, E^{'})`$, new edge weight $`w^{'}: E^{'} \rightarrow R`$
  - $`w^{'}(f) = \prod\limits_{e \in E(f)} w(e)`$
  - in other words, transitive closure is constructed by product of edge weights (not summation in the usual case)
- $`T^{'}`$: some spanning tree on $`G^{'}`$
- $`T`$: some steiner tree on $`G`$

denote two sets of probabilities:

- $`P(T^{'})`$: the probability of sampling $`T^{'}`$ from $`G^{'}`$
- $`P(T)`$: our desired probability of samppling steiner tree

# sampling procedure in general

sampling an steiner tree can be done in the following steps:

1. construct a transitive closure $`G^{'}`$ on original graph $`G`$
2. sample a spanning tree $`T^{'}`$ from $`G^{'}`$
   - assuming we know some algorithm to sample spanning tree on undirected and weighted graph
3. reconstruct the steiner tree $`T`$ from the $`T^{'}`$ on $`G`$ to minimize the probability difference between $`T`$ and $`T^{'}`$

"Reconstruction" means creating a mapping from edges in $`T^{'}`$ to edge subset in $`G`$. 
Specifically, we map $`f \in T^{'}`$ to $`E(f) \subseteq E`$ s.t $`\prod\limits_{e \in E(f)} w(e) = w^{'}(f)`$

ideally, we would like $`P(T)`$ and $`P(T^{'})`$ stay as close as possible.

one way is to recontruct $`T`$ from $`T^{'}`$ in a specific way such that $`P(T) \approx P(T^{'})`$.

# reconstruction problem

given a sampled spanning tree $`T^{'}`$ and its reconstructed steiner tree $`T`$, their probability has the following form:


$`P(T^{'}) \propto \prod\limits_{f \in T^{'}} \prod\limits_{e \in E(f)} w(e)`$

$`P(T) \propto \prod\limits_{e \in T} w(e)`$

ideally, if we can upper-bound the "probability distance" $`d(T^{'}, T)`$ for every $`T^{'}`$ using some reconstruction algorithm, then we can bound the distance between the two probability distributions. 

define the "distance" between $`T^{'}`$ and $`T`$ as

$`d(T^{'}, T)=\frac{P(T^{'})}{P(T)}`$.

then the problem is:

given $`T^{'}`$ in $`G^{'}`$, reconstruct $`T`$ from $`T^{'}`$ in $`G`$ such that $`d(T^{'}, T)`$ is minimized. 




