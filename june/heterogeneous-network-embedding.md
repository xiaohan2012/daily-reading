# Heterogeneous Network Embedding via Deep Architectures, KDD 2015

- [video](https://www.youtube.com/watch?v=ZpyzyyXHx6A)

# setting

- a graph of two node types (text and image), three edge types (inter and intra)
- text and image itself has unique content information (raw image and tfidf vector)

# objective function

- linear map: map text and image (of different input vector length) to the same latent space by two linear mappings (two matrices)
- non-linearity map: for each node type, one encoder to transform the input to some embedding
  - this is before the linear map
- loss function defined according to binary logistic regression
  - `log (1 + exp(A_ij sim(xi, xj)))`
  - `sim(xi, xj)`: inner product of the latent vector
  - one loss function for each edge type
  - plus regularization term

# parameters

- parameters for each non-linear map
- parameters for the linear map


# learned

- a way to encode edge information via embedding and pairwise similarity
- [softmax](https://en.wikipedia.org/wiki/Softmax_function): exponential normalized by sum of exponentials
- content + link + non-linearity gives better result
- application of embedding: classification, clustering , information retrieval (similarity function)
- it can address out-of-samples: because of the neural networks, the method can calculate embedding for unseen samples

# questions

- the baselines do not seem strong
- retrieval results not very good ("Cow")
- what about visualization result? do we need more specific methods?



