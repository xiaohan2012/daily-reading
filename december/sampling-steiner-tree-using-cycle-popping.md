# sampling steiner tree using cycle popping

adapting to steiner tree

replace 2 in Algorithm 1 by:

- "for each terminal nodes", instead of "for each node"

## cycle popping for steiner tree

- pop until there are no cycles involved with terminals nodes

proof that it returns a steiner tree. 

suppose some terminal node `x` is connected to some other connected subgraph `G^{'}`, not touching the current tree. 
`G^{'}` must have `|G^{'}|` edges (because root is not there). then there must be a cycle. contradiction. 


truncating is required: recursively remove the extra nodes (non-terminal leafs) of the steiner trees.

## to show

1. the tree is distributed by product of edge weights

using the independence property

2. equivalence between this cycle popping algorithm between loop erased random walk on steiner tree

seems to be so. 

