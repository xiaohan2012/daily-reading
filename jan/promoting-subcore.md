# promoting subcore

two questions:

1. determine feasibility in polynomial time (whether a subcore can be promoted using candidate edges)
2. finding the optimal solution in polynomial time
  - related to the weighted version of max core problem
  - [ ] is this weighted version NP-hard?

given a subcore, we get the edge and node induced subgraph from candidate edge and `V(sc)`.

to determine the minimum number of edges required to promote `sc` (or to decide if it's possible), we first try to match as many `V_1` nodes as possible. 
   - we need to get a number here
   - also matching a node `u` might occupy chance of other node `v` beucase `u` might be able to connect to another external node, while `v` can only be promoted if using interior edges

For the remaining `v \in V_1 'cup V_2`, we check if we can connect to some higher order node using candidate edges or promote together some equal-lower core number node:

- if `\exists (v, u)`, where `c(u)>K`, then `v` can be promoted
- else if `\exists (v, u) \in E_c`, where `\deg^{>K}(u)=K-1, c(u)=K-1`, in this case: `u` will be promoted as well
  - or `\deg^{>K}(u)=K-2, c(u)=K-2`, there exists another `w \in V_1, V_2` and `(w, u) \in E_c`, in this case `u, w, v` will be promoted all together 
  - [ ] validate if this is the case for the optimal solution
  - this can be generalized to `m` edges
- else, it's impossible to promote it

