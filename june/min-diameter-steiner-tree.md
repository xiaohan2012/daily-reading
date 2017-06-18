
# Algorithms for the minimum diameter terminal Steiner tree problem

focus on complete metric graph

# concepts

- terminal steiner tree problem
  - constraint that each terminal is the leaf of the tree
  - metric cost: constant factor
  - non-metric: no known constant factor
- minimum diameter spanning tree problem
  - metric case: polynomially solvable,
  - non-metric case: equal to absolute 1-center problem, also polynomially solable.
- minimum diamter steiner tree problem (MDSP)  
- minimum diameter terminal steiner tree problem (MDTSTP)
 - all terminals are leaves of the tree
- shortest steiner path tree
- absolute 1-terminal steiner center


- steiner path
  - only two ends of the path *can* be terminal nodes
- one-to-all shortest steiner path tree (one-to-all shortest path tree), `TT(v)` and `T(v)`
  - from v to all other nodes
- one-to-many shortest steiner path tree (one-to-many shortest path tree), `TT_S(V)` and `T_S(V)`
  - from v to all other steiner nodes
- **points** of edge and graph  
- absolute 1-steiner center
  - point that minimizes the maximum length of shortest path from point to terminals  
- vertex 1-steiner center: vertex instead of point
- absolute 1-terminal Steiner center
  - considers steiner path, more restricted
  - the center is a steiner point (not terminal)
- vertex 1-terminal Steiner center: similar

thinking:

- why absolute 1(-terminal)-steiner center?
  - if we can find such center, by their definition, we know the answer, just find the shortest path tree with this center as the root
-   

## theorem 1

interpretation:

1. for terminal steiner tree version, optimal solution is a one-to-many shortest *steiner* path tree, `TT_S(x*)`
  - `x*` is absolute 1-terminal steiner center
  - why *steiner path*? because problem requires terminals to be at the ends/leaves
2. for steiner tree version, optimal solution is one-to-many shortest path tree, `T_S(x*)`.
   - `x*` is absolute 1-steiner center
4. `x*` is the mid **point** of the longest leaf-to-leaf path in the tree.

- why middle?
- why point?

- a tree is monopolar if a vertex is the center
- a tree is dipolar if two vertices are centers

## theorem 2

optimal solution is either monopolar or dipolar

# algorithms

## complete graph with metric cost

- `L_i` stores all terminals sorted by lengths of all edges between terminal to `v_i`
  - sorted by edge length (because complete graph, so singular form)
- `L_i[k]`: the kth vertex in `L_i` (they call it `index`)
- `i(k)`: position of node  `v_k` in `L_i` (they call it `identifier`)
- `j_i^*(k)`:
  - first, take nodes from  `k+1` to `|S|-1` in `L_i`
  - then, consider the positions of the above nodes in `L_j`
  - return the one with maximum position
-   


# questions

- why metric helps? because of short-cutting?
- why complete graph?	    