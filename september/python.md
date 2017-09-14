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