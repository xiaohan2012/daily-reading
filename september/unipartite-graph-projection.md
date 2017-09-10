# problem

given a set of 

```
{post-1: {user_i, user_j, ...}, 
 post-2: {user-p, user_q, ...}
}
```

create a graph on posts such that two posts are connected if they share common users. 

# idea

1. create bipartite adjacency matrix `m` (row is post, column is suer
2. matrix multiplication `m * m.T`, the new matrix is `m'`
3. get the graph from the `m'`

trick (sparse matrix to `graph_tool.graph`)

```python
g = Graph()
adj = ...
g.add_edge_list(zip(*adj.nonzero()))
```