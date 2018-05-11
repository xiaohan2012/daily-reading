# spectral graph theory: introduction

http://www.cs.yale.edu/homes/spielman/561/lect01-15.pdf

# notation:

- $`A`$: adj matrix
- $`D`$: degree matrix (diag)
- $`W = D^{-1} A`$: normalized weight matrix, each row sum up to 1
  - $`A D^{-1}`$ has each column sum up to 1, tranpose of $`W`$
- $`p`$: the probabiltiy vector (a row)
- $`p W`$: one transition of the system
  - $`W`$ can be viewed as operator
- eigen values: $`\lambda_1 \le \dots, \le \lambda_n`$
- eigen vectors: $`\phi_1  \dotse \phi_n`$

# spectral theorem

in short, if $`n`$ by $`n`$ matrix $`M`$ is *symmetric* and real, there exists $`n`$ eigen vectors that are mutually orthogonal and unit and corresponding $`n`$ real eigen values.

if not symmetric:

- may be not $`n`$ eigen values.
- or non-orthnogonal eigen vectors

## Rayleigh quotient

theorem: the value that maximizes the Rayleigh quotient is the eigen vector that corresponds to the largest eigen value, $`\lambda_n`$

- the Rayleigh quotient $`\le \lambda_n`$
- for the minimization case, it corresponds to the smallest eigen value, $`\lambda_1`$

check the proofs

what's the relationship between the $`x^T L x`$ and $`\frac{x^T L x}{x^T x}`$?

- if $`x`$ is unit, then they are the same

# eigen value of laplacian

- number of zero eigen values = number of connected components
  - for connected graph, $`\lambda_1=0`$ 
- assume graph is connected, $`\lambda_2`$ is called *algebraic connectivity of a graph*
  - the larger, the more connected
  - bipartite graph has $`\lamdba_2 = 0`$

## visualization of line graph

[notebook](data/line-spectral.ipynb) to get some intuition