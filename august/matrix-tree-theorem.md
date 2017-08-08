
# notations

- a graph `G` has `p` nodes and `q` edges

- adjacency matrix: `A` (p by p), `A_ij` number of edges between `v_i` and `v_j` 

- incidence matrix: `M` (p by q), `M_ij=`
  - `1` if `e_j = (v_i, *)`
  - `-1` if `e_j = (*, v_j)`
  - 0, otherwise
  - each column has one 1, one -1 and `q-2` 0s

- laplacian matrix: `L` (p by p), `L_ij=`
  - `-A_ij` if `i != j`
  - `deg(v_i)` if `i = j`

# lemmas

## lemma on determinant

given matrix `A` (m by n) and `B` (n by m), 

- if `m > n`, then `det(AB) = 0`
- if `n < m`, then `det(AB) = sum_S det A[S] det B[S]`

## lemma (a)

`M M^T = L`

- `(M M^T)_ij = \sum_k M_ik M^T_kj = \sum_k M_ik M_jk`
  - if `i=j`, `M_ik M_jk = M_ik^2`, summation of over it counts the number of edges incident to `i`
  - if `i != j`, then if there is a edge `k` connecting `i` and `j`, then `M_ik M_jk=-1`

## lemma (b)

if `G` is `d`-regular (every  node has degree `d`), then `L = dI - A`

## lemma on detM and is spanning tree or not

- denote `M_0` as the incidence matrix with the last row removed, therefore it's `p-1` by `q`
- given a set of `p-1` edges, `S`, the corresponding submatriz of `M_0` is `M_0[S]` by keep the columns corresponding to `S`

the lemma says:

1. if `S` is not a spanning tree, then `det(M_0[S]) = 0`
2. if `S` is a spanning tree, then `det(M_0[S]) = 1 or -1`

for 1, an example is 4 node graph with nodes 1...4, a non spanning tree is `1-2`, `2-3` and `1-3`. 

in this case `M_0[S]` is 

```
   [ 1,  0, -1
    -1,  1,  0
     0, -1,  1]
```

adding up the rows produces a zero row, thus the det is zero (by property of determinant)

for 2, the matrix can be re-ordered into a bi-diagonal matrix where the diagonal matrix is one. 

# main theorem


## theorem 1

let `L_0` be the laplacian with the last row and column removed, then

`det(L_0) = number of spanning trees for G`

- `L_0 = M_0 M_0^T` by lemma (a)
- `det (L_0) = det (M_0 M_0^T)`
  - `= \sum_S det(M_0[S]) det(M_0^T[S])` (lemma on determinant)
  - `= \sum_S det(M_0[S])^2` (transpose does not change determinant)

## theorem 2



# questions

- is it true that `det L_0 = det L`?
- what about undirected/directed graph?

# learned

- degree of nodes: number of edges it's incident to.
  - if the node has only one edge, its degree is one
- 