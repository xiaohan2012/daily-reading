# Heterogeneous Network Embedding via Deep Architectures, KDD 2015

- [video](https://www.youtube.com/watch?v=ZpyzyyXHx6A)

# setting

- a graph of two node types (text and image), three edge types (inter and intra)
- text and image itself has unique content information (raw image and tfidf vector)

# objective function

computation workflow

1. given texts and images, derive their raw features, `x_i` and `z_i`
   - `x` and `z` might be of different dimension
   - the features are derived with a blackbox, might be some non-linear models
2. linear transform them into the same dimension by `x' = Ux` and `z' = Vz`
3. loss function defined according to binary logistic regression
   - `log (1 + exp(A_ij sim(xi, xj)))`
   - `sim(xi, xj)`: inner product of the latent vector
   - one loss function for each edge type
   - plus regularization term


## parameters

- parameters for each non-linear map, the neural network parameters
- parameters for the linear map, `U` and `V`


# learned

- one-sentence summary: representational learning with network regularization
  - smoothing done via *binary logistic regression* (similar or not)
    - not so intuitive
  - reminds of the paper [topic modeling with network regularization](http://www-personal.umich.edu/~qmei/pub/www08-netplsa.pdf)

- a way to encode edge information via embedding and pairwise similarity

- [softmax](https://en.wikipedia.org/wiki/Softmax_function): exponential normalized by sum of exponentials

- experiment shows: content + link + non-linearity gives better result

- application of embedding: classification, clustering , information retrieval (similarity function)

- it can address out-of-samples: because of the neural networks, the method can calculate embedding for unseen samples (inductive learning)

# difference to skipgram-style papers

- random walk is constrained to be 1-hop (edges)

# questions

- the baselines do not seem strong
- retrieval results not very good ("Cow")




