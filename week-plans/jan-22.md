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

- [X] implement weighted version of sample steiner tree
- [X] re-read the proof on cut (1h) and loop erased random walk (1h)
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

- [X] sampling algorithm with edge weights (how to evaluate the correctness? assign 1 and epsilon to two adjacent edges) (2h)
- [X] shell scripts that varies on fraction of *infected nodes/observed nodes* 0.01, 0.02, 0.04, 0.08, 0.16, 0.32 (0.5h)
  - [X] gen cascades
  - [X] run it 

- [X] check the proof again, try to interpret the intuition (seriously)   (1h)



## weighted sampling

evaluated correctness of loop-erased on `<>`-graph. the case is actually a spanning tree, 

more to do:

- [ ] how to have edge pointing from root to children?
  1. it's good to have edge pointing from root to children
  2. however, the tree returned by LERW is pointed to the root



# Friday

- [ ] run inference on different cascade size
- [ ] plot the average precision score for different cascade sizes
- [ ] command support for approximation scheme in `generate_queries.py`
- [ ] save the running time as well in `sumulator.py`
- approximated prediction-error based query strategy
  - [ ] script 1: varying the number of nodes used for estimation
  - [ ] script 2: varying the number of nodes that are filtered 
  - [ ] plot 1: a plot that gives the average precision score vs iteration on different approximation schemes (vs the full scheme)
  - [ ] plot 2: a bar plot showing the time difference
- [ ] measure the similarity (to proved distribution ) of the probability distribution for both `loop_erased` and `cut`
  - on a small grid graph (with weights)
  - on a fork graph (`<><><>` this kind of shape): we can enumerate all steiner trees there
- [ ] [Detecting Large Reshare Cascades in Social Networks](https://research.fb.com/wp-content/uploads/2017/04/sansnet-www17.pdf) (2h)


## fb interview
 
- what are experimental design skills
- what's my current research
- what I want to work at fb
  - understand how information propagates, build mathematical model to capture cascades
  - make inference/prediction on cascade: what kind of cascade
  - design event detection algorithms (what's an event)
- [data science questions](https://www.glassdoor.com/Interview/Facebook-Data-Scientist-Interview-Questions-EI_IE40772.0,8_KO9,23.htm)

Research Methods (Pirate): This tests your empirical research methods, machine learning and experimental design skills. We will ask about real situations you can encounter in Facebook – questions a product manager might ask. you may be asked to come up with a strategy and design for the research project from start to end.”
 
Research/Background (Jedi): Dive into your research and background. Good to be able to discuss your research in a cogent way and articulate what you want to work on at Facebook. They sometimes ask you to code up a short algorithm as well.

Statistics (Ninja): This portion of the interview asks questions about probability and statistics basic topics


