# problem formulation

1. learn label embedding such that labels that are co-occur together have similar embeddings
2. learn function that maps training instance to label embedding space, such that the mapped vector is "close" to embeddings of the label that the training instance has

# notation

input:

- $`\{x_i, y_i\}_{i=1, \ldots, N}`$, $`x_i \in R^M`$, $`y_i \in \{0, 1\}^L`$: $`M`$ num. features and $`L`$ num. labels
- we use $`l(x)`$ to denote the set of label indices $`x`$ has

- $`z \in R^{K}`$: label embedding of dimension $`K`$
- $`f: R^M \ rightarrow R^{K}`$

# approach

## label embedding learning

1. build label graph using label co-occurence statistics
2. apply graph embedding learning method to learn the embedding $`z`$

## learning $`f`$

formulated as a ranking problem: $`f(x)`$ should be able to predict its label vectors

training objective:


$`\sum\limits_{i=1,\ldots,N} \sum\limits_{j \in l(x)} \frac{sim(f(x_i), z_j)}{sim(f(x_i), z_j) + \sum\limits_{k \in S^{-}} sim(f(x_i), z_k)}`$

where $`S^{-}`$ is a set of negative label samples. 

- $`sim(a, b)`$: can be $`exp(cosine(a, b)`$ or $`exp(a \cdot b)`$ (inner product)

the function $`f`$ can be ConvNet, if the input data is texture data.


## prediciton

approximate nearest neighbor search on labels (eculidean distance, etc)

# motivation

- explicitly model label relation: easier to understand the result
- KNN needs to store all the training data embeddings and labels
  - here, we store label embeddings (still large, asymtotically the same for XML problems)
  - learn sparse embedding to save space and improve model?
- if there are more trainig data points, then prediction should be faster if we use label embeddings to compare against


# questions

- [ ] KNN is safe in the way that it incorporetas label frequency bias implicitly: how can we incorporate such bias?
- [ ] ensemble learning, how can produce an ensemble of learners?
  - as the negative samples are randomly selected, there is some randomness of each learner
- [ ] what if the constructed graph is not a connected component? only keep the largest cc?


# as a small project

todo:

- construct the label graph, check if they are connected component, if not, how many labels need to be dropped and frequency of such label
- the model, noisy contrastive learning + CNN
- start with [Wiki10-31K](http://manikvarma.org/downloads/XC/XMLRepository.html)


