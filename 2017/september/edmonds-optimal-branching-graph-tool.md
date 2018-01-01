- [random spanning tree in graph_tool](https://git.skewed.de/count0/graph-tool/blob/master/src/graph/topology/graph_random_spanning_tree.cc)


[boost::graph_traits](http://www.boost.org/doc/libs/1_63_0/libs/graph/doc/graph_traits.html): wrapper around graph-related object types, such as `vertex_descriptor`

[weave](https://docs.scipy.org/doc/scipy-0.18.1/reference/tutorial/weave.html#introduction): compile/execute code on the fly in Python

# c++ part

```python
BOOST_PYTHON_MODULE(libgraph_tool_search)
```

to bind c++ functions to python module



# `std::bind`

wraps a function, like partial function and currying. 

[example](http://en.cppreference.com/w/cpp/utility/functional/bind)

[std::placeholders](http://en.cppreference.com/w/cpp/utility/functional/placeholders) used together with `std::bind`

- function types: `std::function<void(const std::string&)>`

# hints

`run_action`?

```c++
void get_kruskal_spanning_tree(GraphInterface& gi, boost::any weight_map,
                               boost::any tree_map)
```

- `tree_map`: `edge_property`
- `weight_map`: `edge_property`

```python
def _prop(t, g, prop):
    """Return either a property map, or an internal property map with a given
    name."""
```

```python
def min_spanning_tree(g, weights=None, root=None, tree_map=None):
    if tree_map is None:
        tree_map = g.new_edge_property("bool")
    if tree_map.value_type() != "bool":
        raise ValueError("edge property 'tree_map' must be of value type bool.")

    u = GraphView(g, directed=False)
    if root is None:
        libgraph_tool_topology.\
               get_kruskal_spanning_tree(u._Graph__graph,
                                         _prop("e", g, weights),
                                         _prop("e", g, tree_map))
    return tree_map
```

`boost::kruskal_minimum_spanning_tree` [signature](http://www.boost.org/doc/libs/1_35_0/boost/graph/kruskal_min_spanning_tree.hpp)

```c++
  template <class Graph, class OutputIterator, class P, class T, class R>
  inline void
  kruskal_minimum_spanning_tree(const Graph& g,
                                OutputIterator spanning_tree_edges, 
                                const bgl_named_params<P, T, R>& params)
```


```c++
    template <class Graph, class IndexMap, class WeightMap, class TreeMap>
    void operator()(const Graph& g, IndexMap vertex_index, WeightMap weights,
                    TreeMap tree_map) const
    {
        kruskal_minimum_spanning_tree(g, tree_inserter<TreeMap>(tree_map),
                                      weight_map(weights).
                                      vertex_index_map(vertex_index));
    }
```

I should use `tree_inserter<TreeMap>(tree_map)` as the tree_map

[back_inserter](http://www.cplusplus.com/reference/iterator/back_inserter/)

example:

`std::copy (bar.begin(),bar.end(),back_inserter(foo));`

- appends elements in `bar` to `foo`
- `foo` must have `push_back` method


- [boost::property_map](http://www.boost.org/doc/libs/1_40_0/libs/property_map/doc/property_map.html)
  - key-value mapping
- [identity_property_map](http://www.boost.org/doc/libs/1_40_0/libs/property_map/doc/identity_property_map.html): returns the key itself. 

[boost::multi_array](http://www.boost.org/doc/libs/1_65_1/libs/multi_array/doc/user.html)


# edmonds optimal branching: signature

```c++
edmonds_optimum_branching<true, true, true>
            (g, identity_property_map(), weights.origin(),
             roots, roots + 0, back_inserter(all_branchings[MAX_SPAN_0]));
```

- `g`: ?
- `identity_property_map()`: property_map
- `weights`: `boost::multi_array`
- `roots`: `    Vertex              roots[] = {0, 1};`
- `all_branchings[MAX_SPAN_0]`: `vector<Edge>`

# define my own graph type in `boost`

it seems to me that I need to define my own `vertex_decriptor`, etc

an example:

```c++
namespace boost{

    struct graph_traits<my_graph_type> {
            typedef int                             vertex_descriptor;
            typedef int                             edge_descriptor;
            typedef directed_tag                    directed_category;
            typedef disallow_parallel_edge_tag      edge_parallel_category;
            typedef edge_list_graph_tag             traversal_category;
            typedef complete_graph::edge_iterator   edge_iterator;
            typedef unsigned                        edges_size_type;

            static vertex_descriptor null_vertex() {return -1;}
        };
}
```

# namespace detail

in one sentence, keep global namespace clean

https://stackoverflow.com/questions/26546265/what-is-the-detail-namespace-commonly-used-for


# boost concept checks

example 1: 

`function_requires< GraphConcept<G> >();` 

from [here](http://www.boost.org/doc/libs/1_35_0/libs/graph/doc/EdgeListGraph.html)

example 2:

`function_requires< EdgeListGraphConcept<TEdgeListGraph> >();`

from edmonds'. 

it checks whether class `TEdgeListGraph` has [`EdgeListGraphConcept`](http://www.boost.org/doc/libs/1_35_0/libs/graph/doc/EdgeListGraph.html).  `EdgeListGraphConcept` defines function `void constraints()`, which list the valid statements of the concept

`GraphInterface`