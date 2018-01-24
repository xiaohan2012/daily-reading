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
- calculate the similarity of tree sampling distributions on cut/loop_erased random walk
  - on the same small graph as in the `random_steiner_tree` package
  - [ ] the tree edges are assigned probability
  - [ ] unweighted version

- [ ] approximate query selection (with two different levels of approximation, candidate pruning fraction and nodes-for-estimation fractions)
  - so two figures (each legend correspond to a different fraction)
- [ ] time difference and final average precision score to run 100 queries on different approximation configurations
  - maybe a table of two dimension on each approximation choices

- [X] exclude queried node
- [ ] change to IC model in experiment
- [ ] assign edge probabilities in experiment

# sunday

- [ ] approximate query selection (with two different levels of approximation, candidate pruning fraction and nodes-for-estimation fractions)
  - so two figures (each legend correspond to a different fraction)


# monday

- [X] run on order-steiner-tree greedy
- [X] evaluation result on order-steiner-tree

```
processing cascade/grqc/47.pkl started, query_method=pagerank, inference_method=order_steiner_tree
0th query raises AssertionError
```

meeting summary:

- cigdem will fix the theory part
- for me:
  - implement the weighted tree version
  - implement with resampling part
  - different settings (cascade model, cascade size, graph topology) try to produce a bigger difference
  - are cut and loop-erased random-walk giving the same probability?
  

# Thursday

- sampling algorithm with edge weights (how to evaluate the correctness? assign 1 and epsilon to two adjacent edges) (2h)
- [ ] a shell script that varies on fraction of *infected nodes/observed nodes* 0.01, 0.02, 0.04, 0.08, 0.16, 0.32 (0.5h)
  - [ ] run it 
- approximated prediction-error based query strategy
  - [ ] script 1: varying the number of nodes used for estimation
  - [ ] script 2: varying the number of nodes that are filtered 
  - [ ] plot 1: a plot that gives the average precision score vs iteration on different approximation schemes (vs the full scheme)
  - [ ] plot 2: a bar plot showing the time difference
- [ ] check the proof again, try to interpret the intuition (seriously)   (1h)
- [ ] [Detecting Large Reshare Cascades in Social Networks](https://research.fb.com/wp-content/uploads/2017/04/sansnet-www17.pdf) (2h)
