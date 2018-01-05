# label embedding extreme multi-label classification

# loss function

denote the embedding of the input data (text, feature vector, etc) as `z_t`
and the embedding of its labels as `\{z_l\}`. 

the loss function is:

`J(z_t, z_l) = - \text{E}_{l} \left( \log (\sigma(z_t^T z_l)) - Q \text{E}_{l^{'} \in P(t)}\log (\sigma(z_t^T z_l^{'})) \right)`

where `\sigma` is the sigmoid function, `Q` is the number of negative label samples and `P(t)` is the probability distribution of sampling a label other than `\{z_l\}`

note that is should be `\text{E}_{l}` instead of `\sum_{l}`

- if using expectation, treating each instance as equal
- if using sum, instance with more labels are biased

# textual data

text -> CNN -> fully connected (FC) --> `z_t`

# bag of words

words --> embedding look-up --> aggregator (mean, max-pooling) --> FC --> `z_t`

# feature vector

feature vector --> FC (one or more layers) --> `z_t`
