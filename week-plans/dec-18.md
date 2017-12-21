# plan

## core maximization

hardness proof:


edge addition method: 


- [X] ask feedback from Aris (1h)

coding:


- [ ] translate test cases from google test to Python (2h)

## active learning

- [ ] integrate loop erased random walk with the current code (1h)
- [ ] code the sample and truncate algorithm in Boost Python and integrate it with the current code (2h)



# monday

- [X] frog: check if the fix (2h)
  - using the frequency bounded version of set cover
  - when compansating edges, consider node-wise and use degree $`(c_{max}+2)`$ or core to upperbound the number of edges. 
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

[more](december/core-max-hardness-counter-example.md)

## code

- $`g._Graph__graph`$ gets the internal graph ($`graph_tool`$)
- todo: C++ interface for python to get the tree
  - [python code](https://graph-tool.skewed.de/static/doc/_modules/graph_tool/topology.html#random_spanning_tree)
  - [c++ interface code](https://git.skewed.de/count0/graph-tool/blob/master/src/graph/topology/graph_random_spanning_tree.cc)
  - [_get_rng](https://git.skewed.de/count0/graph-tool/blob/master/src/graph_tool/__init__.py#L3423)

## meeting 


# Tuesday

- [X] frog: cikm 2017 (0.5h)
- [X] C++ interface for python to get the tree (2h)
  - understand how $`graph_tool`$ works (0.5h)
  - adapt it to our case (1h)
- [X] produce a minimum working example, input: $`graph_tool.Graph`$, output: $`EdgeFilter`$ (0.5h)
- [X] how to measure probability distribution on combinatorial structures, read the bridging state paper (1h)
- [X] using KDD template
- [X] organize the document, problem motivation, formulation, method and properties (if the method has) (2h)
  - we have three methods

## measure probability distributipn on combinatorial structures

similarity/difference to true distribution. examples:

- cosine similarity $`p \widetilde{p} / \sqrt{||p|| ||\widetilde{p}||}`$
- or KL-divergence

one issue: should we enumerate over all combinatorial structures? I don't think so. 

# Wednesday

- frog: 
  - [X] counter-intuitive: if the weight is larger than 1, then it encourages larger trees? how to solve this problem? should we constrain to certain cases of weights? (0.5h)
  - [X] why *independence* between cycles popped and the tree? (0.5h)
  - [X] why the *equivalence* between cycle popping and loop erased random walk (0.5h)
- [X] think about: given a subgraph, how to determine the number of edges (or lower-bound) to increase the core (1+1 hr)
  - how to define such subgraph? subcore?
  - possible direction: based on degree from higher order nodes? my previous thinking? based on the finger prints?
  - [subcore algorithm](december/subcore-algorithm.md)
- [X] python wrapper (eliminate the type conversion stuff) (0.5h)
- [ ] measure whether the loop erased random walk obeys the desired distribution (1h)
- [ ] wrapper for steiner tree sample pool and refactoring (1+1h)
- [X] cikm 2017 (0.5h)

## frog

- the problem formulation does not match the result
- fix on probability distribution: which turns out to be not so intuitive now
- [ ] formalize it in document

30 hours (4 days)

# Thursday

- frog: 
  - [X] (Cython tutorial)(http://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html) (1h)
  - [X] [language basics](http://cython.readthedocs.io/en/latest/src/userguide/language_basics.html#language-basics) (1h)
- [X] cikm 2017 (0.5h)
- [X] example/illustration of the upperbound (0.5h)
  - background: def of subcore, results on subcore, why use subcore
- [X] understand how Cython is used for interfacing in networkit (1h)
- [X] python interface to $`glist`$ using Cython (2h)
  - function 1 `affected_nodes`: input -- graph, edge, output -- nodes affected
  - function 2: `insert_edge`: input -- graph, edge, output -- nodes affected, core numbers
  - function 3: `core`, the core numbers
- [X] meeting (1h)

## meeting

1. [ ] hardness
2. [ ] inapproximability
3. [ ] the problem version with one given node
4. [ ] computing how many edges are needed to promote a whole substructure

## subcore algorithm

- [update](december/subcore-algorithm.md)
- the upperbound is not tight as well
- defined another optiamization problem and proposed greedy solution. is it optimal?
- not sure why connecting within subcore. 

# Friday

- [ ] document my finding (independence and probability) (1h)
- [ ] communicate it to Aris and Cigdem (0.5h)
- [ ] the problem version with one given node (0.5h)
- [ ] wrap `NCComponent` in Cython (name should be `subcore`) (1h)
- [ ] test Cython `Glist`, `insert`, `remove`, `core` (0.5h)
- [ ] greedy without incremental update and test on toy example (1h)
- [ ] cut algorithm in Boost and interface with Python (2h)
- [ ] cikm (0.5h)


## 