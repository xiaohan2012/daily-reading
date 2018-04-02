# main tasks

- understand and experiment with the cross entropy method
- learn on proving inapproximability
- think, validate, code the edge-dag method


# monday

- [ ] code: understand and experiment with the cross entropy method
- [X] read: learn on proving inapproximability
  - follow the MIT video
- [X] think: re-think edge-dag method
  - [X] run it on small examples
- [ ] skim: one cascade prediction paper

## notes on edge-dag

needs to prove the following:

1. there cannot be any pending edges that become parent of new edge node (either remaining as pending edge or form a new edge node)

2. given an new edge node, the set of dependent edges `(u, v)` are those:
   - adjacent to one of the promoted nodes, `u`
   - and has `core(u) \le core(v)`

# tuesday

- [X] follow the MIT video
- [X] think: prove the claims in core-max
- [X] code: experiment with the new method
  - much worse than greedy on grqc
  - possible reason 1: introduces unnecessary dependent edges (check the single edge and where it's in the DAG)
  - possible reason 2: `inc_weighted_gain` should be updated as edges are being selected
- [X] code: investigate why lattice-1024 gives bad result
- [X] code: new eval measures
- [ ] skim: one cascade prediction paper


## wednesday

- [ ] why lattice-1024 gives bad result?
- [ ] are there edge groups that create synergic effect?


## why lattice gives bad result

several unclear observations:

1. `g_norm` produces steiner trees with **larger** sizes than those by `g`
  - and queries from `g_norm` are more far-away than the infection region

2. 