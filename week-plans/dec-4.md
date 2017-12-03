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

np-hardness (3h)

- [ ] prove that adding more than 1 edges increase node's core number by at most 1
- [ ] prove that adding the target edges is the most beneficial than adding other edges


## active learning

- [ ] reuse the steiner trees (1h)
  - both query and inference algorithm
- [ ] run grqc 500 rounds with 500 samples (0.5h)
- [ ] think about incremental update (reusing information) and make it formal (2h) 
  - understand what's used in the mccalum's paper
- [ ] closure-based sampling, what's the challenge to prove probability distribution (1h)
- [ ] meeting:
  - show the experiment result
  - present the scalability idea (monotonicty and incremental update)
  - wilson's algorithm
- [ ] reading
  - https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture6.pdf (1h)
  - https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture7.pdf (1h)


## paper reading

# monday

- [ ] frog: if correct, make the algorithm and proof formal (wilson's variant) (2h)
  - [ ] try to understand equivalence between cycle popping and LERW again
  - [ ] the probability part, why `\sum P(C)` is a constant? 
  - if possible write down the confusions, let's discuss with Cigdema and Aris
  - refer to [this](december/sampling-steiner-tree-using-cycle-popping.md)
- [ ] https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture5.pdf (1h)
- [ ] fix bug in `treap.remove` (1h)
- [ ] `initialize`: init all the data structures (1h)
- [ ] `candidate-edge` (1h)
- [ ] abstract reading cikm (0.5) 
  - get the main idea and take down notes