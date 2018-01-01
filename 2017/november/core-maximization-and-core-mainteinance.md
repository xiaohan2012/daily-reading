# VLDB paper's relation to core maximization problem

## $`pcd`$

for each node, its core change is upperbounded by $`pcd`$ (pure coredegree)

to use this information, need to compute it efficiently across all nodes


# ICDE paper: ordered-based approach

## another upperbound from (Section A):

given node $`u`$, the size of the subset of $`sc(u)`$ that nodes in it are ordered *after* $`u`$. 

- $`sc`$ is the subcore
- the question is: is the bound tighter than $`pcd`$?

this bound can be computed by $`BFS`$ in $`O(E)`$. 

## observation: size of sub core/pure core

can be very large, even to $`10^5`$ (more than 10% of the nodes). 

Figure 5 in the ICDE paper. 
