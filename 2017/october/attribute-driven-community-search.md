# Attribute-Driven Community Search

- **input 1**: attributed graph, where each node can have one or more attributes
- **input 2**: query `Q=(V_q, W_q)`
  - a set of nodes `V_q`
  - a set of attribute: `W_q`
- **output**: find *1)* densely-connected* (by `k`-truss) and *2)* attribute homogeneous subgraphs

relevant methods:

1. k-core
2. k-truss: each edge in at least k-2 triangles (the graph can be disconnected)
3. 1.0-quasi-k-clique-l-adjacent community model: two k cliques will be merged if they share at least l vertices

but they does not consider labels

one straight-forward solution: filter the graph by queried attributes and then use community query method
- too strict as sometimes incorporating attribtues not in `W_q` gives denser subgraphs

# what is a good community

- **dense**: `(k-d)`-truss, a `k`-truss containing `V_q` and each node is no more than `d` from query node
  - is `d` necessary to capture denseness

- **relevance/coverage**: node attributes covers as many attributes as possible in `W_q`

- **homogeneity**: nodes should share as many attributes with each other as possible


# method

concepts: 

1. connected k-truss: a k-truss that is connected
2. communication cost: the maximum of shortest path length between `u \in H` and `q \in V_q`
3. `(k, d)`-truss: a k-truss that has communication cost `\le d`

## attribute score function 

good `f(H, W_q)` should capture:

1. if one node covers more `w \in W_q`, `f` should be higher (single node)
2. for some `w \in W_q`, if it's covered by many nodes, `f` should be higher (single attribute)





