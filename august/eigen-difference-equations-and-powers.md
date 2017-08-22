# goal

study $`u_{k+1}=A u_k`$

# compound interest

## discrete time, difference equation

suppose yearly interest rate 6%, then we have $`P_{k+1}=1.06 P_k`$. after 5 years, $`P_5 = 1338`$ if $`P_0=1000`$

next, suppose we deompose the the interest rate by certain date length (for example, month or day), 
then, for splitting:

- by month, $`P_{60} = 1349`$
- by day, $`P_{5 \cdot 365} = 1349.83`$

## continous time, differential equation

even further we make the time continous by considering $`\delta t`$
$`p_{k+1} = (1+0.06 \delta t)p_k \rightarrow \frac{p_{k+1} - p_k}{\delta t} = 0.06 p_k`$

in other words, we have $`\frac{dp}{dt} = 0.06 p`$

the solution is $`p(t) =e^{0.06t}p_0`$, then $`p(5) = 1349.87`$

# fibonacci numbers

captured by Fibanacci equation: $`F_{k+2} = F_{k+1} + F_{k}`$

in other words, denote $`u_k=(F_{k+1}, F_k)`$, then

$`u_{k+1} = \begin{bmatrix} 1 && 1 \\ 1 && 0\end{bmatrix} \begin{bmatrix} F_{k+1} \\ F_k \end{bmatrix}`$

## solving $`u_k = A^k u_0`$

in general, by eigen decomposition $`A=S^{-1}\Delta S`$, we get 

$`u_k = S^{-1} \Delta^{k} S u_0`$

denote $`c=S u_0`$ and columns in $`S^{-1}`$ as $`\begin{pmatrix} x_1, \ldots, x_n \end{pmatrix}`$, then 

$`u_k = c_1 \lambda_1^k x_1 + \ldots + c_n \lambda_n^k x_n`$


## how to compute the `k`th fibanacci number?

for fibonacci numbers, $`\lambda_1 = \frac{1+\sqrt{5}}{2}`$ and $`\lambda_2 = \frac{1-\sqrt{5}}{2}`$, eigenvectors are $`x=(\lambda, 1)`$

then, $`F_k=\frac{1}{\sqrt{5}} [\lambda_1^k - \lambda_2^k]`$

note that $`\frac{F_{k+1}}{F_k} \approx \lambda_1`$ for $`k \rightarrow \infnty`$ (because $`0<\lambda_2<1`$)

comment: $`\lambda_1`$ captures the rate of growth. 

## different cases for $`u_k = A^k u_0`$

if $`u_0`$ is an eigenvector $`x`$ of $`A`$, then $`u_k=\lambda^k x`$

if $`u_0`$ is a linear combination of eigenvectors of $`A`$, $`\sum_i c_i x_i`$, 
then $`u_k = \sum_i c_i \lambda^k x_i`$

to get vector `c`: `Sc=u_0`, then `c=S^{-1}u_0`

what if neither?