http://www.cs.yale.edu/homes/spielman/561/lect03-15.pdf

$`\mu_1 \ge \mu_2 \ge \cdots \ge \mu_n`$ (opposite to the case of laplacian, $`L`$)

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

# graph coloring

- problem of graph coloring: color each node so that neighboring nodes does not have the same color
- a graph is $`k`$-colorable if it has $`k`$ coloring
- chromatic number of graph, $`\chi(G)`$, minimum $`k`$ s.t. the graph is $`k`$-colorable

trivial results:

- any graph is $`d_{max}`$-colorable
  - algorithm: color each vertex with different color to its neighbors
- generalization of the above algorithm:
  1. order the nodes in some way
  2. color each node in order s.t its color is different to its previous neighbors

## upperbound: Wif's bound

$`\chi(G) \le floor(\mu_1) + 1`$

main idea:

- using the generalized algorithm
- show any the max node degree of any subgraph is smaller than $`\mu_1`$ (using previous lemma)
- any such max degree upper bounds the $`\chi(G)`$

## lowerbound: Hoffman's bound

$`\chi(G) \ge 1 + \frac{\mu_1}{-\mu_n}`$

main idea (check the proof)

- working on block-form of matrix
- using the relationship on min/max eigenvalues of the matrix and its blocks. 

# questions

- how the largest eigen value of $`A`$ corresponds to the smallest eigen value of $`L`$ 
