# properties of determinant

1. `det(I) = 1`

2. two rows changes lead to sign flip of det

3. det depends linearly on the first row

4. if two rows are equal, the det = 0
   - try row exchange

5. subtracting one row on others lead to det unchanged
   - linear dependence

6. zero rows lead to det = 0
   - try add some numbers to the zero row (linear dependence)

7. if A is triangular, det = product of diagonals
   - by gaussian (back) elimination, det does not change
   - and linear dependence, `a11 a22 ...ann det(I)` (linear dependence)

8. singularity leads to det = 0
   - gaussian elimination leads to zero rows

9. `det(AB) = det(A) det(B)`
   - proof?

10. det A^T = det A

# computing determinant

## first way: permutation

determinant can be decomposed into matrices such that:

- for each matrix, each row in it has only one non-zero entry
- the non-zero entries are all from different columns
- in other words, each matrix corresponds to a permutation/re-ordering of `1...n`
  - so there are `n!` such matrices

the decomposition is due to properties of determinant

big formula:

`detA = \sum_{all P} a_{1 p1} a_{2 p2} ... a_{n pn} detP`

- `p1, ..., pn` one permutation/reordering
- `detP=1 or -1`  for even/odd exchanges

## second way: cofactor (recursive)

in the first row, for each element `a_ij`:

- take the remaining `n-1 by n-1` submatrix by:
  - removing the first row and `j`the column, denoted as `A_1j`
- `detA` can be decomposed into `a11 C11 + a12 C12 + ... + a1n C1n`
  - `C1j = (-1)^{1+j} det(M_1j)`
  - notice the recursion

## third way: pivot

using triangular facrorization:

`det A = det LDU  = det L det D det U = \prod pivot_i`

# applications of determinant

## computing $`A^{-1}`$



formula:

$`A^{-1} = \frac{C^T}/\text{det} A`$

to see why:

denote:

- `C = [C_11, ..., C_1n; ...; C_n1, ..., C_nn]`

then:

`AC=diag([det A, ..., det A)`

becaue `\prod_k a_ik C_ij`:

- `=det A` if `i=j` (diagonal)
- `=0` otherwise (off-diagonal), because of they are duplicate rows

page 248

## solution of `Ax=b`

aka Cramer's rule:

the jth solution:

$`x_j = \frac{\text{det} B_j}{\text{det} A}`$

`B_j=A with jth column replaced by b`

proof: 

1. using `x=A^{-1} b= C^T b / det(A)`
2. the jth element in `C^T b` is `\sum_i C_ij b_i`, which is exactly `det B_j`


## volume

to get the volume of a matrix, think of each row as an edge (vector pointing to certain direction of certain length)

### volumn and determinant for orthogonal matrix



then consider the simple case, a orthogonal matrix, whose rows are orthogonal to each other. 

denote the length of each column is `l_i`,

then `A A^T = diag(l_1, ..., l_n)`

take determinant operator, it gives `det(A) = \prod l_i`

in other words, the volume of an orthogonal matrix equals the product of its vector/edge lengths


### volume for general matrix

we need to orthogonalize it by using Gram-Schmidt process:

- for each row, orthogonalize it by substracting it by its projections on the preceding rows
- no need to normalize as what's done in Gram process

this leaves us orthogonal rows. 

### formula for pivot

observation: first k pivots are only determined by the first k rows and columns

this is because the nature of row elimination

in other words, $`A_k = L_k D_k U_k`$

then:

$`d_k = \frac{det(A_k)}{det(A_{k-1})}`$

ratio of determinants. 