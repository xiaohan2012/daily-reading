# random spanning tree in Boost Graph

http://www.boost.org/doc/libs/1_65_1/boost/graph/random_spanning_tree.hpp

# `random_spanning_tree_internal`

called internally

node states:

- `black`: in the tree
- `gray`: visited and not in the tree
- `white`: not visited and not in the tree


# random edge generator

- `loop_erased_random_walk` relies on `NextEdge` function to get the next edge
- `weighted_random_out_edge_gen` can be used to define such function, also with weight

# `graph_tool` version

- root is randomly selected if not specified: not exactly the same as Wilson's version
- https://graph-tool.skewed.de/static/doc/_modules/graph_tool/topology.html#random_spanning_tree

# modification to steiner tree version

change this line

```c++
BGL_FORALL_VERTICES_T(v, g, Graph) {
```
