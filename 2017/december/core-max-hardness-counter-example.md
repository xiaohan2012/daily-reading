# one counter example for hardness proof of core maximization

a very large set of $`n+1`$ elements (so $`c_{max}=n`$) and $`(x, y_1)`$, $`(x, y_2)`$ $`(x, y_3)`$, $`(x, y_4)`$, ..., $`(x, y_n)`$ and $`(y_1, z_1)`$, $`(y_2, z_2)`$, $`(y_3, z_3)`$, ... $`(y_n, z_n)`$

by our graph construction:

- also $`x`$ receives $`n-1`$ compensating edges (because of the $`n+1`$-element set)

suppose the set $`(y_1, z_1)`$, $`(y_2, z_2)`$, .. are selected. then:

- $`x`$ has $`n`$ higher order edges (one end of the edge is of a higher core), received from covered set

together, $`x`$ has $`2n-1`$ edges which the other end is in a higher core. 

therefore, even though $`x`$ is not selected, its core number increases, which shouldn't happen.