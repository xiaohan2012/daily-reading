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
- k-truss on author-paper graph
  - common "co-author": there is at least a path of type `A-P-A-P-A`
  - what is a good k-truss community for citation network?

# Wednesday

- problem: how to assign edges to partitions so that task can be done efficiently
  - actually, there is no choice in assign to which partition. each task/edge can be assigned to only certain partition(s) (one or two)
  - so the scheduling policy can be: assign edge/task to corresponding partition whenever it's idle

- insertion in batches (distributed setting): group the edges such that the lower end point are in the same core
  - constraint: each touched lower end point has exactly one adjacent edge being inserted (this makes sure the core change is at most 1)
  - this generalizes the case of star network, edges within the same core  
  - benefits: 
    1. low communication cost in sending edges and updating cores (because they are in batches)
    2. low core computation cost (shown in the `(n-1)`-clique example)

- cases where core change > 1
  - if for `u`,  multiple `(u, v)` are inserted and `v \afer u`, then `\Delta core(u)` can be larger than 1
  - in this case, affected nodes can be in other cores, which might introduce communication cost
  - can we do better using batch insertion? centralized and distributed setting?
    - centralized setting: have some example that is a linear-factor faster. 
    - *question*: what's the algorithm for centralized setting in this case?

- other questions to consider: 
  - what are the nature of edge insertion?
  - core number are should be distributed by power law, this affects how to partition the data. how should it be done?
    - for nodes with small core, they should be further partitioned by community (this should be auto-detected by core composition order)
    - *question*: how to partition the nodes so that nodes' neighbors which have similar core number are in the same partition? state the motivation and formulate the problem. 

- discussing with Cigdem:
  - guided simulation for sampling steiner trees
  - using time