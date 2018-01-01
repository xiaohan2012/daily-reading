# Multi-input and multi-output models

## specifiy model

```python
Model(inputs=[main_input, auxiliary_input], outputs=[main_output, auxiliary_output])
```

where `main_input, auxiliary_input, main_output, auxiliary_output` are just layers

## different loss function and weights

```python
model.compile(optimizer='rmsprop', loss='binary_crossentropy',
              loss_weights=[1., 0.2])
```

using `binary_crossentropy` on all outputs

or differentiate them

```python
model.compile(optimizer='rmsprop',
              loss={'main_output': 'binary_crossentropy', 'aux_output': 'binary_crossentropy'},
              loss_weights={'main_output': 1., 'aux_output': 0.2})
```


# Shared layers

just call that layers with different inputs

```python
import keras
from keras.layers import Input, LSTM, Dense
from keras.models import Model

tweet_a = Input(shape=(140, 256))
tweet_b = Input(shape=(140, 256))

# This layer can take as input a matrix
# and will return a vector of size 64
shared_lstm = LSTM(64)

# When we reuse the same layer instance
# multiple times, the weights of the layer
# are also being reused
# (it is effectively *the same* layer)
encoded_a = shared_lstm(tweet_a)
encoded_b = shared_lstm(tweet_b)
```

# links

https://keras.io/getting-started/functional-api-guide/#multi-input-and-multi-output-models