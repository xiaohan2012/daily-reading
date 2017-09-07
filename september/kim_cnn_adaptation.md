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


# experiment results

## experiment result for `kim_cnn`

softmax entropy as loss

1. p@1: ~30%
2. p@3: ~18%
3. p@5: ~14%

weird thing:

1. performnace **decreases**
2. training loss **increases**

possible explation: learning rate too high ([source](https://stackoverflow.com/questions/39868939/possible-explanations-for-loss-increasing))


## fastxml

1. precision at 1: 0.28439597315436244
2. precision at 3: 0.194910514541387
3. precision at 5: 0.15000000000000002
4. precision at 10: 0.10486577181208054

## PFastreXML

1. precision at 1: 0.2785234899328859
2. precision at 3: 0.1977069351230425
3. precision at 5: 0.1545302013422819
4. precision at 10: 0.10696308724832215

##  kimcnn + logistic entropy

1. p@1: 0.57
2. p@3: 0.38 
3. p@5: 0.29