# best edge for core numer increase

# problem

given $`G=(V, E)`$, select one edge among $`\hat{E}=V \times V - E`$ that maximizes 

$`\Delta_f(e) = f(G+\{e\}) - f(G)`$

where $`f(G)=\sum\limits_{v \in V} core(v)`$. 

## main challenge

among $`O(n^2)`$ edges, how to select the best one efficiently? how to avoid iterating over possible candidate edges, which takes at least $`O(n^2)`$ time. 

## variants

select $`B`$ edges $`E^{'} \subseteq \hat{E}`$ that maximizes:

$`f(G+E^{'}) - f(G)`$

# pruning strategy

main idea: we derive an upperbound for edge $`(u, \cdot)`$ absed on node $`u`$. 
using this upperbound and computed $`\Delta_f(\cdot)`$ values, we can prune edges efficiently. 

for each candididate edge $`e=(u, v)`$, we assume $`core(u) < core(v)`$ w.l.o.g, 

then $`\Delta_f(e)`$ is *upper-bounded* by the numbers of the nodes $`x`$ such that: 

$`x`$ is reachable from from $`u`$ via some path that consisting of nodes $`y`$ with $`core(y) = core(u)`$.

this result is from Theorem 4 of VLDB paper

- we denote reachable node set by $`nc(u)`$
- such bound by $`ub(u)=|nc(u)|`$


in other words, suppose we have computed the exact value $`\Delte_f(e)`$ for a small set of edges and we take the maximum $`\Delte_f^{'}`$, then any edges $`(u, \cdot)`$ with $`ub(u) \le \Delte_f^{'}`$ can be pruned.

note that, we are actually pruning nodes instead of edges because $`\Delte_f((u, v))`$ only depends on $`u`$.

# edge selection strategy

(using the order-based paper, ICDE 2017)

the question is how to select edges to make $`\Delte_f`$ as much as possible. 

**rule 1**, edges $`e=(u, v)`$ with $`\deg^{+}(u) < core(u)`$ can't increase its core number, in other words, $`\Delta_f(e)=0`$. 

these edges can be pruned in time $`O(n)`$


**rule 2**, for edge $`e=(u, v)`$ with $`\deg^{+}(u) = core(u)`$ and node $`v \in nc(u)`$, we would like $`\deg^{+}(v)=core(v)`$ as well, because in this case, $`v`$ might increase its core number as well. 

in other words, we denote the set of nodes $`nc^{+}(u)`$ as $`v \in nc(u)`$, $`\deg^{+}(v) = core(v)`$ and nodes in $`nc^{+}(u)`$ reachable from each other via path of nodes in $`nc^{+}(u)`$ itself. 

this heuristic selects edge $`e=(u, v)`$ with maximum $`|nc^{+}(u)|`$.



# algorithm

## index for pruning

for pruning, nodes $`V`$ can be grouped by their core index and connectivity relation, so that nodes with the same core index and are reachable from each other via path of nodes with same core index are grouped together. 

it's obvious that such groups are disjoint. 

then we can prune groups instead of nodes because nodes in the same group have the same $`ub`$ value. 

this grouping information can be easily calcualted by first k-core decomposition and second, BFS, which takes $`O(E)`$. 

## iterative pruning

1. initially prune nodes accoding to rule 1
2. select an edge $`e(u, v)`$ according to rule 2
3. update best $`\Delta_f`$ value
4. prune nodes if $`\Delta_f`$ changes
5. go back to step 2

## time complexity

becaue we are pruning nodes, it's $`O(n)`$ 