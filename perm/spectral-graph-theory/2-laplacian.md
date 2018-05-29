http://www.cs.yale.edu/homes/spielman/561/lect02-15.pdf

# laplacian
another way to look at lapalacian: 

sum over (u, v) of $`(\delta_u - \delta_v) (\delta_u - \delta_v)^T`$, where $`\delta_u`$ is indicatetor vector at $`u`$

$`x L_G x^T = \sum\limits_{(u, v) \in E} w_{u, v} (x(u) - x(v))^2`$

# relation to graph drawing

1. consider line graph and assign a real-value to each vertex (position on a line)
2. intuitively, nodes with edges should be close to each other and this maps to minimizing the above formula
3. we constrain the vector to be:
   - non-zero/unit-length
   - orthgononal to $`[1, 1, 1,..., 1]`$
4 for 2D case, we consider two vectors $`x`$ and $`y`$
  - we furhter constrain that $`x`$ is orthogonal to $`y`$

we find that $`x`$ and $`y`$ corresponds to $`\phi_2`$ and $`\phi_3`$ (2nd and 3rd eigenvector)

# isoperimetry and $`\lambda_2`$

*isoperimetry ratio* of a vertex set $`S`$: $`\theta(S) = cut(S)  / |S|`$

isoperimetry number of $`G`$, minimum  isoperimetry ratio of some vertex set in $`G`$

Cheeger's Inequality:

$`\theta(S) \ge \lambda_2 / (1-s)`$ where $`s = |S| / |V|`$

- $`\lambda_2`$ lower bound on isoperimetry number
- the larger the $`\lambda_2`$, the harder to cut, the more connected the graph

# example graphs and eigen values

## complete graph

$`\lambda_1=1, \lambda_2 = \cdots \lambda_n = n`$

note that $`\lambda_2=n`$, relate this to Cheeger's Inequality, this means complete graph is well-connected (hard-to-cut)

## star graph

$`\lambda_1=1, \lambda_2 = \cdots \lambda_{n-1} = 1, \lambda_n=n`$

uses the fact that $`\text{Tr}(M) = \sum\limits_{i=1, \ldots, n} \lambda_i`$ 