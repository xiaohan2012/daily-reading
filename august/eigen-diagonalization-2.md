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
   - a special case, for `A=I`, eigenvalues are all 1s, eigenvectors spans the whole space of $`\mathbb{R}`$
   - therefore $`S^{-1}IS=I`$ for any invertible `S`


## when diagonalization fails?

in order to make diagonalization succeed, $`S`$ needs to be invertible, in other words, $`S`$ contains **enough independent** eigenvectors. 

**shortage of eigenvectors** leads to failure to diagonalization. 

note that repeated eigenvalues is a **necessary but insufficient** cause for such failure:

- for `I`, it has repeated eigenvalues but it's diagonalizable because it's already diagonal
- for $`\begin{pmatrix} 3 && 1 \\ 0 && 3 \end{pmatrix}`$, eigenvalues are 3s but eigen vectors are `[c 0]` (dependent

$`\lambda=0`$ does not mean such failure. for example:

$`\begin{pmatrix} 1 && 0\\ 0 && 0 \end{pmatrix}`$

- eigevalues: `[1, 0]`
- eigenvectors: `[1 0]` and `[0 1]`

## invertibility and diagonalizability on eigenvalues/eigenvectors

invertibility and diagonalizability: not directed actually

- diagonalizability depends on having enough eigenvectors
- invertibibility depends on non-zero eigenvalues
  - $`det(A) \neq 0`$ leads to invertibibility
  - $`det(A)=\prod_i \lambda_i`$

## distinct eigenvalues

if all eigenvalues are distinct, then eigen vectors are linearly independent. 

example, given 2-by-2 matrix $`A`$, it has:

- eigen values $`x_1, x_2`$ 
- eigen vectors $`\lambda_1, \lambda_2`$

being linear independent means 

$`c_1 x_1 + c_2 x_2 = 0`$  (1)

for some non-zero $`c_1, c_2`$.

multiplying the above by `c_1 \lambda_1 x_1 + c_2 \lambda_2 x_2=0` (2)

subtracting 1 by 2 times $`\lambda_2`$ leads to $`c_1=0`$, which is a contraction for being non-zero

# complex eigenvalues/eigenvectors

example: 90-degree-rotation matrix:

$`K=\begin{pmatrix} 0 && -1 \\ 1 && 0 \end{pmatrix}`$

$`\text{det}(K - \lambda I) = \lambda^2 + 1`$

$`\lambda_1=i, \lambda_2=-i`$

for real matrices, they do not always have real eigenvalues, but there are always `n` complex eigenvalues. 

what does it mean to have imaginary parts in eigenvalues/vectors?

# $`A^k`$, $`A^{-1}`$ and $`AB`$

## $`A^k`$

for $`A^k`$, eigenvalues are $`\lambda_i^k`$, eigenvectors are the same. 

proof: $`A^k x = \lambda A^{k-1} x = \ldots = \lambda^k x`$

## $`A^{-1}`$

just $`\frac{1}{\lambda}`$ (if $`A`$ is invertible)

$`Ax = \lambda x \quad \rightarrow \quad \frac{1}{\lambda} x = A^{-1}x`$

## $`AB`$

if the eigenvectors are same for `A` and `B`, the eigenvalues are simply the product.

theorem: $`A`$ and $`B`$ share the same eigenvector matrix $`S`$ if $`AB=BA`$

one directin, if the share the same `S`, then $`AB=BA`$

suppose $`A=S^{-1} \Lambda_1 S`$ and $`B=S^{-1} \Lambda_2 S`$, then 

$`AB = S^{-1} \Lambda_1 \Lambda_2 S`$ and $`BA = S^{-1}  \Lambda_2 \Lambda_1 S`$

then $`AB=BA`$

the other direction, $`ABx=BAx=\lambda Bx`$

`x` and `Bx` are both eigenvectors of `A` sharing the same $`\lambda`$. 

therefore `Bx` is a multiple of `x`, in other words, `x` is eigenvector for `B` as well. so they share the same eigenmatrix `S`.





# learned

- eigenvalue diagonalization $`S^{-1}AS=\Lambda`$
- **necessary** condition for undiagonalizability -- repeated eigenvalues
  - however, repeated eigenvalues is not sufficient (identity matrix as a special case)
  - typical case for diagonalizability: distinct eigenvalues
- distinct eigenvalues lead to distinct independent eigenvectors
- condition for invertibility, nonzero eigenvalues
- eigenvalue for $`A^{k}, A^{-1}, AB`$
  - special treatment for `AB`, `AB=BA` to make sure the same eigenvectors are shared
