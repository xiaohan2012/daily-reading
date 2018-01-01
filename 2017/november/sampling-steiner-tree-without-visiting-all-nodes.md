# sampling steiner tree without visiting all nodes

assuming the algorithm as the same one in Broder's paper, except that we terminate until all termianls are visited. 

# observation

1. there might be extra edges to be removed (a cycle that does not touch any terminal)
2. the final tree (after cutting extra edges) is a valid steiner tree
   - because it's connected
   - each node in the graph has 1 edge (except the starting node)

# algorithm



# to check in experiment

- how many nodes are actually visited compared to `N`?