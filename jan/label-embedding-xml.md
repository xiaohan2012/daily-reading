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

# papers on learning on bipartite graphs

- [Graph Convolutional Matrix Completion, arxiv, 2017](https://arxiv.org/pdf/1706.02263.pdf): ued graph autoencoders
- [Supervised Bipartite Graph Inference, NIPS 2009](https://papers.nips.cc/paper/3428-supervised-bipartite-graph-inference.pdf)
- [Scalable Metric Learning for Co-embedding, ECML PKDD, 2015](https://pdfs.semanticscholar.org/79eb/875562967957abbbfce54a079b38195a5794.pdf)

# related questions

- Given a graph, where certain nodes have features while some does not, how to learn the embedding?
  - can we adapt the formulation of GraphSage to this setting?