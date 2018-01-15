# plan

## NetFill experiment for KDD submission and SDM paper

- [ ] learn how to run NetFill
- [ ] Python interface for NetFill (2h)

## SDM paper

- [ ] report experiment on small datasets
- [ ] case study on small datasets	
  - graph topology visualization
  - node states viz

## KDD submission

goal: by next Friday.

- experiment comparing different query strategies
- experiment comparing different sampling strategies
- the algorithm/implementation is optimized

- [ ] writing for query stretagy part 
- [ ] unify the inconsitent sampling problems


## core maximization

goal: some algorithm inspires from the optimal solution on karate club (based on subcore algorithm)

- [ ] state the difference between version with given candidate set of edges and with the complementary edge set 
- [ ] subcore algorithm: after matching as many nodes, what to do with the rest unmatched nodes? how to maximize the gain?


# monday

- [X] ML coffee talk (1h)
- [X] frog: profile code for entropy method (1h)
  - what's the bottle neck, optimize it? (?h)
- [X] review optimizing scalability using lazy evaluation (0.5 h)
- [X] is it appliable to entropy/prediction error method (0.5 h)
- [X] if applicable, state it in the document (0.5h)
- [X] meeting (1h)
  - current progress
  - scalability issue
- [X] extract the subgraph of the karate club and investigate what's the case of the optimal solution for greedy (1h)
  - could subcore algorithm be applied to this case?


## profiling entropy method

- unstable:  the tree sampling can take a long time, can we just set time out for early stopping
  - what's the reason for this?

the main bottle neck is sampling a steiner tree

**incremental tree sampling** 

instead of sampling a tree from scratch, we can sample a new tree based on previously sampled trees (the trees might not be valid for the current observation)

for example, 

- if the queried node is infected, we can attach this node to the current tree (assuming the tree does not contain it)
- if the queried node is uninfected, we just moreve this node from the current tree (assuming the tree contains it)

**observation**

the first node takes a longer time connect and it also gives larger standard deviation

## meeting summary

- [X] pure version with no approximation
- [X] experiment on smaller graphs

## optimal solution structure

- core-3 node connects to 3 nodes in core-4
- core-4 has two nodes with degree < 5
- two edges give the boost, even though there is not inter-core edges



