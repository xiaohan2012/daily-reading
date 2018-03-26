# main tasks

- understand and experiment with the cross entropy method
- learn on proving inapproximability
- think, validate, code the edge-dag method


# monday

- [ ] code: understand and experiment with the cross entropy method
- [ ] read: learn on proving inapproximability
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