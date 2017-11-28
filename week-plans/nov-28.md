# week plan

## core maximization


algorithms to implement:

- `affected-nodes(G, e)`: list of affected nodes because of edge addition, related to ICDE 2017 paper (without change core number and change the `O` linked list) (1h)
   - `find-nc`: together with `affected-nodes`, return the nc id that the affected nodes should move to
- `initialize`: init all the data structures (1h)
- `candidate-edge` (1h)
- `best-edge` (1h)
- `maintain` (1h)
- `greedy` (1h)

thinking:

- [ ] np-hardness of the core maximization problem (2h)

## active learning project

faster steiner tree sampling:

- [ ] understand Wilson's paper: https://www.cs.cmu.edu/~15859n/RelatedWork/RandomTrees-Wilson.pdf (3h)
- [ ] understand boost implementation http://www.boost.org/doc/libs/1_65_1/boost/graph/random_spanning_tree.hpp (0.5h)
- [ ] does the same lemma (determinant) hold if we terminate the algorithm when all terminals are visited? (2h)


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

- [ ] frog: integrate `core-decompose` of ICDE to networkit C++ (3h)
  - compile/build networkit
  - change the code (graph object) in ICDE to the classes in networkit C++
  - expose the properties (core, deg+, order) to Python using Cython
  - test with small examples
- [ ] understand Wilson's paper: https://www.cs.cmu.edu/~15859n/RelatedWork/RandomTrees-Wilson.pdf (3h)
- [ ] `core-bfs`: BFS guided by core number in C++ (1h)



20 h ~= 3 days

