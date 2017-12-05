# week plan

## core maximization

code

- [ ] `best-edge` (1h)
- [ ] `maintain` (1h)
- [ ] `greedy` (1h)
- [ ] exhausive search (2h)
- [ ] experiment on dolphin graph (2h)
- [ ] experiment on grqc graph
- [ ] present result to Lorenzo and Francesco (1h)


## active learning

- [ ] reuse the steiner trees (1h)
  - both query and inference algorithm
- [ ] run grqc 500 rounds with 500 samples (0.5h)
- [ ] think about incremental update (reusing information) and make it formal (2h) 
  - understand what's used in the mccalum's paper
- [ ] closure-based sampling, what's the challenge to prove probability distribution (1h)
- [ ] reading
  - https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture7.pdf (1h)

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

- closure version, how to assign the edge weights? is it equivalent to the wilson's algorithm
- formalize wilson's proof
- read the non-uniform random spanning tree generation. 