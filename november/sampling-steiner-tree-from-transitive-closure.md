# sampling steiner tree from transitive closure

# algorithm overview

- construct a transitive closure $`G^{'}`$ on original graph $`G`$
- sample a spanning tree $`T^{'}`$ from $`G^{'}`$
  - assuming we know some algorithm to sample spanning tree on undirected and weighted graph
- reconstruct the steiner tree $`T`$ from the $`T^{'}`$ on $`G`$

# notation

- $`G=(V, E)`$, $`w: E \rightarrow R`$
- terminals $`X`$
- for each edge $`\mathbb{e}`$ in transitive closure, denote its corresponding edges in $`G`$ as $`E(\mathbb{e})`$
- transitive closure $`G^{'}=(X, E^{'})`$, $`w^{'}: E^{'} \rightarrow R`$
  - $`w^{'}(\mathbb{e}) = \prod\limits_{e \in E(\mathbb{e})} w(e)
  - in other words, transitive closure is constructed by product of edge weights (not summation in the usual case)


# challenges

given a sampled spanning tree `$T^{'}$` and its reconstructed steiner tree `$T$`, denote the probability of sampling `$T^{'}$` and `$T$` from their corresponding graphs:


`$P(T^{'}) \propto \prod\limits_{\mathbb{e} \in T^{'}} \prod\limits_{e \in E(\mathbb{e})} w(e)$`

`$P(T) \propto \prod\limits_{e \in T} w(e)$`

define the "distance" between `$T^{'}$` and `$T$` as

`$d(T^{'}, T)=\frac{P(T^{'})}{P(T)}$`.


the problem is:

given `$T^{'}$` in `$G^{'}$`, reconstruct `$T$` from `$T^{'}$` in `$G$` such that `$d(T^{'}, T)$` is minized. 

by "reconstruction", it means creating a mapping between edges in `$T^{'}$` and edge set in `$G$`. 
Specifically, `$f \in T^{'}$` to `$E(f) \subseteq E$` s.t `$\prod\limits_{e \in E(f)} w(e) = w^{'}(f)$` 
