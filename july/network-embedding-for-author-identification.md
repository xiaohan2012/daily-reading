# Task-Guided and Path-Augmented Heterogeneous Network Embedding for Author Identification

[paper](http://dl.acm.org/citation.cfm?id=3018735)

# goal

given an anonymized paper, return a ranked list of authors of the paper.

# prelimilary

in a heterogenous network, a paper is represented by:

- a set of neighbouring nodes grouped by their type, such as keyword, venue, year, etc
- and a list of authors of the paper

notations:

- `U`: embedding

# problem

given a set of papers (represented a above) and the corresponding authors, 

learn a model that ranks the authors so that the true authors are ranked top.

# model

training objective consists of:

- supervised learning objective 
- network-based smoothing objective 
- regularizer

## task specific

modeled as a supervied machine learning problem where label = 1 if the target is the actual author and 0 otherwise. 

given the embedding `u` for each non-paper node, paper's embedding is built-up  by:

1. for each neighboring type, take the mean within that type (using embedding parameter `u`)
2. for each mean vector, take the weighted linear combination (using weight parameter `w`)

score between paper and author = dot product between paper and author

hinge loss ranking objective: `max(0, f(p, a') - f(p, a) + c)`

- related to maximum margin learning, `f(p, a)` should be at least `c` larger than `f(p, a')`. gaurantees quality

## network structure smoothing

similar to word2vec

important steps:

- normalize **each** meta-path augmented adjacency matrix (de-bias)

## meta-path selection

different meta-path contribute differently to the final identification performance, 

method used here: 

1. for each meta-path, evaluate it alone 
2. sort the above and incrementally add one at a time
3. use cross-validation to select the best combination

## experiment

1. pre-training from network smoothing used

# questions

- what's negative sampling? 
  - is it possible that an actual edge is sampled as negative? seems like so
  - [more on word2vec](https://www.youtube.com/watch?v=ERibwqs9p38&t=941s)
- asynchronous SGD
  - how is the parameters updated? 
- why as a ranking problem? why not multi-label classification?
  - too many labels?
- why using dot product? 

# learned

- using embedding and vector similarity function to solve learning to rank problem
- connection between multi-label classfication and learning to rank
  - learning to rank + score threshold / k (the top-"k")  ~= multi-label classification
- benefits of hinge loss
- one usual requirement of embedding: to preserve proximity (w.r.t network topology)
- one framework for supervised nework embedding, two main components
  - supervised component: training labels, embedding and some architecture
  - network topology: inducing similarity from edges
  - general to incorporate multi-task
