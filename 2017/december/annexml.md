# AnnexML: Approximate Nearest Neighbor Search for Extreme Multi-label Classification

# overview

it uses the same generla idea as SLEEC, however in comparison to SLEEC, it improves:

- graph construction for training data (using both label and feature)
- embedding learning (ranking-based intead of low-rank based)
- prediction (using approximate k-nearest neighbor search)

# problem with SLEEC

## recap of SLEEC

training:

- partiion training data using features (for faster prediction)
- inside each partion, build kNN graph of training data using label vectors
- learn embedding for each training point (low-rank matrix factorization)
  - note that they do not assume the label matrix is low-rank but the kNN graph is low-rank
- then learn projection matrix (feature -> embedding)

prediction:

- assign test point to the nearest cluster (using feature vect)
- project the feature into embedding
- find top-k nearest neighbors inside the cluster
- get the labels

## potential issues

1. data clustering: only uses input features, not the labels (points with similar labels might not be in the same cluster)
2. prediction is based on KNN (order matters, not the distance values)
   - not sure what it means
3. prediction time: 8 ms (SLEEC) vs 0.5 ms (FastXML)
   - this is just empirical, without complexity analysis (could be due to the implementation details)

# motivation

**for problem 1:**

build a k-nearest neighbor graph (KNNG) of training points from the *label vectors* (not the feature vectors?).

and partition the grpah into subgraphs (cut based?)

**for problem 2:**

learn embedding for each subgraph using ranking-based objective (intead of regression based)

how?

**for problem 3:**

using approximate k-nearest neighbor search instead of linear search

# details

globel picture: an ensemble of learners, each learner represents one partition of the data points. 

## partitioning

1) build k-nearest neighbour graph on the label vectors

naive approach, `O(N^2)`. 

- using inverted index (label -> data points)
- ignore some head labels to avoid `O(N^2)`

in contrast to SLEEC, which performs k-means on feature vectors

2) linear seperator (`w_c`) learning and partitioning

there `K` partitions, therefore `K` partition vector to learn. 

for each data points `i`, take its nearest partition `j`, update `w_j` so that `i` closer to `i`'s neighbours while further to other points. 

space complexity: `O(KM)`. feature hashing [25] is used to reduce it.

**short summary**

to partition the data using *both label and feature information*, they did:

- KNNG construction using *label vectors* (with bias on tail labels)
  - determine which nodes are similar to each other ("similarity" labels)
- partition the *feature vectors* using the above KNNG as weak supervision. 
  - sequentially maximization procedure that updates the partition vector, `w_c`

an interesting way to partition the data. 

## embedding learning

in SLEEC, embedding is learned via low-rank matrix approximation. 

here, it learns embedding that should **predicts its neighbors** in KNNG. 

**note that**

- SLEEC uses the projected vector to retrieve top-k neighbors during prediction, however, this is not learned directly
- in this paper, the top-k part is modeled explicitly.

objective is similar to "word2vec", in terms of prediction probability:

- using cosine similarity: scaled to `[-1, 1]`, no need to add extra regularization term
- using `exp` and `\gamma` to scale the value

learning projection matrix is done by linear regression

- the parameter to learn here is the regression matrix `V_c`
- the embdding `z` is computed by multiplying `V_c` with `x`

## prediction

1. uses ball tree for approximate nearest neighbor search. 
2. then uses the KNNG to retrieve the neighors in the graph and refine the top nearest neighbors. 

some detail:

1. it uses Euclidean distance because it's metric, which is important for ball tree
2. cosine distance is not metric 

# learned

in general:

- building KNN graph: label vectors as weak supervision
  - interesting way to partition data: by learning `k` linear separators using the above KNNG
- embedding learning via word2vec-style approach
- approximate nearest neighbor search trades speed with accuracy (therefore, it uses KNNG search to remedy this)
  - also shown in Table 4

ensemble:

- the more the learners, the better the performance (Figure 1)
- for experiment, it's important to set the number of learners to equal for different methods

experiments:

- it's almost impossible to perform the best on *all* datasets
- it's necessary to compare the method with/without the improvement. 
- what to compare:
  - best performance on different datasets
  - improvements of different parts (justification of the method)
  - prediction speed


# links

- [source code, in C](https://github.com/yahoojapan/AnnexML)


# my thinking

- the basic idea: use k nearest neighboring training points to predict the labels of the test point.
  - can we avoid this?

