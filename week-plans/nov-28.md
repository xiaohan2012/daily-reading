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

- [ ] frog: review ICDE, VLDB and the arxiv paper. what are possible good candidate edges? (1.5)
- [ ] what's wrong with november/quasi-clique-detection.md and the lemma in Section 5? (1h)
  - how could it be used?
- [ ] ask about feedback from Lorenzo by Francesco (0.5h)

afternoon:

- [ ] check `networkkit` (1h)
  - C++ interface: easy to extend?
  - comparison with `graphtool`: functionalities and usage
  - is ICDE 2017 code easy to integrate into `networkkit`?
- [ ] `core-decompose`: return core, degp, order (1h)
  - test with same examples
- [ ] `core-bfs`: BFS guided by core number (1h)
  - test with small examples
- [ ] meeting with Cigdem (1h)

20 h ~= 3 days