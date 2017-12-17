# plan

## core maximization

hardness proof:


- [ ] if so, write down the proof (1h)

edge addition method: 

- [ ] think about: given a subgraph, how to determine the number of edges (or lower-bound) to increase the core (1+1 hr)
  - how to define such subgraph? subcore?
  - possible direction: based on degree from higher order nodes? my previous thinking? based on the finger prints?


- [ ] ask feedback from Aris (1h)
- [ ] meeting with ISI (1h)

coding:

- [ ] (Cython tutorial)(http://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html) (1h)
- [ ] [language basics](http://cython.readthedocs.io/en/latest/src/userguide/language_basics.html#language-basics) (2h)
- [ ] python interface to `glist` using Cython (1h)
- [ ] translate the greedy algorithm in Cython and Python (3h)
- [ ] translate test cases from google test to Python (2h)

## active learning


- [ ] organize the document, problem motivation, formulation, method and properties (if the method has) (2h)
  - we have three methods
  - using KDD template
- [ ] integrate loop erased random walk with the current code (1h)
- [ ] code the sample and truncate algorithm in Boost Python and integrate it with the current code (2h)
- [ ] how to measure probability distribution on combinatorial structures, read the bridging state paper (1h)
- [ ] measure whether the loop erased random walk obeys the desired distribution (2h)


# monday

- [ ] frog: check if the fix (2h)
  - using the frequency bounded version of set cover
  - when compansating edges, consider node-wise and use degree `(c_{max}+2)` or core to upperbound the number of edges. 
  - solves the following: 
    - a node's core might increase if we don't constrain the edges being added
    - make sure that selecting sets do not mistakenly include extra elements. 
- [ ] read Section 6 and 7 of "random spanning tree using coupling from the past" paper  (2h)
  - how to deal with unrooted tree using the cycle popping technique
- [ ] transitive closure documentation (1h)
  - algorithm, method, things to prove
- [ ] code the loop erased random walk in Boost Graph and Boost Python (2h)
  - so that a graph is passed in and a tree/efilter is returned
- [ ] cikm 2017 (0.5h)


30 hours (4 days)