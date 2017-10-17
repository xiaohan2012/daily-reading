- active learning
  - [X] understand the document
- core
  - [ ] what's the algorithm for equal/higher core edges
  - [ ] experiment the algorithm


# Monday

- questions about active learning document
  - method 2: why use an approximation if exact method is avaiable
- mutual information: $`H(X_{V-u}) - H(X_V) + H(X_u)`$
  - estimating $`H(X_V)`$: use sampled steiner tree
  - however, the steiner tree is not an accurate estimation of the possible trees
- meeting with Francesco
  - core mainteinance: properties in general (if each node has at most one incient edges being inserted)
  - check other papers
- DSD tutorial by Aris
  - a lot of approximation algorithms
  - for different definition of graph density and different settings, static, dynamic
- about life and work: no need to get trapped at local minimum, look far, think big

# Tuesday

- read paper densest subgraph in streaming and mapreduce
  - the 2-approximation
  - `\log n` pass (streaming setting)
  - mapreduce review
- possible extensions of k core decomposition project:
  - streaming setting
  - distributed setting
- shall we do distributed k-core mainteainance because not much work is done there.
  - can collaborate with Gianmarko
- observation (continue batch insertion)
  - the (n-1)-clique and n-clique example, reversing the edges insertion order reduce the time to `O(n^2 \log n)`
  - Francesco's assumption, for node with at most one adjacent inserted edge, `\Delta core(u) \le 1` does not hold
- discussion with Lorenzo
  - better have a problem statement before discussion
  - share the documentations