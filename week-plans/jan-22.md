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

**kdd2018**

weighted 

- [ ] implement weighted version of sample steiner tree
- [ ] re-read the proof on cut (1h) and loop erased random walk (1h)
- [ ] calculate the similarity of tree sampling distributions on cut/loop_erased random walk
  - on the same small graph as in the `random_steiner_tree` package
  - the tree edges are assigned probability

- [ ] approximate query selection (with two different levels of approximation, candidate pruning fraction and nodes-for-estimation fractions)
  - so two figures (each legend correspond to a different fraction)
- [ ] time difference and final average precision score to run 100 queries on different approximation configurations
  - maybe a table of two dimension on each approximation choices

- [ ] design and verify the temporal loop-erasing random walk 
- [ ] try to prove probabilistic property of temporal loop-erasing random walk using a similar approach

side note:

- should consider `IC` model because tree probability is the product of the edge probas

# sunday

- [ ] approximate query selection (with two different levels of approximation, candidate pruning fraction and nodes-for-estimation fractions)
  - so two figures (each legend correspond to a different fraction)



# monday




