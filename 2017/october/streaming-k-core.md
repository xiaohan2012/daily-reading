
# Streaming Algorithms for k-core Decomposition

- [paper](http://www.vldb.org/pvldb/vol6/p433-sariyuce.pdf)
- [a shorter summary](https://gitlab.com/xiaohan2012/daily-reading/blob/master/october/streaming-k-core.md#summary-from-order-based-paper-traversal-insertion-algorithm)

transform the problem of maintaining k-core decomposition to maining the k values of each node. 

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
   - or nodes whose core number is $`K(u)`$
   - and they are reachable via a path from u such that each node in the path has core number equal to $`K(u)`$
   - essentially $`H^u - H_{N(u)+1}`$

# algorithm: locating candidate

## subcore

subcore is essentially the nodes whose core number might change. 

Algorithm 2: find the subcore (k-shell) by traversal and update the K value accordingly. 

- essentially a variant of DFS that only visits edges whose endpoints have given a specific core number
- meanwhile, it returns current degree ($`cd`$), which is used to track its degree in its max-core. 

current degree `cd`: current degree of the node in its maximal core:

- it will be tracked (as intermediate result)
- if `cd(u)` is fewer than `K=core(u)+1`, then it should be excluded from core-`K`


## pure core

goal: locate a smaller set of candidates

$`MCD`$: maximum core degree of $`u`$: num of neighbors that have greater or equal $`K`$ values than $`K(u)`$ (same as `cd`?)

- $`MCD(u) \ge K(u)`$: $`MCD`$ is an upperbound on $`K(u)`$
- only when $`MCD(u)>K(u)`$, an adjacent edge addition could result in update
  - $`u`$ needs enough neighbors to have core number $`K(u)`$

def:

- pure core: subcore plus **the extra condition**, $`MCD(u)>K(u)`$

main theorem: only nodes in pure core may change their core number

`pcd`: pure core degree
## algorithm: updating core number

as both subcore and purecore gives *possible* nodes that change their core number, we need to determine them exactly. 

Algorithm 3 gives the edge insertion case. 

basic idea:

- order the nodes by their $`cd`$ value from low to high
- process each node $`u`$ sequentially, if $`cd(u) \le k`$, it cannot be in the new (k+1)-core, and we need to update its neighbors $`cd`$ value (chain effect)
- once $`cd(u)>k`$, it holds that the remaining nodes have $`cd()>k`$ (because of the ordering), thus they will all be in the new $`(k+1)`$-core (break the loop)

## TRAVERSAL algorithm

based on the concept of pure core degree ($`PCD(u)`$): number of neighbors $`w`$that are either:
  - $`K(u) = K(w)`$ and $`K(u) < MCD(w)`$
  - $`K(u) < K(w)`$

intuition for PCD: potential number of neighbors that are in the next max-core

we can use PCD as the new criteria for candidate node filtering. 

the algorithm computes the $`cd`$ on the fly. not sure how it works exactly. 


# edge deletion

very similar to chain effect. 

1. decrement the $`MCD`$ value, if the new value is smaller the $`K`$, its core number will change
2. as a result, its neighbors $`MCD`$ value might change also. do 1 and 2 recursively. 


# implication for public private network

consider the star structure of query node $`u`$, 

we can divide the neighbours into two sets:

- $`\{v \in N(u) \mid K(v) > K(u)\}`$: their $`K`$ values won't change 
- $`\{v \in N(u) \mid K(v) \le K(u) \}`$: their $`K`$ values might change. 

and we just traverse from each $`v`$ and collect the subcores. 


# resources

- [k-core decomposition in C++](http://www.geeksforgeeks.org/find-k-cores-graph/)
  - based on modified version of DFS
  - why time is $`O(V+E)`$?


# main idea of the traversal algorithm


- max-core degree, $`mcd(u)`$: number of neighbors of $`u`$ in $`core(u)-core`$ ($`core(w) \ge core(u)`$)
  - for a node $`u`$ to be n $`k`$-core, $`mcd(u) \ge k`$ should hold.
  - so if $`mcd(u) < core(u)+1`$ ($`core(u)+1`$ is the new possible core number), $`u`$ can be pruned
  - in other words, we need to maintain $`mcd(u)`$ for each $`u`$
- pure-core degree, $`pcd(u)`$, further pruning of the neighbors by max-core degree
  - intuition: for some nodes in neighbors  w.r.t $`mcd(u)`$, specifically $`\{w \mid core(w)=core(u) \}`$, they have no way to increment their core number, thus cannot affect $`u`$
  - exclude neighbors, $`\{w \mid core(w)=core(u), mcd(w) \le core(w)\}`$ (using the above result)
  - so, if $`pcd(u)<core(u)+1`$, they can be pruned. 
  
note that nodes in max-core degree is a superset of nodes in pure-core degree. 


## summary from "order-based" paper: traversal insertion algorithm

- edge $`(u, v)`$ is inserted
- suppose $`K=core(u)<core(v)`$

now we collect $`V^{'}`$, nodes that might need to change

1. we start from $`u`$, perform DFS 
1. we consider only nodes $`w`$ that:
   - $`core(w)=core(u)`$: by theorem 3.2
   - $`mcd(w) > K`$: if $`mcd(w) \le K`$, then it has no way to move to (K+1)-core. not edges is added incident to w. the only way it can move up is by promotion of its neighbors. 
1. additionally, we maintain $`cd(w)`$, maximial possible number of neighors of $`w`$ in $`(K+1)`$-core. 
   - initially $`cd(w)=pcd(w)`$
   - if $`cd(w) \le K`$, it's sure that $`w \not\in V^{*}`$
   - then we decrement the $`cd`$ values of its neighbors
   - this process goes on (called evition propagation)
   - (do we increment it i some cases?)
   - example 4.2 explains the process quite 
1. also, we update $`mcd`$ and $`pcd`$

to upperbound $`|V^{'}|`$, we introduce the idea of pure-core, $`pc`$ 

- set of nodes that have core number $`K`$
- connected
- and $`core(w)>K`$

it's shown that (by experiment):

- size of $`pc`$ has high variance and can sometimes be very large
- so the problem of vldb paper is the search space can be large (for some nodes). 
