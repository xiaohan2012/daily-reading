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

