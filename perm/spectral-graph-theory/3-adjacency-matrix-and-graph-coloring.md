http://www.cs.yale.edu/homes/spielman/561/lect03-15.pdf

$`\mu_1 \ge \mu_2 \ge \cdots \ge \mu_n`$

for d-regular graph, $`\mu_1=d`$ and $`\phi_i = \text{constant}`$

# largest eigenvalue $`\mu_1`$

$`d_{ave} \le \mu_1 \le d_{max}`$

proof idea: 

- using rayleigh quotient

also, $`d_{ave}(S) \le \mu_1`$, where $`S`$ is any subgraph of $`G`$

for any $`S \subseteq G`$, $`\lambda_{max}(A) \ge \lambda_{max}(A(S)) \ge \lambda_{min}(A(S)) \ge \lambda_{min}(A)`$

proof idea:

- thinking $`y \in R^{n-1}`$, where $`R^{n-1}`$ is a subspace of $`R^n`$
- use rayleigh quotient

if $`\mu_1 = d_{max}`$, then $`G`$ is $`d_{max}`$-regular

# eigenvector

Perron-Frobenius theorem (one result)

- $`\phi_1`$ is strictly positive

for bipartite graph, $`\mu_1 = - \mu_n`$

- $`+`$ for one side, $`-`$ for the other side

for laplacian, $`\phi_n`$ corresponds to the largest eigen value, it assigns as different "colors" to neighboring vertices. 


