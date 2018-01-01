# week plan

## core maximization


algorithms to implement:

- [ ] `initialize`: init all the data structures (1h)
- `candidate-edge` (1h)
- `best-edge` (1h)
- `maintain` (1h)
- `greedy` (1h)

thinking:


## active learning project

faster steiner tree sampling:


- [X] understand boost implementation http://www.boost.org/doc/libs/1_65_1/boost/graph/random_spanning_tree.hpp (0.5h)
- [ ] does the same lemma (determinant) hold if we terminate the algorithm when all terminals are visited? (2h)

experiment with larger dataset

- [ ] reuse the steiner trees (0.5h)
- [X] run grqc data (without improved scalability) (0.25h)
- [X] plot the result

think: 

- [ ] incremental update (1h)
  - upperbound the prediction error?
  - is the prediction error monotonically decreasing? if so, we can use lazy evaluation
  - can be apply the similar incremental techniques in optimal active learning paper?

# tuesday

- [X] frog: review ICDE, VLDB and the arxiv paper. what are possible good candidate edges? (1.5)
- [X] what's wrong with november/quasi-clique-detection.md and the lemma in Section 5? (1h)
  - how could it be used?
- [X] ask about feedback from Lorenzo by Francesco (0.5h)

afternoon:

- [X] check `networkkit` (1h)
  - C++ interface: easy to extend?
  - comparison with `graphtool`: functionalities and usage
  - is ICDE 2017 code easy to integrate into `networkkit`?

## frog

(two tighter underbounds for the core maximization problem)[november/core-maximization-and-core-mainteinance.md]


## what's wrong with the finger prints?

- for node with order $`i`$ in its $`nc`$, $`K-i+1`$ is a lower bound of $`\text{deg}^{+}`$ not an equality constraint. 

other:

1. being in $`k`$-core indicates the finger print ($`\ge`$ version)
2. however, does the reverse hold? no, because the $`i`$th node does not have to connect to all previous $`i-1`$ nodes? 

I think we still need some heuristic to guess. 


## networkit vs graphtool

- more contributors
- better documentation (better guides on integration)
- functionalities, similar
- built with `Cython` and without `Boost`

## `core-decompose`

mapping of the variable in pseudo code to variable in C++

- core -> `core`
- degp -> `node.rem`
- order -> `tree_`

# Wednesday

- [X] frog: integrate `core-decompose` of ICDE to networkit C++ (3h)
  - [X] compile/build networkit
  - [X] change the code (graph object) in ICDE to the classes in networkit C++
  - expose the properties (core, deg+, order) to Python using Cython
  - test with small examples
- [X] understand Wilson's paper: https://www.cs.cmu.edu/~15859n/RelatedWork/RandomTrees-Wilson.pdf (3h)


## frog

- learned got to know how to compile and test networkit code using `scons` and `gtest`
- changed the data types in ICDE code to match networkit

next step:

- compile the ICDE code using scons
- write test examples in gtest for `ComputeCore`
- make the test pass

## Wilson's paper

- got the idea of the algorithm
- but didn't understand the proofs

## comments on Cigmdent's comment

- similar to delay-bfs. tree building incrementally
  - connect to current tree or specific node?
- based on Wilson's algorithm?


# Thursday

- [X] frog: np-hardness of the core maximization problem (1h)
  - reduction from maximum set cover? promising
- [X] Wilson's paper (1h)
  - understand the probability proof
- [X] order-respecting steiner tree sampling algorithm based on Wilson's algorithm (1h)
- [X] CIKM 2017 paper skimming (graph related) (0.5h)
  - [here](november/cikm2017.md)
- coding (2h): 
  - [X] compile the ICDE code using scons
  - [X] write test examples in gtest for `ComputeCore`
  - [X] make the test pass
- [X] discussion with Cigdem (1.5h)
  - incremental steiner tree growing algorithm
  - scalability problem: complexity and ideas to reduce it

## Wilson's algorithm

for steiner tree, can we analyze the probability distribution using cycle-popping technique? 

# Friday

- [X] frog: NP-hardness (1h)
  - how to make sure only certain edges can be selected?
- [X] understand the probability proof and level stuff (1h)
- [X ] cikm papers selection (0.5h)
- [ ] plot the result (0.5h)
- [X] discussion with Lorenzo (1h)
  - np-hardness
- [X] `core-bfs`: BFS guided by core number in C++ (1.5h)
  - return a list of `nc`s and `nc_id`
  - test case
- [X] `affected-nodes(G, e)`: list of affected nodes because of edge addition, related to ICDE 2017 paper (without change core number and change the `O` linked list) (1.5h)
   - `find-nc`: together with `affected-nodes`, return the nc id that the affected nodes should move to
   - test case

## frog

- fixed the graph construction
- the other direction still to be proved

## wilson's algorithm


december/sampling-steiner-tree-using-cycle-popping.md

- cycle popping for steiner tree

next step:

- imagine explaining it to Cigdem

think about the following:

- needs to understand the equivalance between cycle popping and LERW
- does termination within finite time hold?
- does the probability distribution hold?


## discussion with Lorenzo

- prove that adding more than 1 edges increase node's core number by at most 1
- prove that adding the target edges is the most beneficial than adding other edges

## extra: prediction error monotinicity check

december/active-learning-prediction-error-monotonicity.md

# sunday

- [X] plan for next week (1h)
- [X] email for Sa's studio
- [X] look at housing (1h)
- [X] draw logo (1h)
- [X] video for dawei (3h+1h)

# summary

core maximization

- idea of proving np-hardness
- integrated ICDE code to networkit
- some other functions

active learning

- feasibility of closure based sampling
- using wilson's algorithm
- experiment on grqc dataset (prediction error based is the best w.r.t median however, need more rounds for stability)
- some idea on monotonicity
