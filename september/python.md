- `set.issubset`

- `np.random.choice`: `replace=True` by default

```python
with pytest.raises(AssertionError):
    q_gen.random()
```

# clean and create a directory in tensorflow

```python
if tf.gfile.Exists(FLAGS.log_dir):
    tf.gfile.DeleteRecursively(FLAGS.log_dir)
  tf.gfile.MakeDirs(FLAGS.log_dir)
```

# "remove" nodes in `graph_tool`

hide it by setting vertex_fitler, benefit:

- it's fast
- node indexes are not changed

# accessing `vertex_property` and `edge_property`

it's slow. use `dict` if possible

# custome object for `set`

change the following functions:

- `__eq__`
- `__ne__`
- `__hash__`

[source](https://stackoverflow.com/questions/5754440/performing-set-operations-on-custom-classes-in-python)

# `vertex_filter`

for graph with hidden hides, its `vertex_filter` will raise error if hidden hides are accessed. 

however, `vertex_filter.a` still have the same length as `g.num_vertices()`

# `graph_tool` installation

`./configure CXXFLAGS="-std=gnu++14"`


# `graph_tool` plot in `matplotlib`

remembe to add before plotting:

- `plt.swith_backend('cairo')

# `Graph.vertex` and `Graph.edge`

- slow to access the node and edge by integers

```
1755     26303      2891233    109.9     95.5          v = libcore.get_vertex(self.__graph, int(i), use_index)
```

```
  1776      3184       333105    104.6     34.9          s = self.vertex(int(s))
  1777      3184       324256    101.8     33.9          t = self.vertex(int(t))
  1778      3184       286766     90.1     30.0          edges = libcore.get_edge(self.__graph, int(s), int(t), all_edges)
```

`graph_python_interface.cc`: 

- `get_vertex`: `get_vertex_hard` (`O(n)`) and `get_vertex_soft` (`O(1)`)
- `get_edge` internally runs `get_edge_dispatch`, seems to iterate through out edges

`Graph.vertex(...)`: 

- if `use_index=True`: return the node with index `i`
- if `use_index=False`: return the `i`th vertex (can differ if the graph is filtered)

# quickly check if a node is in `g`

`g._Graph__filter_state['vertex_filter'][0].a[node]`

don't use `g.vertex`

# GraphView creation

```
  3104       404       529413   1310.4     36.8                      ef[0].fa = efilt.fa
```
setting edge filter is slow, takes `36.8\%` of the time. 

