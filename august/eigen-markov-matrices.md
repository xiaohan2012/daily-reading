# example

each year, $`1/10`$ people outside of California move in and $`2/10`$ of people inside California move out.

captured by the **markov matrix**:

$`A=\begin{bmatrix}0.9 && 0.2 \\ 0.1 && 0.8 \end{bmatrix}`$

then the process is:

$`u_{k} = Au_{k-1}`$

or 

$`u_{k} = A^k u_0`$

where $`u_0 = \begin{pmatrix} y_0 \\ z_0 \end{pmatrix}`$

# markov process

caputured by markov matrices, with two properties:

1. each column sum up to 1 (no body is lost or gained)
2. no negative entries (probability should be non-negative)


# solving $`u_{k} = A^k u_0`$

1. solving $`det(A-\lambda I) = \lambda_2 - 1.7 \lambda +0.7`$ gives $`\lambda_1=1, \lambda_2=0.7`$
2. this gives $`S=\begin{bmatrix} 2 & 1 \\ 1 & -1 \end{bmatrix}`$ and $`S^{-1}=\begin{bmatrix} 1/3  & 1/3 \\ 1/3 & -2/3 \end{bmatrix}`$

**note** that the text book gives different $`S`$, still, the decomposision $`S \Lambda S^{-1}`$ gives the same result $`A`$. (it take me a while to verify)

substituting $`A=S \Lambda S^{-1}`$, $`u_k = S \Lambda^k S^{-1}`$ gives

$`(y_0 + z_0) \begin{bmatrix} 2/3 \\ 1/3 \end{bmatrix} + (y_0 - 2 z_0) (0.7)^k  \begin{bmatrix} 1/3 \\ -1/3 \end{bmatrix}`$ 

the second term diminishes, therefore, 

$`\begin{bmatrix} y_{\infty} \\ z_{\infty} \end{bmatrix} = (y_0 + z_0) \begin{bmatrix} 2/3 \\ 1/3 \end{bmatrix}`$ (**steady state**)

the steady state corresponds to the eigenvector of $`\lambda_1`$

## properties of markov matrices

1. $`\lambda_1=1`$ is an eigenvalue of $`A`$
2. the other eigenvalues $`\lambda_k<1`$
3. eigenvector $`x_1`$ is the steady state because $`A x_1 = x_1`$ (after the transition, it does not change)

note that:$`\lambda_1=1`$ is because:

1.  each column of $`A`$ sums up to 1, 
2. therefore $`A-I`$ has each column sum up to zero. 
3. therefore sum of all rows is zero vector, therefore rows are linearly dependent (singular)
4. therefore $`det(A-I)=0`$

## one person instead of a population

then $`A`$ can be thought as the probability that the person will be in California or outside.


# Stalability of $`u_{k+1} = A u_k`$

recall that $`u_k = \sum_i c_i \lambda^k x_i`$

therefore $`\lambda_1, \ldots, \lambda_n`$ deterins the stability. 

- for Fibonancci numbers, $`\lambda_1 = \frac{1+\sqrt{5}}{2} > 1`$,  and it's unstable
- for Markov matrices, $`\lambda_1=1`$, it's neurally stable
- for $`\lambda_1<1`$, it's stable. $`u_{\infty}=0`$

