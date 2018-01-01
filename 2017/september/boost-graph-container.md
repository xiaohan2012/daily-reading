# overview

https://theboostcpplibraries.com/boost.graph-containers

two other graph containers:

- `boost::adjacency_matrix`: internally uses a 2D table
- `boost::compressed_sparse_row_graph`: immutable graph (no nodes/edges can be added/removed once graph is created)

# `boost::adjacency_matrix`

template parameters does not have the first two  as in `boost::adjacency_list` because it doesn't need to.

however, the direction parameter is needed. 

an example:

```c++
typedef boost::adjacency_matrix<boost::undirectedS> graph;
graph g{edges.begin(), edges.end(), 4};
```

# `boost::compressed_sparse_row_graph`

think of it as the `csr_matrix` in `scipy.sparse`.

```c++
typedef boost::compressed_sparse_row_graph<boost::bidirectionalS> graph;
graph g{boost::edges_are_unsorted_multi_pass, edges.begin(),
       edges.end(), 4};
```

only supports directed graph (you can make it undirected by adding `(i, j)` and `(j, i)` simultaneously 

