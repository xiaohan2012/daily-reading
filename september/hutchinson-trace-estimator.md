# Hutchinson's trace estimator

goal: estimate $`\text{tr}(A)`$, trace of matrix when $`A`$'s form is not explicit. 

motivation: if $`A`$ has some "complex" form, for example $`A=B^k`$, then evaluating $`\text{tr}(B^k)`$ by first computing $`B^k`$ then evaluating the trace is $`O(kn^3)`$. 

hutchinson's method is a cheaper way to do 

# main result $`\text{tr}(A)=\text{E}[z^T A z]`$


we now prove it

$`A \in \mathbb{R}^{n \times n}`$, $`z`$ is a random vector of length $`n`$ with mean 0 and variance 1. 

##  $`\text{E}[z z^T]`$

$`z`$ is a column vector, $`\text{E}[z z^T]_{ij} = \text{E}[z_i z_j] = \Sigma_{ij} + \mu(z_i) \mu(z_j)`$ ($`\Sigma`$ is the covariance matrix for varible $`z`$, the left is by def of covariance)

so:

$`\text{E}[z z^T] = \Sigma + \mu \mu^T`$

in other words, if $`\mu(z)=0`$ and $`\Sigma(z)=I`$, then 

$`\text{E}[z z^T] = I`$

such a $`z`$ can be Rademacher distribution, with each entry equal to -1 or 1 with equal proba. or $`z`$ can be gaussian distribution. 

## to continue

using cyclic property of trace

- $`\text{tr}(A)=\text{tr}(AI)=\text{tr}(A\text{E}[z z^T])`$
- $`=\text{E}[\text{tr}(Az z^T)]`$
- $`=\text{E}[\text{tr}(z^TAz)]`$
- $`=\text{E}[z^TAz]`$

so we have transformed a linear algebra problem (trace computation) to a statistical problem


# resource

http://blog.shakirm.com/2015/09/machine-learning-trick-of-the-day-3-hutchinsons-trick/

# $`\text{E}[x^T A x]`$

given column vector $`x`$ of length $`n`$ and $`n \times n`$ matrix $`A`$, what $`\text{E}[x^T A x]`$ (it's a real number)? 

$`x^T A x=\sum_i x_i \sum_j A_{ij} x_j = \sum_{ij} A_{ij} x_i x_j`$

- $`\text{E}[x^T A x]=\text{E} [\sum_{ij} A_{ij} x_i x_j]`$
- $`= \sum_{ij} A_{ij} \text{E}[x_i x_j]`$ (linearity of expectation)
- $`=\sum_{ij} A_{ij}(\text{E}[x_i] \text{E}[x_j] + cov(x_i, x_j))`$ (by definition of covariance, $`cov(i, j)=\text{E}[x_i x_j] - \text{E} [x_i] \text{E} [x_j]`$)
- $`=\sum_{ij} A_{ij}\mu_i \mu_j + A_{ij} \sigma_{ij})`$ (notation convenience)
- $`=\mu^T A \mu + \sum_i \sum_j A_{ij} \sigma_{ji}`$
- $`=\mu^T A \mu + \sum_i (A\Sigma)_{ii}`$
- $`=\mu^T A \mu + \text{tr} (A\Sigma)`$

# trace properties


$`\text{tr}(AB) = \text{tr}(BA)`$

cyclic property

$`\text{tr}(ABCD)=\text{tr}(BCDA)=\text{tr}(CDAB)=\text{tr}(DABC)`$


$`\det(\exp(A))=\exp(\text{tr}(A))`$ (for gaussian models?)