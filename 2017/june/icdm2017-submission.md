# Reconstructing a cascade from temporal observations

# for minimum steiner tree: proof of factor-2 for MST approach


basic idea:


1. `c(MST-based solution)`
  - because redundant edge removal
2. `c(MST on metric closure)`
  - because MST is the **minimum** spanning tree
3. `c(Hamiltonian path)`
  - by short cutting and metric property of metric closure
  - short cutting uses the edges in metric closure
4. `c(Eulerian trail that visits each terminal)`
  - because of edge removal
5. `c(Eulerian graph that repeats each edge in T* twice)`
  - because of the doubling
6. `2 OPT`

- point 1 < point 2 < ... < point k
- `c` is the cost
- `OPT` is the optimal solution value

**just learned**

- why doubling the edges to construct Eulerian graph?
  - because of the Eulerian graph, we can construct the Hamiltonian path.

## for minimum order steiner tree: proof of factor-sqrt(k) 

basic idea of proof (follows the proof of the previous one):

- however, we split the terminals into groups (to preserve order constraint) and construct a tree from root to them separately.
- meanwhile, for each subtree, its cost is upper-bounded by `2OPT`
- **then the question is**:
  - what's the maximum number of groups we can have?
  - `sqrt(k)` proved by Lemma 1


# factor-k proof for greedy

algorithm:

sort the terminals by time and add a path from one terminal to the tree at each iteration

proof idea:

- for each added path, its length is smaller than `c(T*)`
- at most `k` paths are added
- so factor-k

# factor-k proof for delay-bfs

algorithm:

proof idea:

- tree cost <= sum of tree depth at each iteration (iteration i is during ith node being added)
- to be continued


# learned

- Eulerian trial: path that visists each **edge** in graph exactly once
  - for tour/circle, start and end nodes are same
- Eulerian graph: graph that contains Eulerian trial
- Hamiltonian trial: path that visists each **node** in graph exactly once
- one way to deal with variant of steiner tree problems using the MST heuristic
- to prove factor-k, decompose into each iteration and prove the cost added by each iteration is smaller than OPT