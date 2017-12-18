# generating random spanning trees more quickly than the cover time

https://dl.acm.org/citation.cfm?id=237880

# algorithm

## general setting

- weighted directed graph
- returns a directed tree
- goal: the tree probability is prop to product the edge weights

## preprocessing

goal: convert the graph into a markov chain

if the graph is stochastic, good. 
otherwise..

**rooted version**: 

our goal: $`P(T) \propto \prod_{(u, v) \in T, u \neq r} w(u, v)`$.

the modification on $`w`$: normalize each edge's weight to $`w^{'}(u, v) = w(u, v) / \sum_{x \in N(u)} w(u, x) = w(u, v) / w(u)`$

if we apply the same goal on this new graph, then 

$`P^{'}(T) \propto \prod_{(u, v) \in T, u \neq r} w^{'}(u, v) = \prod_{(u, v) \in T, u \neq r} w(u, v) / w(u)`$

as we know $`\prod_{(u, v) \in T, u \neq r} 1 / w(u)`$ is a constant, therefore $`P^{'}(T) \propto \prod_{(u, v) \in T, u \neq r} w(u, v) = P(T)`$. 

**unrooted version**

normalization $`w^{'}(u, v) = w(u, v) / \text{max}_u w(u)`$

$`P^{'}(T) \propto \prod_{(u, v) \in T, u \neq r} w^{'}(u, v) = \prod_{(u, v) \in T, u \neq r} w(u, v) / \text{max}_u w(u) \propto \prod_{(u, v) \in T, u \neq r} w(u, v) = P(T)`$

note that to make it stochastic, we need to make up for the "missing edges", thus creating self-loops is a natural decision. 

## rooted version


1. intially current tree only contains the root
2. for each node, do random walk until it touches the current 
   - mark all the nodes on the walk as visited and they become part of tree

## unrooted version

the paper claims that sampling an unrooted spanning tree can be done by:

1. sample a root w.r.t the stationary distribution
2. call the rooted sampling process

I'm not sure why Figure 2 adopts a different approach, since the above is more straightforward. 

meanwhile, uniformally sampling a root should also give the same result for both weighted and unweighted graphs (using Broder's proof from directed tree to undirected tree, the summation). 

**update Dec, 18, 2018**

this above approach can be used to sample undirected and Eularian graphs.

however, for general directed graphs, image adding a dummy vertex $`v^{*}`$ that every node connects to. and we want to sample a tree rooted at $`v^{*}`$. 

if removing $`v^{*}`$ gives a forest (multiple nodes connect to $`v^{*}`$), then it's not a valid tree. otherwise, the remaining is a spanning tree.  

in other words, the only node that connects to $`v^{*}`$ is the root. 

in the new algorithm, for each node it has $`\delta`$ probability to connect to $`v^{*}`$ and $`1-\delta`$ probability to visit other nodes. 

if there are multiple nodes visiting $`v^{*}`$, then the tree is invalid. and we make $`\delta`$ smaller to try again. 

the smaller the $`\delta`$, the more likely the algorithm succeeds, however, the longer time it takes to run. 



# cycle popping

## cycle popping algorithm

- each non-root node is a associated with a stack with its neighbors (randomly generated
- on top of each stack, it defines an directed edge. together, all edges define a directed graph
- the graph can be a spanning tree or contains cycles

if it contains cycles, pop the stacks associated with the cycle. continue the cycle popping until non cycle is found. 

it's a different algorihm on surface but essentially identical to the loop-erasing algorithm 

## equivalence of cycle popping and LERW


- random walk is defined by the stacks and their top elements. 
- we start with some vertex, do a random walk using the stacks. 

if cycles are detected (revisit some vertex), we ignore the cycle and start from the same vertex again until it touches the current tree. 

"Ignoring" internally pop the cycle (redefine the random walks on the nodes in the cycle). 

It's also equivalent to loop erasing part of the LERW algorithm. 

Note that the order of the cycles being removed does not matter (proved later). 
  

## main theorems

1. if the graph contains a spanning tree, cycle popping is done in finite steps. otherwise, it never terminates. 
2. the probability of the tree generated is uniform. 

## proof for termination within finite number  (assuming it has a spanning tree)

main lemma: every cycle will be eventually popped regardless of the popping order. 

## proof of probability distribution

the cycle being popped is independent with the tree be generated. 

## infinite number of cycles

example: disconnected components

# runnning time analysis

definition:

- $`E_i T_j`$: expected number of steps to start from $`i`$ to reach $`j`$ using random walk
- mean commute time between $`i`$ and $`j`$: $`E_i T_j + E_j T_i`$
- mean hitting time, the time to go from a $`\pi`$-random node to another $`\pi`$-random node: $`\sum\limits_{ij} \pi(i) \pi(j) E_i T_j`$

for $`RandomTreeWithRoot`$, it takes mean commute time to visit a $`\pi`$-random vertex. 

$`\sum_i \pi(i) E_i T_r + E_r T_i`$ (proof of theorem 14)



# learned

some terms:

- cycle popping: an algorithm as well as proof technique for the sampling distribution
- loop-erased random walk: random walk that gets rid of loops (by marking visited nodes)

dealing non-stochastic weighted graph:

- normalize the edge weights
- adding cycling to itsself (unrooted version)

algorithm to use for different cases:

- dealing with rooted tree and undirected graph (even for unrooted tree): use $`RandomTreeWithRoot`$
- for general graph and unrooted tree: use $`RandomTree`$

# I don't understand..

- proof of theorem 14 (CFTP paper): why considering the walk started at `u` visits `u` before `r`? why not start from `u` and reach `r`

# links 

- http://www.bigredbits.com/archives/226
- http://staff.utia.cas.cz/swart/present/UST.pdf (maybe I should go through it)
- coupling from the past paper (on unrooted version)