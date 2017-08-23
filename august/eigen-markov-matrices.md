# example

each year, $`1/10`$ people outside of California move in and $`2/10`$ of people inside California move out.

captured by the **markov matrix**:

$`A=\begin{cmatrix}0.9 && 0.2 \\ 0.1 && 0.8 \end{cmatrix}`$

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
2. this gives $`S=\begin{cmatrix} 2 & 1 \\ 1 & -1 \end{cmatrix}`$ and $`S^{-1}=\begin{cmatrix} 1/3  & 1/3 \\ 1/3 & -2/3 \end{cmatrix}`$

**note** that the text book gives different $`S`$, still, the decomposision $`S \Lambda S^{-1}`$ gives the same result $`A`$. (it take me a while to verify)

substituting $`A=S \Lambda S^{-1}`$, $`u_k = S \Lambda^k S^{-1}`$ gives

$`(y_0 + z_0) \begin{cmatrix} 2/3 \\ 1/3 \end{cmatrix} + (y_0 - 2 z_0) (0.7)^k  \begin{cmatrix} 1/3 \\ -1/3 \end{cmatrix}`$ 

the second term diminishes, therefore, 

$`\begin{cmatrix} y_{\infty} \\ z_{\infty} \end{cmatrix} = (y_0 + z_0) \begin{cmatrix} 2/3 \\ 1/3 \end{cmatrix}`$ (**steady state**)



