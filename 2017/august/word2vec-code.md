# code 

- [src (to start)](https://github.com/tensorflow/tensorflow/blob/r1.3/tensorflow/examples/tutorials/word2vec/word2vec_basic.py)
- [src (more comprehensive)](https://github.com/tensorflow/models/blob/master/tutorials/embedding/word2vec.py)

# build dataset

1. take the most frequent words as vocabulary
2. map the document to word ids
   - if word is not in vocabulary, then it's mapped to `UNK`
3. get the dictionary (`word -> id`) and reverse dictionary (`id -> word`)



# negative sampling

done by `generate_batch(batch_size, num_skips, skip_window)`:

- `batch_size`: number of pairs
- `num_skips`: within each window, the number of context/skip words
- `skip_window`: window size (one direction)

output: `(context word, label word)` pairs

algorithm: 

1. slide a window over the document word sequence, where window size defined by `skip_window`
2. at label word is at the center of the current window
3. randomly sample `num_skip` context words
4. collect the context word and label word pair

# subsampling

goal: to avoid frequent words to be sampled too many times

method: associate each word with a probability to be dropped

- the more frequent the word, the more likely it will be dropped (in the context window)
- [more explanation](http://mccormickml.com/2017/01/11/word2vec-tutorial-part-2-negative-sampling/)

related concept: downsample

- in signal processing: decrease sampling rate
  - [example in matlab](https://se.mathworks.com/help/signal/ref/downsample.html)

# candidate sampling

[to read](https://www.tensorflow.org/extras/candidate_sampling.pdf)

for example, NCE or negative sampling.

not sure what's the difference.

# computing similarity

remember to normalize the weight:

```python
norm = tf.sqrt(tf.reduce_sum(tf.square(embedding), 1, keep_dims=True))
normalized_embedding = embedding / norm
```

then, matrix multiplication: 

```python
valid_embedding = tf.nn.embedding_lookup(normalized_embedding, valid_examples)
similarity = tf.matmul(valid_embedding, normalized_embedding, transpose_b=True)
```

need to transpose `normalized_embedding`


# python tricks

## reverse `id->value` to `value->id`

```python
reversed_dictionary = dict(zip(dictionary.values(), dictionary.keys()))
```

## `collections.deque` as a sliding window

`collections.deque(maxlen=span)` to define a sliding window (the `maxlen` parameter)

slide the window by using `deque.apend(e)`


# tf learned

## `tf.zeros` vs `np.zeros`

1. `tf` gives `float32` by default
1. `np` gives `float64` by default

## `with graph.as_default()`

put `init = tf.global_variables_initializer()` inside the `with` statement

## average loss for mini-batch

instead of print loss for each batch, printing  the average loss of the last `k` batches is more reasonable. 

## `1...n` choose `k` without replacement

`np.random.choice(n, k, replace=False)`

## example of  `tf.nn.embedding_lookup(embedding, input_ids)`

```python
import tensorflow as tf
import numpy

train_input_1 = tf.constant([[1,2], [0,1], [1, 3]])
train_input_2 = tf.constant([0, 1, 2, 3])
embedding = tf.constant(np.random.rand(4, 10))
embed = tf.nn.embedding_lookup(embedding, train_input_1)
with tf.Session() as sess:
    embed_val = sess.run([embed])[0]
    print(embed_val.shape)
```

- `train_input_1`: returns a tensor of `[3, 2, 10]`
- `train_input_2`: returns a tensor of `[4, 10]`

to summarize, the returned shape is: `[batch_size, data_dim, embedding_dim]`

## flattening tensor

`tf.reshape(tensor, [-1])`

## `np.argsort` equivalent, `tf.nn.top_k`

- `tf.nn.top_k(tensor)`: get the greatest along the last dim
- `tf.nn.top_k(tensor, k)`: get the k-greatest along the last dim

example:

```python
m = tf.constant([[3, 1, 2], [0, 1, 0], [1, 1, 3]])
best = tf.nn.top_k(m, 2)[1]
with tf.Session() as sess:
    print(sess.run(best))
```

# review of word2vec

problem: given a context word, predict its word label.

in other words, words are both input and output

