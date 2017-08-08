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


