# goals

- def and prop of orthogonal matrices `Q`: 
  - inverse is tranpose
- solution to `Qx=b`
  - just $` Q^T b `$
- Gram-Schmidt process for factorization `A=QR`


# definition


**orthonormal vectors**: $`q_1, \ldots, q_n`$ are orthonormal if 

$`q_i^T q_j`$

- `=1` if `i=j`
- `=0` otherwise (orthgonal)


if `Q` (square or rectanglar) has **orthonormal columns**, then $`Q^T Q=I`$

- $`Q^{-1} = Q^T`$ (left-inverse)

## examples of orthnogonal matrices

- rotation matrix: `[c, -s; s, c]`
- permutation matrix

## multiplication preserves length 

`||Qx||=||x||`

proof:

 `||Qx||^2=||x||^2`

## orthonormal square matrix

its transpose is also orthnormal

# solving `Qx=b`

$`x = Q^{-1} b = Q^T b`$

in other words, $`x_j = q_j^T b`$, `q_j` jth column

another way to see it, think about the following problem:

find the coefficients $`x_1, \ldots, x_n `$ of the basis vectors: $`b=x_1 q_1 + \ldots + x_n q_n`$

where `q_1, ..., q_n` are orthonormal vectors., 

then multiplying both sides of the equation by `q_j^T` gives:

$` q_j^T b = x_j q_j^T q_j `$

then, $`x_j=q_j^T b`$, exactly the solution to `Qx=b`

# least square

for `Q` of size `m x n`, where `m>n`, using the normal equations: $`A^T A x = A^T b`$, we get:

$`x=Q^T b`$

by using the properties. 

so least square is much easier

# Gram-Schmidt process

## vector projection (recap)

project `a` on `b`

the angle $`\theta`$ between a and b is given by

$`cos \theta = \frac{a^Tb}{|a||b|}`$

then, the projected vector length is:

$`|a| cos \theta = \frac{a^T b}{|b|}`$

then the projected vector is length times unit vector of `b`

$`\frac{a^Tb}{|b|} \frac{b}{|b|} = \frac{a^T b}{|b|^2}b`$


## project `b` on orthonormal vectors `q`

for orthonormal vectors, $`|q|^2=1`$ , therefore the projected vector is

$`(b^T q) q`$


## orthognolize vectors

rule of thumb: 

1. for each row, subtract it with its projections on previous rows (orthogonalize)
2. normalize it

consider three vectors `a, b, c`, we "make them orthonormal".

for the first one, just normlize it $`q_1=\frac{a}{|a|}`$

for the second one, it needs to be orthognol to `q_1`. we substrat `b` by the component that is parallel to `q_1`. like the following

$`B = b - (q_1^T b) q_1`$

that component is essentially the projection of `b` on `q_1`

then we normalize it:

$`q_2 = B / |B|`$

similar for `c`, we subtract two projections from it.

$`C= c - (q_1^T c) q_1 - (q_2^T c) q_2`$

so from `a, b, c`, we get `q_1, q_2, q_3`

in other words, from `A` to `Q`


# `A=QR`

what the relation between `A` and `Q`?

- `a` is its projection on `q_1`
  - $`a=(q_1^T a) q_1`$
- `b` is the sum of its projection on `q_1` and `q_2`
  - $`b=(q_1^T b) q_1 + (q_2^T b) q_2`$
- `c` is the sum of its projection on `q_1`, `q_2` and `q_3`
  - $`c=(q_1^T c) q_1 + (q_2^T c) q_2 + (q_3^T c) q_3`$


![viz](https://ibin.co/w800/3X3jTrXxg241.png)




