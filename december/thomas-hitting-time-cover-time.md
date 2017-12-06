# hitting time and cover time of random walk

- https://resources.mpi-inf.mpg.de/departments/d1/teaching/ws11/SGT/Lecture7.pdf

# def

- hitting time: `H(u, v)` expected length of random walk that starts from `u` and visits `v` for the first time
- `C(u)`: expected length of random walk to visit all other nodes for the first time
- cover time `C=max_u C(u)`

# main theorems

**Theorem 7.2** cover time of graph upperbounded by `O(n^3)`

proof using:

- `H(u, v)` for edges
- it takes more time to cover a spanning tree than the supergraph that contains it

**Theorem 7.3** exact formula for cover time

proof techniques:

- markov inequality, union bound

**Theorem 7.5** cover time for regular graph `\Theta(n^2)`

the proof technique might be useful

**Theorem 7.6** exact formula for `H(s, t)` (**important**)

related to eigenvalue and eigenvectors. 

**Theorem 7.7** Random target lemma

the probability of visiting some vertex is independent of the starting vertex

