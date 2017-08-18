# eigenvector diagonalization

define:

- $`A`$: `n` by `n` matrix with `n` linearly independent eigenvectors
- $`S`$: matrix with eigenvectors as columns
- $`\Lambda`$: the eigenvalue diagonal matrix

then: 

$`S^{-1} A S = \Lambda`$

proof by $`As=\lambda s`$, where `s` is one column in `S`.

note that:

1. in order to have $`S^{-1}`$, $`S`$ needs to contain `n` **independent** columns. in other words, the eigenvalues need to be distinct.
2. non-uniqueness of `S`: because any eigenvector multiplied by any non-zero constant is still a eigenvector
   - a special case, for `A=I`, eigenvalues are all 1s, eigenvectors spans the whole space of $`\mathbb{R}$n`$
   - therefore $`S^{-1}IS=I`$ for any invertible `S`


## when diagonalization fails?

in order to make diagonalization succeed, $`S`$ needs to be invertible, in other words, $`S`$ contains **enough independent** eigenvectors. 

**shortage of eigenvectors** leads to failure to diagonalization. 

note that repeated eigenvalues is a **necessary but insufficient** cause for such failure:

- for `I`, it has repeated eigenvalues but it's diagonalizable because it's already diagonal
- for $`\begin{pmatrix} 3 && 1 \\ 0 && 3 \end{pmatrix}`$, eigenvalues are 3s but eigen vectors are `[c 0]` (dependent

$`\lambda=0`$ does not mean such failure. for example:

$`\begin{matrix} 1 && 0\\ 0 && 0 \end{matrix}`$

- eigevalues: `[1, 0]`
- eigenvectors: `[1 0]` and `[0 1]`

## invertibility and diagonalizability on eigenvalues/eigenvectors

invertibility and diagonalizability: not directed actually

- diagonalizability depends on having enough eigenvectors
- invertibibility depends on non-zero eigenvalues
  - $`det(A) \neq 0`$ leads to invertibibility
  - $`det(A)=\prod_i \lambda_i`$