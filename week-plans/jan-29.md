# weekly plan

**core maximization**

randomly remove 

- [ ] implement subcore algorithm
  - using maximal matching (2-approximation to maximum matching)
  - [networkx implementation](https://networkx.github.io/documentation/networkx-1.10/reference/generated/networkx.algorithms.matching.maximal_matching.html#networkx.algorithms.matching.maximal_matching)

- [ ] compare greedy and subcore on grqc dataset


experiment setting:

- remove a random set of edges from the original graph
- use these removed edges as the candidate edges

**kdd 2018**

- approximation on estimated node samples
- run one larger dataset using approimation
- 

# monday

- [ ] compare the probability distribution of cut and loop-erased against a small network (2h)
  - random graph with 6 nodes (connected), with random edge weight (0 to 1.0)
  - 2 fixed terminal nodes (randomly selected), fixed root
- plot the average precision score on (1h)
  - [X] different cascade size 
  - [X] different approximation schemes
- meeting (1h)
- my research and what to work on (1h)
- summarize the two FB papers I have read (what I have learned, what's the question they aim to answer)



todo:

- get the running time of s0.16 and without pruning

intuition: 2 mins for 0, 56 secs for 0.05

## meeting

- the summation part: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.294.9956&rep=rep1&type=pdf the weighted cut algorithm
- https://www.math.ubc.ca/~barlow/preprints/106_ust_survey.pdf cycle popping part
- why random so good?
  - root sampling strategy by posterior distribution, pagerank, distance
  - steiner tree sampling using edge weights
  - more graphs
  - more cascade models
- theorem 2 and theorem 1 as special case
- root direction semantic

## discussion with Cigdem

- [ ] realized tree probability is *proportional* to `\prod w(u, v) / w(u)`
- [ ] check the proof again

