# Sequential

[Sequential](https://keras.io/getting-started/sequential-model-guide/)

linear stacking of layers: 

- either defined by `Sequantial([layer1, layer2, ...])`
- or `model.add(layer)`

# compile

before training, need to compile by `model.compile`

compile specifies:

- optimization method
- loss function
- evaluation metrics

loss function:

  - "binary_crossentropy": for "sigmoid"
  - "categorical_crossentropy": for `softmax`

# training

`model.fit(input_x, input_y, epochs=10, batch_size=32)`

# layers

## Dense

densely connected layer

## Conv2D

replaces `Convolution2D`, 

`Conv2D(num_filters, (width, height), input_shape=(32, 32, 1)`

- note that last dim in `input_shape` is the number of channels

# other tricks

- `model.fit(callbacks=[TensorBoard(log_dir='/tmp/autoencoder'))` to write to `tensorboard`
