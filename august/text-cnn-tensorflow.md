# name_scope
  
for better graph visualization by adding hierarchy

tip: for operations in the same layer, group them into one `name_scope`
  

# `embedding_loopup`

- [tf.nn.embedding_lookup(embedding_table, ids)](https://www.tensorflow.org/api_docs/python/tf/nn/embedding_lookup)
  - `ids`: tensor containing the ids to be looked up in `embedding_table`
  - it returns a 3d tensor `[None, sequence_length, embedding_size]`

## why using `tf.expand_dim`

`conv2d` expects 2d tensor `[batch, widht, height, channel]`
 
[tf.expand_dim(tensor, axis)](https://www.tensorflow.org/api_docs/python/tf/expand_dims): inserts a dimension of 1 at `axis`

- `tf.reshape` a more verbose way to expand

# parameters to `max_pool` and `conv2d`

- `max_pool`
  - `ksize=[batch, height, width, channels]`
- `conv2d`
  - `filter=[height, width, in_channels, out_channels]`
height comes **before** width!

## padding="VALID"

without padding the boundaries (narrow padding)

# `tf.concat([t1, t2, ...], axis)`

concatenate tensors along axis. 

example: given 2d tensors, if concat along:

- axis=0, stacking along rows (verticle)
- axis=1, stacking along columns (horizontal)

# accuracy calculation

remember to cast to float: `tf.cast(correction_predictions, tf.float32)`

# handy helpers

- `tf.nn.bias_add(x, b)`
- `tf.nn.xw_plus_b(x, W, b)`: equal to `tf.matmul(x, W) + b`
- `tf.nn.softmax_cross_entropy_with_logits(score, correct_label)`

# learned/to-learn


- `device`: constrain the computation to run only on certain devices
- checkpoints and plot training process 

