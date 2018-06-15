# Rings, Paths, and Cayley Graphs

## ring

- has the $`sin`$ and $`cos`$ form
- each eigen value has *two* eigen vectors (so there are $`n/2`$ unique eiven values)
- drawing first two eigen vectors form a xx-gon shape (Figure 5.1)
  - can intuitively verify that these eigen vectors correspond to th same eigen value

## path

closed related to ring, 

given a path $`P_n`$ with  $`n`$ nodes and consider a ring $`R_{2n}`$ of $`2n`$ nodes, 
then:

- eigenvalues of $`P_n`$ are the unique eigen values of $`R_{2n}`$
- each eigenvector of $`P_n`$ has values corresponds to the first $`n`$ values in the corresponding eigen vector of $`R_{2n}`$

## cayley graphs

cayley graphs, by def, has:

- nodes corresponds to elements in  *some group*
- edges specified by generators $`S`$, (subset of the group)
  - there is an edge $`(u, v)`$ if there exists $`s \in S`$ in the generator, $`u \circ s = v`$, where $`\circ`$ is some *group operator*
- $`S`$ must be closed under inverse: if $`s \in S`$, the $`s^{-1} \in S`$
  - inverse defined by the group

## special case 1: ring

ring is a special cayley graph, where

- group is all integers modulo $`n`$
- generators are $`\{-1, 1\}`$
  - inverse defined by negative
- group operators are $`+`$ (addition)

## specal case 2: hypercube

- group: $`\{0, 1\}^d`$
  - group operator $`+`$ as *addition modulo 2*
- generators: subset of $`\{0, 1\}^d`$ where there is only one $`1`$
  - corresponding to going in just one coordinate

visualize $`d=2`$ or $`d=3`$

# generalizing hypercubes

still consider hypercube, but now the generators has $`k`$ elements, $`g_1, \ldots, g_k`$. 

so the graph is $`k`$-regular.


## eigen values and eigen vectors of generalized hypercubes

each vector $`b \in \{0, 1\}^2`$ defines a eigenvector of the form:

\[k - \sum\limits_{i=1}^{k}(-1)^{b^T g_i}\]

note that $`(-1)^{b^T g_i} \in \{-1, 1\}`$

## random set of generators and approximation to complete graph

if $`\{g_i\}`$ are chosen uniformly randomly, then 

the expectation of $`\sum\limits_{i=1}^{k}(-1)^{b^T g_i}`$ will be 0

in other words, eigenvalues will tend towards $`k`$

using Chernoff bound (summation of independent random variables will not deviate far from the summation of their expectation)

we can further bound summation with high probability if we set $`k=cd`$, where $`d=\log n`$.

(in other words, now the graph is a $`\log-n`$-regular graph)

further, if we multiply the edge weight by $`n/k`$, then the eigen values is bounded near $`n`$.

in this way, we can use hypercube with $`cd`$ random genrators to approximate the complete graph.