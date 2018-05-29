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
- eigen values: $`\lambda_1 \le \cdots, \le \lambda_n`$
- eigen vectors: $`\phi_1  \cdots \phi_n`$

# spectral theorem

in short, if $`n`$ by $`n`$ matrix $`M`$ is *symmetric* and real, there exists $`n`$ eigen vectors that are mutually orthogonal and unit and corresponding $`n`$ real eigen values.

if not symmetric:

- may be not $`n`$ eigen values.
- or non-orthnogonal eigen vectors

## Rayleigh quotient

defined as

$`\frac{x^T M x}{x^T x}`$

theorem: the value that maximizes the Rayleigh quotient is the eigen vector that corresponds to the largest eigen value, $`\lambda_n`$ of $`M`$

- the Rayleigh quotient $`\le \lambda_n`$
- for the minimization case, it corresponds to the smallest eigen value, $`\lambda_1`$

check the proofs

why divided by $`x^T x`$? 

1. any *rescaling* of the vector $`x`$ produces the same answer


# eigen value of laplacian

- number of zero eigen values = number of connected components
  - for connected graph, $`\lambda_1=0`$ 
- assume graph is connected, $`\lambda_2`$ is called *algebraic connectivity of a graph*
  - related to how well connected a graph is
  - bipartite graph has $$`\lambda_2 = 0`$

## visualization of line graph

[notebook](data/line-spectral.ipynb) to get some intuition

# main questions

- [X] how to interpret algebraic connectivity $`\lambda_2`$? 
  - refer to [2-laplacian.md](2-laplacian.md)
- why bipartite graph has $`\lambda_2=0`$, what does the eigen-vector look like?
