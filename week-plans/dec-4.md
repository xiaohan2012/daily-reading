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

- frog: [ ] read the non-uniform random spanning tree generation (1.5h)
- [ ] understand the discussion (0.5h)
- [ ] create an illustration and finalize the proof (1h)
- [ ] cikm 2017 (0.5h)
- [ ] `maintain` (1h)
- [ ] `greedy` (1h)
- [ ] python interface and try on karate graph (1h)
- [ ] discussion with Lorenzo (1h)



