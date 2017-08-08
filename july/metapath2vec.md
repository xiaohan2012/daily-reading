# metapath2vec: Scalable Representation Learning for Heterogeneous Networks

[paper](https://www3.nd.edu/%7Edial/publications/dong2017metapath2vec.pdf)

# homogenous approach

ignore node types

examples: deepwalk, node2vec

disadvantages: 

- random walk is biased towards highly visible nodes 
- so less "popular" nodes are less often visited, thus embeddings for them are less accurate

by distinguishing nodes by types, the bias might be mitigated

for example, in panama-paper dataset, there are far many entities than officers and intermediaries.


# meta-path based random walk (heterogenous approach)

similar to skip-gram and deepwalk, but:

- the random walk process is guided by meta-path,
  - in other words, the visited node sequence should match type sequence encoded by the meta-path
  - for example, in Equation 3, transition probability is zero if edge type does not match

difference between metapath2vec and metapath2vec++: 

- lies in softmax function
- metapath2vec, the normalization term involve *all nodes* regardless of their types
- metapath2vec++: normalization term involve only nodes *with the same type*
  - `P_t(u_t)` in Equation (6) for ++ while `P(u_t)` for normal version. (negative sampling part)

# algorithm

1. for each node, select `w` meta paths of length `l`
2. each meta path corresponds to a "document"
3. loop through each path
  - take the current node as the center
  - and surrounding nodes as neighbors (within certain window size)


# difference with author identification paper

- softmax function (type-wise vs global)
- sampling procedure
  - metapath2vec: each metapath corresponds to a document and neighours are defined on such document
  - chen's paper: neighbours are defined by the destination od the meta path
  - so in metapath2vec, each metapath provides more training samples instead of one.

# questions

- which meta paths to select?
  - only one meta path can be selected as input
  - the paper selects the most popular ones by other papers
- is `N_t(v)` a set or multiset? if using multiset, coccurence can be captured because certain node pairs appear more often as neighbours than other nodes
- what's the intuition differentiating the softmax functions by type (`++` version)?
  - actually not explained well
  - also experiment result does not give clear preference

# learned

- network representation learning: 
  - common ingredients of NRL: skip-gram model
  - difference: how to define "neighbours"
  - example: 
    - deepwalk: random walk on homogenous graph
    - metapath2vec: add bias/guide to walk by constraining edge type

- another way to use sampled meta path: treats as document (as what's done in deepwalk)

- [hogwild-parallize SGD without locking](https://people.eecs.berkeley.edu/~brecht/papers/hogwildTR.pdf)
  - with theoretical analysis
  - used by this paper, however is not shown to work well with word2vec, may suffer from writing to the same piece of memory

- metapath2vec++ is not necessarily good than metapath2vec