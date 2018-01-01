- [Generating random spanning trees more quickly than the cover time](http://dl.acm.org/citation.cfm?id=237880)
- [Faster generation of random spanning trees](https://people.csail.mit.edu/madry/docs/randtreegen_full.pdf)
- [Random Walks and Random Spanning Trees](https://math.dartmouth.edu/~pw/math100w13/kothari.pdf): contains Wilson algorithm
- [How to Get a Perfectly Random Sample from a Generic Markov Chain and Generate a Random Spanning Tree of a Directed Graph](http://www.sciencedirect.com/science/article/pii/S0196677497909172)
  - [exact sampling with coupled markov chains](https://www.stat.berkeley.edu/~aldous/206-RWG/RWGpapers/propp_wilson.pdf)
- [Non-uniform random spanning trees on weighted graphs](http://www.sciencedirect.com/science/article/pii/S0304397598003259)

# intro

problem: given a graph, *uniformly* sample a spanning tree

two categories of method:

- determinant based: from `O(m n^3)` to `O(n^{2.376})`
- random walk based: `O()`

# background

random walk

- hitting time of node v and u: expected number of steps to hit u starting from v
- cover time of v: expected number of steps to visit all nodes starting from v

# derterminnant based

using the fact that \# of spanning trees = determinant of the adj matrix

but what's the algorithm?

# random walk based

main theorem: by using random walk method, the tree is uniformly distributed (by Broder and Aldous)

## Andrei Broder algorithm

1. randomly select a node
2. do random walk from it
   - whenever a new node is visited, add the node and the visited edge to tree
3. continue until all nodes are visited

running time bounded by expected cover time:

- `O(n^3)` (worst case)
- often `O(n logn)`

better running time by Wilson (Generating random spanning trees more quickly than the cover time): bounded by hitting time

# questions

- how is cover/hitting time calculated?


# learned

- cover time: time to visit all nodes
- random walk based random spanning tree algorithm