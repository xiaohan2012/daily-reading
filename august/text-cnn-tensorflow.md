# preprocessing

## document to integer ids

- [VocabularyProcessor(max_document_length,...)](http://tflearn.org/data_utils/#vocabulary-processor)
  - documents longer than `max_document_length` will be trimmed shorter

  
# neural network related

## `embedding_loopup`

- [tf.nn.embedding_lookup(embedding_table, ids)](https://www.tensorflow.org/api_docs/python/tf/nn/embedding_lookup)
  - `ids`: tensor containing the ids to be looked up in `embedding_table`
  - it returns a 3d tensor `[None, sequence_length, embedding_size]`

## why using `tf.expand_dim`

`conv2d` expects 2d tensor `[batch, widht, height, channel]`
 
[tf.expand_dim(tensor, axis)](https://www.tensorflow.org/api_docs/python/tf/expand_dims): inserts a dimension of 1 at `axis`

- `tf.reshape` a more verbose way to expand

## parameters to `max_pool` and `conv2d`

- `max_pool`
  - `ksize=[batch, height, width, channels]`
- `conv2d`
  - `filter=[height, width, in_channels, out_channels]`
height comes **before** width!

## padding="VALID"

without padding the boundaries (narrow padding)

## update global step

use: `current_step = tf.train.global_step(sess, global_step)`

- `global_step` is just a variable
- `global_step = tf.Variable(0, name="global_step", trainable=False)`

----------------------


# tensorflow general

## `name_scope`
  
for better graph visualization by adding hierarchy

tip: for operations in the same layer, group them into one `name_scope`

## `tf.concat([t1, t2, ...], axis)`

concatenate tensors along axis. 

example: given 2d tensors, if concat along:

- axis=0, stacking along rows (verticle)
- axis=1, stacking along columns (horizontal)

## `optimizer.minimize`

equal to calling `compute_gradients()` and `apply_gradients()`:

- as name suggests

## accuracy calculation

remember to cast to float: `tf.cast(correction_predictions, tf.float32)`

## handy helpers

- `tf.nn.bias_add(x, b)`
- `tf.nn.xw_plus_b(x, W, b)`: equal to `tf.matmul(x, W) + b`
- `tf.nn.softmax_cross_entropy_with_logits(score, correct_label)`


## `placeholder` and `constant`

  - `placeholder` `shape=None` if it's a scaler
  - `shape` in `constant`?


# `tf.summary`

- `tf.summary.histogram` and `tf.summary.scalar`
- `tf.nn.zero_fraction`: count zero fraction (sparsity)
- `tf.summary.merge()` to merge single summaries

to get summary, needs to run it in session:

1. `_, summary, step = sess.run([train_op, summary_op, global_step])`
2. add it to summary writer: `summary_writer.add_summary(summary, step)`
   - `step` is needed


## gradient summary

    for g, v in grad_and_vars:
    	if g is not None:
	   # add summary


remember `if g is not None`

----------------------

# checkpoints

- initialize saver object: `tf.train.Saver(tf.global_variables(), max_to_keep=some_number)`
  - `tf.train.Saver`
  - `tf.global_variables`
- do checkpoint: `saver.save(sess, checkpoint_prefix, global_step=global_step)`


# evaluation workflow

1. load `vocab_processor`
   1. `learn.preprocessing.VocabularyProcessor.restore(vocab_path)`
1. transform the input text into matrix
   1. `vocab_processor.transform(x_raw)`
1. restore session using:
   1. load `saver = tf.train.import_meta_graph()` from checkpoint file
   1. restore session `saver.restore(session, checkpoint_file)`
      - get `checkpoint_file`: `tf.train.latest_checkpoint(FLAGS.checkpoint_dir)`
      - a string
1. get placeholder variables and prediction variable
1. `sess.run` to get result
1. evaluate

## MetaGraph

- contains definition of a graph and other metadata
- contains the information required to:
  - **continue training**
  - **perform evaluation**
  - **run inference on a previously trained graph**
- [ref](https://www.tensorflow.org/programmers_guide/meta_graph)

## get variables

use:

    	
    variable = graph.get_operation_by_name("name_scope/variable_name").outputs[0]

## misc

- accumulate result: `np.concatenate([acc, new_rows)`
- stack columns: `np.stack_column(columns, columns)`

# autoreload

add 
    
    c.InteractiveShellApp.extensions = ['autoreload']
    c.InteractiveShellApp.exec_lines = ['%autoreload 2']

to `ipython_config.py`

# mistakes

- to evaluate **single** variable, run `sess.eval(var)`, **no** bracket
- to evaluate **multiple** variables, run `sess.eval([var1, var2, ...])`, **with** bracket