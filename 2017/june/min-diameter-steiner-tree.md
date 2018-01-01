
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
  - `x*` is absolute 1-terminal steiner center: point that is close to every node (`min_x max_v d(x, v)`)
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
  - monopolar/diplolar steiner tree: `M_S(v)` / `D_S(v)`
  - monopolar/diplolar terminal steiner tree: `TM_S(v)` / `TD_S(v)`
  
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

basic idea for the terminal steiner tree version:
find both the best monopolar and dipolar trees and compare the two trees.

- for monopolar tree, iterate through each non-terminals and calculate the diamter of tree
  - how to ensure the node is mid point? why mid point? 

- for dipolar tree, iterate through all non-terminal pairs and caluclate the diameter based on the pairs
  - why not take the longest edge from each end of the pair and return it as the diameter?

# Tamir's paper

minimum diameter spanning tree on general complete graph (triangle inequality does not necessarily hold)

identical to 1-center problem (what's the problem?).




# questions

- why metric helps? because of short-cutting?
- why complete graph?
- why considering *point*?
  - because of the metric property? think of a plane of euclidean space, you consider point in this case
- mid point issue:
  - theorem 1 requires the root is the mid point of the longest path
  - interpretation: root is like the circle center
  - however, given the optimal tree, the root does not need to be the mid point
- absolute 1-center problem in euclidean space
  - aka. **smallest circle problem**: given a set of points on a plane, what's the best circle to cover these points?
  - can be solved in [linear time](http://www.personal.kent.edu/~rmuhamma/Compgeometry/MyCG/CG-Applets/Center/centercli.htm)



# summary

- considered two problems:
  - min diameter terminal steiner tree problem (MDTSTP)
  - min diameter steiner tree problem (MDSP)
  - **Note**: I only talk about MDTSTP, result for MDSP can be inferred similarly
- theorem 1:
  - optimal solution is the shortest steiner path tree with absoluate 1-terminal steiner center as the root
- theorem 2:
  - the optimal solution is monopolar or dipolar
  - monopolar means the root of OPT is a vertex
  - dipolar means the root of OPT lies in an edge (not the two ends)
- exact algorithm:
  - find best monopolar and dipolar trees respectively and compare them (**used theorem 2**)
  - for monopolar tree:
    - for each non-terminal `t`, find the two longest steiner paths to terminals and get their sum as the diameter rooted at `t`
    - take the non-terminal with maximum diamter
    - time complexity, **why log|S|**
  - for dipolar tree
    - consider each non-terminal pair, `v_i` and `v_j`, calcualte the diameter (tricky part)
    - for each `k`, consider using `L_i[k]` as one leaf connected to `v_i` and `L_j[j_i^*(k)]` as the other leaf connected to `v_j`
    - `L_j[j_i^*(k)]`:
      - filter: further than `L_i[k]` in `L_i`
      - max: furthest in `L_j`
    - **question**: why not just taking the two furthest nodes?



# min diameter ordered steiner tree

algorithm:

1. build the metric closure (directed), `G'`
2. find the min diameter spanning tree `T'` in `G'`
3. reconstruct the tree `T` from `T'`

if the second step can be solved optimally, then is `T` optimal?

attempted proof:

1. OPT
2. c(any leaf-to-leaf path in `T*`) (diameter)
3. c(longest short-cutted leaf-to-leaf path in `T*`) (metric property)
  - now the short cutted paths are in `G'`
  - why max? because the short-cutted diameter path might not the be the maximum, can even be smaller than diam(T')
4. diam(T') (by optimality)
5. diam(T) (edge removal)