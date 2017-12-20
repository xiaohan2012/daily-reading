# sampling steiner tree using cycle popping


## LERW

adapting from spanning tree to steiner tree

replace 2 in Algorithm 1 by:

> "for each terminal nodes", instead of "for each node"

[complete algorithm](http://193.166.24.212/loop_erasing.pdf)

## cycle popping for steiner tree

stacks are defined in the same way as the spanning tree version

> 1) pop until there are no cycles involved with terminals nodes, resulting in $`G_s`$

> 2) return the edges that are traversed on $`G_s`$ starting from each terminal to the root, resuling in $`G_s^{'}`$


**lemma**: $`G_s^{'}`$ returned by the above algorithm is a steiner tree. 

proof that 1) $`G_s`$ returns a steiner tree

suppose some terminal node $`x`$ is connected to some other connected subgraph $`G^{'}`$, not touching the current tree. 
$`G^{'}`$ must have $`|G^{'}|`$ edges (because root is not there). then there must be a cycle. 

contradiction. need to continue popping until $`x`$ is connected to the current tree.

2) since $`G_s`$ is a steiner tree, $`G_s^{'}`$ is also a steiner tree. 

**lemma**: the algorithm terminates within finite steps if there is a steiner tree, otherwise do not terminate 

need to prove that all cycles are popped regardless of order. 

intuition: if cycle popping returns a spanning tree in finite steps, then it must also return a steiner tree in finite steps because the steiner tree is a subgraph of the spanning tree. 

## equivalence between cycle popping and loop erased random walk

start from any terminal, do a random walk defined by the stacks and top elements. 

if a cycle is detected, "ignore/pop" it. if the current tree is touched, add the updated walk (without cycle) to the current tree. 

## probability distribution

- $`P(T, C) = P(T)P(C)=\prod_{e \in T} w(e) P(C)`$
- $`P(T) = \sum_C P(T)P(C)=\prod_{e \in T} w(e)`$

therefore, the tree is distributed by product of edge weights


# update Dec, 20

## probability of steiner tree

if we do the weight normalization, edge weights become `\frac{w(u, v)}{w(u)}`

Consider rooted version, the probability is:

`P(T_r(X)) \propto \prod\limits_{u \neq r, (u, v)\in T_r{X} } \frac{w(u, v)}{w(u)}`

this is not very easy to interpret because different trees may have different denumerator. 

even for unweighted graph, 

`P(T_r(X)) \propto \prod\limits_{u \neq r, u \in T_r{X} } \frac{1}{\deg(u)}`

the interpretation can be:

1. in general, the more edges the tree has, the less likely, (because the multiplying <1 values gives even smaller quantity). note that for regular graphs, this is true strictly
2. given the same number of edges, the smaller degree of the node, the more likely the tree.

## independence of popped cycles and tree

the probability to produce a tree $`T`$ is:

$`\sum\limits_{S \mid T} \sum\limits_{C \mid S} P(C \cap T) = \sum\limits_{S \mid T} \sum\limits_{C \mid S} P(C) P(T) = P(T)`$


first of all, given a stack configuraiton, it returns a fixed tree (regardless of order of cycles being popped). 

- cycles are popped in partial order (non-overlapping cycles does not have a order, while containing cycles have order)

following:

- $`S \mid T`$: the set of stack configurations that produce $`T`$
- $`C \mid S`$: given $`S`$, the set of cycles being popped that produces $`T`$
- because the tree is fixed given $`S`$, thus $`T`$ does not depend on the cycles being popped


## another word on equivalance of cycle popping and LERW

LERW essentially pops cycles by loop erasing. 

Note that the order of the cycle being popped does not matter. 

Therefore, LERW simulates the cycle popping algorithm. 