# `tf.sets`

- `set_intersection(a, b)`: intersection at the last dim
- `set_size(a)`: accepts `SparseTensor`

## `SparseTensor` as argument

when the sets are of different lengths, need to use a sparse tensor

for example, the following label_lists

```[[0, 1, 2], [1, 2], [0, 2]]```

should correponds to the following `SparseTensor` (in dense form)

```
[[0 1 2]
 [1 2 0]
 [0 2 0]]
```

# `div` vs `divide`

- `div`: returns integer if args are ing
- `divide`: float for whatever
- `\`: same as `divide`

#  [SparseTensor](https://www.tensorflow.org/versions/r0.12/api_docs/python/sparse_ops/sparse_tensor_representation#SparseTensor)

correponding concepts:

- `tf.sparse_placeholder(dtype, shape)`
- `SparseTensorValue` (used when evaluating)
- `tf.sparse_to_dense(indices, shape, values).eval()` to get the value

to evaluate it, can do either:

- `feed_dict={sparse_tensor: (indices, values, shape)}`
- `feed_dict={sparse_tensor: SparseTensorValue(indices, values, shape)}`


# possible improvement

- `input_x` and `input_y_binary` can be `SparseTensor` as well, currently it's dense. 

# misc

- `numpy.squeeze` and `tf.squeeze`: remove the dimentions of size 1
-  sort a Tensor: [SO post](https://stackoverflow.com/questions/40784941/sorting-an-array-in-tensorflow)
   - [tf.gather(params, indices, axies)](https://www.tensorflow.org/api_docs/python/tf/gather): gather entries from `params` on `axis` according to `slices`
- `tf.reverse(t, axis=[...])` reverse a tensor on certain axes. 
  - `axis=[..]`: remember the `[]`
- `tf.nn.top_k`: [differentiable](https://github.com/tensorflow/tensorflow/issues/5726)
- flatten a tensor: `tf.reshape(tensor, [tf.reduce_prod(tensor.shape)])`