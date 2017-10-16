# applications

- distance query in graph
- frequent itemset mining (dense bi-clique)
- compress graphs by finding bi-clique

# density functions

edge density, edge ratio, triangle density, etc

# min-cut and max-cut

- min-cut: polynomiall solvable for max-flow (min-cut/max-flow theorem)
- max-cut: NP-hard

for edge density algorithm:

- goldberg algorithm: transform to min-cut, binary search
- charikar algorithm: peeling algorithm, faster and easier to implement
  - turns out to be a corner stone for many other problems/algorithms

## edge surplus framework

defines a general objective function that covers many denisty functions. 

`f(S)=g(e[S]) - h(|S|)`

main theorem: if `g(x)=x` and `h(x)` is concave, then it's polynomially solvable. 

# streaming/dynamic graphs

different focus:

- streaming: focus on space
- dynamic: update and query time

main papers (from worst to best):

- Densest subgraph in streaming and mapreduce., VLDB 2012
- Densest subgraph in dynamic graph streams., 2015
- Space-and time efficient algorithm for maintaining dense subgraphs on one-pass dynamic streams, STOC 2015


