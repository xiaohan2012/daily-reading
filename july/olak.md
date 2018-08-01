# OLAK: An Efficient Algorithm to Prevent Unraveling in Social Networks

# problem and overview

anchor `b` nodes such that the size of `k`-core is maximized

# solution

greedy approach: anchor one node that produces the max. number of *followers* (nodes that move into `k`-core due to the anchoring )

## observations

1. only `(k-1)`-shell plus their neighbors are anchors that might have some followers
2. only nodes in `(k-1)`-shell can be followers: this narrows down the search space for finding followers


# sub problems

important notion: onion layer,`L_0, \ldots, L_K` , which:

1. consists of nodes in `(k-1)`-shell plus their neighbours
2. groups nodes within by the deletion order during k-core decomposiion
3. note that the neighbor nodes are in `L_0`l

## finding the candidates

candidates = nodes in onion layer
- note that 
- stated in Theorem 2
- Algorihtm 3 does that

intuition:

1. nodes in `(k-1)`-shell may have followers
2. if anchoring `v`, where `v` is linked to `u` from the shell, it's possible that `u` follows

## finding followers given node `u`

support path from `u` to `v`: if edge `(x, y)` on the path satisfies `l(x) < l(y)`, `l` is layer index in `L`

Thereom 4: for `v` to be follower of `u`, it's a **necessary** condition to exists a support path from `u` to `v`

implication: we can start anchoring lower-layer nodes



# relation to our problem

our problem seems "quite" different from this one in two ways:

- adding edges vs anchoring nodes
- objective function is different

we might consider studying scalable algorithm for edge version of k-anchored problem, as it is a smoother transition from this problem

