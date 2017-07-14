# blog post on word embedding by Sanjeev Arora

- [1](http://www.offconvex.org/2015/12/12/word-embeddings-1/)
- [2](http://www.offconvex.org/2016/02/14/word-embeddings-2/): not fully understood yet

question: how to represent words into lower-dim space?

one useful assmption -- Firth's hypothesis

- "you shall know a word's meaning by the company it keeps"
- quite vague still but relies on **word-cooccurence** statistics

# examples

- the first two methods attempt to approximate the cooccurence statistics (frequency)
- they are linear models

## Latent Semantic Indexing (LSI)

underlying assumption: similar words should have large similarity score (measured in dot product)

find word vectors `v_1, v_2, ...v_N` that minimizes

- \sum_ij (M_ij - v_i \dot v_j)

essentially low-rank approaximation, SVD

why should it work?

## Latent Semantic Analysis (LSA)

- reweigh `M_ij` in LSI by log
- other reweighing exists such as square root, TF-IDF, etc
- corresponds to weighted SVD
  - generally NP-hard
  - [possible approximation by EM](https://people.csail.mit.edu/tommi/papers/SreJaa-icml03.pdf)

## CBOW (one version of word2vec)

length-l tuple (consecutive words), maximize the *difference* between:

- `exp(v_w 1/l \sum_i v_wi)`: `v_wi` are the contextual words
- same formula but for negative samples (randomly selected words as tuples)

# non-linear embedding models

- simplest version: PMI, `log(p(w, w') / (p(w)p(w')))`
- word2vec
- glove

how are they related? what are the commonality and differences?

# learned

- the bigger picture: many embedding models are based on coccorrence statistics
  - differences might lie in: how the statistics are reweighted
  - what model is used? linear? non-linear?
- LSI and LSA: variants of SVD
  - weighted SVD is NP-hard
- why low dimension is better than high dimension?
  - intuitive explanation: high dimension introduces overfitting. in other words, lower dimension is kind of regularizer