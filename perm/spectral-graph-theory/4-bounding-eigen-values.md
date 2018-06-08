# bounding eigenvalues

http://www.cs.yale.edu/homes/spielman/561/lect04-15.pdf

# main points

- courant fischer theorem and its application to bounding eigenvalue ($`\lambda_2`$ for example)
- definition of positive semidefinite matrix, graph inequality and approximation
- using graph approximation to bound eigenvalues
  - speficically, use path inequality $`(n-1) P_n \ge G_{1, n}`$ (lemma 4.6.1)

# courant fischer theorem

the min-max and max-min relation

some intuition (on min-max): 

- *min* to make the **maximum** remaining space for the *max* part

# bounding $`\lambda_2`$ of  Laplacian matrix

first of all, $`\lambda_2`$ should be orthogonal to unit vector (by definition)

then some result on path graph $`P_n`$

$`\lambda_2(P_n) \le \frac{12}{n(n+1)}`$.

idea: use *test vector* which is orthnonal to $`\mathbb{1}`$

# graph inequality and PSD

positive semidefintite matrix $`A`$ -> $`v^T A t \ge 0`$ -> $`\lambda_1, \ldots, \lambda_n \ge 0`$

and $`A \ge B`$ if $`A-B`$ is PSD. 

using this, we define for graphs:

- $`G \ge H`$, if $`L_G \ge L_H`$

and if $`G \ge c \cdot H`$, then

$`\lambda_k(H) \ge c \lambda_k(H)`$, for all $`k`$


# graph approximation

$`H`$ is c-approximation of $`G`$ if

$`c H \ge G \ge H / c`$

**important theorem**: 

every complete graph $`K_n`$ can be $`(1+\epsilon)`$-approximated by a $`d`$-regular graph of $`n`$ nodes. 


# path inequality

$`(n-1)P_n \ge G_{1,n}`$, where $`G_{1, n}`$ has one edge $`(1, n)`$

this is very useful for bounding eigenvalues of some graphs!

examples:

1. lower bounding $`\lambda_2`$ of $`P_n`$:
2. lower and upper bounding $`\lambda_2`$ of $`T_n`$
