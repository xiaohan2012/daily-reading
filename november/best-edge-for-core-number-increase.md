# best edge for core numer increase

# problem

given $`G=(V, E)`$, select one edge among $`\hat{E}=V \times V - E`$ that maximizes 

$`\Delta f(e) = f(G+\{e\}) - f(G)`$

where $`f(G)=\sum\limits_{v \in V} core(v)`$. 

## main challenge

among $`O(n^2)`$ edges, how to select the best one efficiently? how to avoid iterating over possible candidate edges, which takes at least $`O(n^2)`$ time. 

## variants

select $`B`$ edges $`E^{'} \subseteq \hat{E}`$ that maximizes:

$`f(G+E^{'}) - f(G)`$

# edge pruning strategy

for each candididate edge $`e=(u, v)`$, we first assume $`core(u) < core(v)`$ w.l.o.g, 

## strategy 1: pruning by $`\deg^{+}(u)`$

(using the order-based paper, ICDE 2017)

edges $`e=(u, \cdot)`$ with $`\deg^{+}(u) < core(u)`$ can't increase its core number, in other words, $`\Delta f(e)=0`$. 

these edges can be pruned in time $`O(n)`$


## strategy 2: pruning by upperbound

main idea: we derive an upperbound for edge $`(u, \cdot)`$ absed on node $`u`$. 
using this upperbound and computed $`\Delta f(\cdot)`$ values, we can prune edges efficiently. 

then $`\Delta f(e)`$ is *upper-bounded* by the numbers of the nodes $`x`$ such that: 

$`x`$ is reachable from from $`u`$ via some path that consisting of nodes $`y`$ with $`core(y) = core(u)`$.

this result is from Theorem 4 of VLDB paper

we denote:

- reachable node set by $`nc(u)`$
- the upper bound by $`ub(e)=|nc(u)|`$

in other words, suppose we have computed the exact value $`\Delta f(e)`$ for a small set of edges and we take the maximum $`\Delta f^{'}`$, then any edges $`(u, \cdot)`$ with $`ub(e) \le \Delta f^{'}`$ can be pruned.

note that, we are actually pruning nodes instead of edges because $`\Delta f((u, v))`$ only depends on $`u`$.

## special case : $`e=(u, v)`$ s.t. $`core(u) = core(v)`$

two subcases to consider:

**first**: if $`nc(u) = nc(v)`$, then $`ub(e)=|nc(u)|=|nc(v)|`$. this is obvious

**second**: if $`nc(u) \neq nc(v)`$, we prove $`ub(e)=2`$. 

first of all, we show if $`\Delta f(e)>0`$, then $`\Delta f(e)>2`$ and both $`u`$ anv $`v`$ increases their core index. 

we prove by contradiction (assuming $`u`$ is ordered before $`v`$):

- 1) assuming $`u`$ changes core while $`v`$ remains, then we would require $`\deg^{+}(u)`$ to increase. however, because $`v`$ remains, this is impossible. 
- 2) assuming $`v`$ changes while $`u`$ remains, then this is impossible because $`\deg^{+}(v)`$ does not change in this case. 

second, we show $`ub(e)=2`$. in other words $`u`$ and $`v`$ are the only two nodes with core index increased. 

equivalently, we show $`u > w`$, for $`\forall w \in nc(u) - \{u\}`$. 

because $`u`$ changes, it can be seen that:

$`\deg^{+}(u)=core(u)=\deg^{>}(u)`$ before insertion, where $`\deg^{>}(u)`$ is the number of neighbors on $`u`$ with higher cores.

in other words, other $`w \in nc(u) - \{u\}`$ have $`\deg^{>}(v) < core(u)`$. therefore, they are removed earlier than $`u`$ during the core decomposition step. 

the same thing can be proved for $`v`$. 

# edge selection strategy

the question is how to select edges to make $`\Delta f`$ as much as possible so the above pruning steps can be drastic. 

**heuristic 1** for edge $`e=(u, v)`$ with $`\deg^{+}(u) = core(u)`$ and node $`v \in nc(u)`$, we would like $`\deg^{+}(v)=core(v)`$ as well, because in this case, $`v`$ might increase its core number as well. 

in other words, we denote the set of nodes $`nc^{+}(u)`$ as $`v \in nc(u)`$, $`\deg^{+}(v) = core(v)`$ and nodes in $`nc^{+}(u)`$ reachable from each other via path of nodes in $`nc^{+}(u)`$ itself. 

this heuristic selects edge $`e=(u, v)`$ with maximum $`|nc^{+}(u)|`$.



# algorithm

## index for pruning

for pruning, nodes $`V`$ can be grouped by their core index and connectivity relation, so that nodes with the same core index and are reachable from each other via path of nodes with same core index are grouped together. 

it's obvious that such groups are disjoint. 

then we can prune groups instead of nodes because nodes in the same group have the same $`ub`$ value. 

this grouping information can be easily calculated by:

1) k-core decomposition 
2) BFS, which takes $`O(E)`$

## iterative pruning

1. initially prune edges using pruning strategy 1
2. select an edge $`e(u, v)`$ 
3. update best $`\Delta f`$ value
4. prune nodes if $`\Delta f`$ using pruning strategy 2
5. go back to step 2

## time complexity

becaue we are pruning nodes, it's $`O(n)`$ 