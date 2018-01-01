# Preventing Unraveling in Social Networks: The Anchored k-Core Problem


# unraveling process

- nodes with degree fewer than $`k`$ will be removed from the graph
- this creates a cascading process
- finally, it reaches an equilibrium such that the subgraph $`H`$ contains nodes whose induced degree $`\ge k`$

# problem formulation

given a graph, threshold $`k`$ and budget $`b`$, we want to anchor $`b`$ nodes so that the size of the unraveled graph $`H`$ is maximized. 

"anchor" a node will make the node remain no matter what. 

# theoretical result

- for $`k=2`$, polynomial solvable for general graphs
- for $`k \ge 3`$, inapproximable for general graphs
  - for bounded treewidth graphs, polynomial solvable

