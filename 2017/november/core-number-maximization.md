# goal

add $`B`$ edges to maximize the following  objective

-  sum of core number of all nodes

# properties of objective

## monotinicity

non-decreasing monotonic: obvious

## non-submodular

an (n-1)-clique $`1, \ldots, n`$ and an n-clique $`n+1,\ldots ,2n+2`$

suppose:

- $`S_1=\{(1,n+1),(2,n+2), \ldots, (n-2, n+1)\}`$
- $`S_2 = S_1 \cup \{(n-1, n+1)\}`$
- $`e = (n, n+1)`$

we have the following:

- $`f(S_1+\{e\}) -f(S_1) = 0`$
- $`f(S_2+\{e\}) -f(S_2) = n-1`$: because all nodes in (n-1)-clique is now part of the n-clique

therefore $`f(S_1+\{e\}) - f(S_1) < f(S_2+\{e\}) - f(S_2)`$.

so it's non-submodular.

## non-supermodular

consider the above example but with edges:

- $`S_1=\{(1,n+1),(2,n+2), \ldots, (n-1, n+1)\}`$
- $`S_2= S_1 \cup \{(1, n+2)\}`$
- $`e=(n, n+1)`$

we have the following:

- $`f(S_1+\{e\}) - f(S_1) = n`$: all nodes in (n-1)-clique are now part of the n-clique
- $`f(S_2+\{e\}) - f(S_2) = 0`$: because nothing changes. 

therefore $`f(S_1+\{e\}) - f(S_1) > f(S_2+\{e\}) - f(S_2)`$.

so it's non-supmodular. 