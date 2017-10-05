- what are the properties of k-core? observation 1 to 3
- 
  

[k-core decomposition in C++](http://www.geeksforgeeks.org/find-k-cores-graph/)
  - based on modified version of DFS
  - why time is $`O(V+E)`$



# bg

def:

- seed-k-core: connected, minimum degree is k
- k-core: connected, maximal
- k value of node $`i`$: $`K(u)`$, maximal  k value of $`H_k^u`$

## obs

1. k-core containing a given node $`u`$ is unique (if two k-cores, violates maximal condition)

2. exists one and only one $`(k-1)`$-core (if two k-1 cores, maximal condition is violated), denoted as $`H_k^u`$
   - note that it's a bigger core

3. node with $`K(u)=k`$ takes part in k cores, $`H_k^u \subseteq H_{k-1}^u \subseteq \ldots H_1^u`$

## corollary

given $`K`$ values for all nodes, to find $`H_k^u`$ for some $`u`$, just traverse the graph starting from $`u`$ to collect nodes $`v`$ with $`K(v) \ge k`$. 

implication:

1. it answers how to find the k-core that contains a *query node*. 
2. the problem of mainintaing k-core decompostion is equal to maintaining the $`K`$ values

# theories

consider one edge insertion or removal, $`(u, v)`$

main result:

1. theorem 1: k values can be changed at most by 1 (absoluate value)
2. theorem 2: if $`K(u)<K(v)`$, $`K(v)`$ won't change. 
3. theorem 3: connectivity
4. theorem 4: assume $`K(u) \le K(v)`$, nodes whose k values *may* be affected are the $`K(u)`$ *shell* reachable from $`u`$. 
   - essentially $`H^u - H_{N(u)+1}`$

# algorithm

## subcore

find the shell (called subcore) by traversal and update the K value accordingly. 

## pure core

goal: locate a smaller set of candidates

maximum core degree ($`MCD`$) of $`u`$: num of neighbors that have greater or equal $`K`$ values than $`K(u)`$

- $`MCD(u) \ge K(u)`$: $`MCD`$ is an upperbound on $`K(u)`$
- only when $`MCD(u)>K(u)`$, an adjacent edge addition could result in update
  - $`u`$ needs enough neighbors to have core number $`K(u)`$

def:

- purecore: subcore plus the extra condition, $`MCD(u)>K(u)`$

# implication for public private network

consider the star structure of query node $`u`$, 

we can divide the neighbours into two sets:

- $`\{v \in N(u) \mid K(v) > K(u)\}`$: their $`K`$ values won't change 
- $`\{v \in N(u) \mid K(v) \le K(u) \}`$: their $`K`$ values might change. 

and we just traverse from each $`v`$ and collect the subcores. 

