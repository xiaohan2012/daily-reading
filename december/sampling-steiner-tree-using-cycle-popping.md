# sampling steiner tree using cycle popping


## LERW

adapting from spanning tree to steiner tree

replace 2 in Algorithm 1 by:

>>> "for each terminal nodes", instead of "for each node"

[complete algorithm](http://193.166.24.212/loop_erasing.pdf)

## cycle popping for steiner tree

stacks are defined in the same way as the spanning tree version

>>> 1) pop until there are no cycles involved with terminals nodes, resulting in $`G_s`$
>>> 2) return the edges that are traversed on $`G_s`$ starting from each terminal to the root, resuling in $`G_s^{'}`$


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


