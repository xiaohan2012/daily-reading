# SVD from linear algebra book

# definition

given m by n matrix `A`, find `U`, `sigma` and `V` such that:

`A=U \sigma V'`

- `U`: m by m orthogonal matrix
- `V`: n by n orthogonal matrix
- `\sigma`: diagnonal matrix


# properties


## eigen vectors/values

- columns of `U` are eigen vectors of `AA'`
- columns of `V` are eigen vectors of `A'A`

to see why, consider

`AA' = U\sigma V V\sigma U' = U \sigma^2 U'`

also, `\sigma` is the sqrt of the eigen values of `AA'`

## row/column/null space

- first `r` columns of `U`: column space of `A`
- last `m−r` columns of `U`: left nullspace of `A`
- first `r` columns of `V`: row space of `A`
- last `n−r` columns of `V`: nullspace of `A`
- `r` is the rank


# applications

- data compression (images): take the significant eigen vectors (based on eigen values)
- network embedding learning

# computing SVD

using QR algorithm on `AA'` and `A'A`


# recap

- orthogonal matrix `M`: `M M^T = diagonal matrix`
  - also orthonormal matrix `M M^T=I`
- eigenvector decomposition: `M=Q diagonal Q'`
- QR algorithm: for orthgonal decomposition (Gram-Schmidt orthogonalization)