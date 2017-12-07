# week plan

## core maximization


code

- [ ] visualize the result (added edge, red)
- [ ] exhausive search (2h)
- [ ] experiment on grqc graph
- [ ] present result to Lorenzo and Francesco (1h)


## active learning

- [ ] closure version, how to assign the edge weights? is it equivalent to the wilson's algorithm
- coding Wilson's variant

## paper reading

# monday

- [X] frog: if correct, make the algorithm and proof formal (wilson's variant) (2h)
  - [X] try to understand equivalence between cycle popping and LERW again
  - [X] the probability part, why `\sum P(C)` is a constant? 
  - if possible write down the confusions, let's discuss with Cigdema and Aris
- [X] https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture5.pdf (1h)
- [ ] fix bug in `treap.remove` (1h)
- [X] abstract reading cikm (0.5) 
  - get the main idea and take down notes

## frog

`\sum_C P(C) = 1` because of probability theory

formalized the idea in [this](december/sampling-steiner-tree-using-cycle-popping.md)

## markov chain reading

december/thomas-random-walks-and-markov-chains.md

## "bug" in `treap.remove`

cannot understand the `Treap` code. just avoided the bug without fixing it. 

need to under how node insertion/deletion works for binary search tree.

# Tuesday

- frog: hardness proof, if correct, make it formal
  - [X] prove that adding more than 1 edges increase node's core number by at most 1 
  - [X] prove that adding the target edges is the most beneficial than adding other edges
- [X] https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture6.pdf (1h)
- [X] cikm 2017 (0.5h)
- [X] `initialize`: init all the data structures (1.5h)
- [X] `candidate-edge` (1h)
- [X] meeting (1h):
  - show the experiment result
  - present the scalability idea (monotonicty and incremental update)
  - wilson's algorithm

## discussion

next:



# Wednesday

- [X] frog: think about incremental update (reusing information) and make it formal (1h) 
  - understand what's used in the mccalum's paper
- [ ] reuse the steiner trees (1h)
  - both query and inference algorithm
  - speed comparison for inference algorithm
- [X] https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture7.pdf (1h)
- [X] `best-edge` (1h)
- [ ] `greedy` (1h)
- [X] cikm 2017 (0.5h)
- [X] lorenzo discussion (1h)

## frog

december/mccallum-incremental-training.md

idea basically the same

## discussion

need to make sure that after removing its neighbors, set nodes and stub nodes, its degree is bounded. 

# Thursday

- frog: [X] read the non-uniform random spanning tree generation (1.5h)
- [X] understand the discussion (0.5h)
- [X] create an illustration and finalize the proof (1h)
- [X] cikm 2017 (0.5h)
- [ ] `maintain` (1h)
- [ ] `greedy` (1h)
- [ ] python interface and try on karate graph (1h)
- [X] discussion with Lorenzo (1h)

## frog

december/non-uniform-random-spanning-tree-on-weighted-graphs.md

## viz

- https://docs.google.com/drawings/d/1zkugV1PaxpSsJWV1-sakt7csSHwk2q9k5EdVvUe0u8M/edit
- https://docs.google.com/drawings/d/1ntHYlC7aq7XJWZcSTSmoH8xBxnTnMwaw8rkWGK-1Gl8/edit
- https://docs.google.com/drawings/d/1-dvVDV8IxJJfAv89GXO7zBhaEuy4wosw5hyXk24LdPc/edit

## greedy code

inserting intra-core edges, should return a new component id

`fakeinsert`, the new nc id that should be returned

- for inter-core edges, it's added to the nc of the high end node
- for itner-core edges:
  - if all nodes in nc are updated, nc id can remain either the same or to the new nc id
  - if not all nodes in nc are updated, then a new nc is created. 

let's just re-run the core-guided bfs for simplicity

# Friday

- [ ] frog: formalize wilson's algorithm and proof (1.5h)
- [ ] non-uniform random spanning tree, automaton theory (1h)
- [ ] polish the proof, specify which nodes' core are increased and how much, which nodes' core stay the same (1h)
- [ ] `maintain` (1h)
- [ ] `greedy` (1h)
- [ ] python interface and try on karate graph (1h)
- [ ] cikm 2017 (0.5h)
