# 

[paper](https://www.youtube.com/watch?v=ERibwqs9p38&t=917s)

learning low-dimensional word vectors is not new. 

however, word2vec is simpler and faster. 


# model (skip-gram)


skip-gram: predict the context words conditioned on the center word

probability distribution for each word as center

objective function (for one document) to maximize: 

`\prod_{i=1..T} \prod_{-m <= j <= m} p(w_j | w_i; \theta)`

- document length: `T`
- window size: `m`
- embedding matrix: `\theta`

apply `- \log` gives:

- `-\sum_i \sum_j \log p`
- to minimize

# computing `p(w_j | w_i)`

`p(w_j | w_i) = exp(u_j u_i) / \sum exp(u_j', u_i)` (softmax function)


however, the denominator can be costly to compute. 

## negative sampling

just sample a few `w_j'` instead of use all. 

## hierarchical softmax

as an alternative to negative sampling to compute the above probability.


# learned

- [cross entropy loss](https://en.wikipedia.org/wiki/Cross_entropy)
  - takes the form: expectation of (-\log q) under p
  - in the problem: "expectation under p" is the empirical mean, `q` is given by the model
- review of softmax --- `p(w_j | w_i)`
  - exponential to make positive
  - normalize to give probability
- negative sampling


# uncovered

- why hierarchical softmax?
- how to do it in parallel