# plan

## core maximization

hardness proof:


- [ ] if so, write down the proof (1h)

edge addition method: 

- [ ] think about: given a subgraph, how to determine the number of edges (or lower-bound) to increase the core (1+1 hr)
  - how to define such subgraph? subcore?
  - possible direction: based on degree from higher order nodes? my previous thinking? based on the finger prints?


- [X] ask feedback from Aris (1h)
- [ ] meeting with ISI (1h)

coding:

- [ ] (Cython tutorial)(http://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html) (1h)
- [ ] [language basics](http://cython.readthedocs.io/en/latest/src/userguide/language_basics.html#language-basics) (2h)
- [ ] python interface to `glist` using Cython (1h)
- [ ] translate the greedy algorithm in Cython and Python (3h)
- [ ] translate test cases from google test to Python (2h)

## active learning


- [ ] integrate loop erased random walk with the current code (1h)
- [ ] code the sample and truncate algorithm in Boost Python and integrate it with the current code (2h)
- [ ] measure whether the loop erased random walk obeys the desired distribution (2h)


# monday

- [X] frog: check if the fix (2h)
  - using the frequency bounded version of set cover
  - when compansating edges, consider node-wise and use degree `(c_{max}+2)` or core to upperbound the number of edges. 
  - solves the following: 
    - a node's core might increase if we don't constrain the edges being added
    - make sure that selecting sets do not mistakenly include extra elements. 
- [X] read Section 6 and 7 of "random spanning tree using coupling from the past" paper  (2h)
  - how to deal with unrooted tree using the cycle popping technique
- [X] transitive closure documentation (1h)
  - algorithm, method, things to prove
- [ ] code the loop erased random walk in Boost Graph and Boost Python (2h)
  - so that a graph is passed in and a tree/efilter is returned
- [ ] cikm 2017 (0.5h)


## frog

one counter example, 

a very large set of `n+1` elements (so `c_{max}=n`) and `(x, y_1)`, `(x, y_2)` `(x, y_3)`, `(x, y_4)`, ..., `(x, y_n)` and `(y_1, z_1)`, `(y_2, z_2)`, `(y_3, z_3)`, ... `(y_n, z_n)`

by our graph construction:

- also `x` receives `n-1` compensating edges (because of the `n+1`-element set)

suppose the set `(y_1, z_1)`, `(y_2, z_2)`, .. are selected. then:

- `x` has `n` higher order edges (one end of the edge is of a higher core), received from covered set

together, `x` has `2n-1` edges which the other end is in a higher core. 

therefore, even though `x` is not selected, its core number increases, which shouldn't happen.

## code

- `g._Graph__graph` gets the internal graph (`graph_tool`)
- todo: C++ interface for python to get the tree
  - [python code](https://graph-tool.skewed.de/static/doc/_modules/graph_tool/topology.html#random_spanning_tree)
  - [c++ interface code](https://git.skewed.de/count0/graph-tool/blob/master/src/graph/topology/graph_random_spanning_tree.cc)
  - [_get_rng](https://git.skewed.de/count0/graph-tool/blob/master/src/graph_tool/__init__.py#L3423)

## meeting 


# Tuesday

- [ ] frog: cikm 2017 (0.5h)
- [ ] C++ interface for python to get the tree (2h)
  - understand how `graph_tool` works (0.5h)
  - adapt it to our case (1h)
  - produce a minimum working example, input: `graph_tool.Graph`, output: `EdgeFilter` (0.5h)
- [ ] how to measure probability distribution on combinatorial structures, read the bridging state paper (1h)
- [ ] why *independence* between cycles popped and the tree? (0.5h)
- [ ] why the *equivalence* between cycle popping and loop erased random walk (0.5h)
- [ ] organize the document, problem motivation, formulation, method and properties (if the method has) (2h)
  - we have three methods
  - using KDD template

30 hours (4 days)
