# inductive representation learning on large graphs

motivation:

- indutive learning (output embdding for unseen nodes)
- incorporating node features (feature-rich graphs

# approach

briefly speaking, a node aggregate information from its neighbors and their neighbors' neighbors and so on.

for a give node `v`, its representation computed by a feed forward neural network, where:

- the input is the node features
- for layer `k`, its input is the output, `h_u^{k-1}` of the `k-1` layer of `v`'s neighbors, `u`

key components:

- aggregate function at layer `k`
- transformation function that transforms the aggregated vector and `h_v^{k-1}` into `h_v^k`. 

## aggregate functions

1. mean aggregator: just take the mean of `h_u^{k-1}` (neighbors)
2. LSTM: its order-sensitive however here neighbors have no order
3. max-pooling: involves a projection matrix and activation function and element-wise max operation. 

## neighbor sampling

currently, it's uniform sampling. 

sampling bounds the memory and run time, otherwise memory can become `O(|V|)`. 

## mini-batch training

just sample a batch of nodes (line 3 of Algorithm 3)

# experiment

citation and reddit data 

- with text features, used word embedding to get the document embedding
- also some node statistics faeture like degree

the task is multi-class classification

## generalization across graphs

- training set: 20 gene networks (trained together)
- test set: 2 other gene networks
- task: multi-class classification

# references

- https://arxiv.org/pdf/1706.02216.pdf
- T. N. Kipf and M. Welling. Semi-supervised classification with graph convolutional networks.


