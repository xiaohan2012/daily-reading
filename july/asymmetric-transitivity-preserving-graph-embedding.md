
# intro

focus on **directed** graph

- transitivity is symmetric in undirected graphs but asymmetric in directed graphs
- *asymmetric transitivity* assumes: given links `u -> v` and `v -> w`, there tends to be a link `u -> w` (but not the opposite direction)

# goal

capture

1. asymetric transitivity
1. higher order proximity: nodes connected via long path can be similar as well
   - intuition -- the *more* and the *shorter* paths between u and v, the more similar they are
  
# problem

two embeddings for one node: as a source and as a target, `U_s` and `U_t`

minimize ||S - U_s U_t^T||^2

- S is the proximity matrix: defined later
- a matrix factorization problem

# higher order proximity 

defines `S` in **common form** `S=M_g^{-1} M_l`

## Katz proximity

- `S = \sum_k=1^\infty \beta \beta^l A^l`
- closed form: `(1-\beta A)^{-1} \beta A`

intrepretation, emsemble of all paths

idea similar to GraRep

# algorithm

directly solving the problem on `S` is time consuming because `S` can be very dense` (matrix product)

because `S=M_b^{-1} M_l`, the method proposes running SVD on `M_b` and `M_l` separately. 

## others

- rooted pagerank
- common neighbors

# learned

- various proximity measures such as Katz, rooted pagerank and their general form
- symmetric transitivity does not always hold (especially for directed graphs)
- use two separete embedding space for source and target respectively
  - reduces to SVD
- partially generalized SVD for scalablity (but with error): `O(mK)`, `m` number of non-zero entries and `K` embedding dimension
- experiment result is very good (compared to line and deepwalk)

