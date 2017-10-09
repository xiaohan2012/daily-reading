- k-order: one instance of all possible vertex sequence produced by a core decomposition algorithm


- k-core: no connectivity requried (so unique)
- k-subcore: nodes with core number equal to k and connected
  - $`sc(u)`$: subcore containing $`u`$, $`k`$ is implicit here, $`k=core(u)`$

- $`V^{*}`$: nodes whose core number need to be updated

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


## traversal insertion algorithm

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


# ordered-based algorithm

## main idea

we can narrow down $`V^{*}`$ only to nodes after $`u`$ and in the same core $`O_k`$. 
(using the paragraph **Edge Insertion**)

then we scan from $`u`$ to the end of $`O_k`$ and build $`V^{*}`$. 

last, we update $`O_k`$ and $`O_{k+1}`$.

## concepts

**order**: the node removal order induced by the core decomposition algorithm

**k-core**: one instantiation of such order

**remaining degree** $`deg^{+}(u)`$: number of neighbors of $`u`$ that ordered after $`u`$:

- interpretation: like the effective degree of $`u`$, because nodes before $`u`$ are removed and they do not contribute to increasing $`core(u)`$

**Lemma 5.1**: a ordering is a k-order if and only if $`deg^{+}(u) \le core(u)`$ for every $`u`$.

property of $`deg^{+}(u)`$: $`deg^{+}(u) \le core(u)`$

and if $`deg^{+}(u) > core(u)`$ after some edge insertion, $`core(u)`$ needs to increment. 


**candidate degree** $`deg^{*}(u)`$: number of neighbors of $`u`$ that are:

1. in the same core, $`O_k`$
2. before $`u`$
3. is a candidate node in $`V_C`$


## scanning process

denote $`V_C`$ as the set of candidate nodes.

1. if $`deg^{+}(u)>K`$, then $`u \in V_C`$
2. othersiwe, nothing is changed

so we discuss the first case.

for each scanned node $`w`$

note that $`deg^{*}(w) + deg^{+}(w)`$ is the *upper bound* of neighbors of in the new $`K+1`$ core. 

1. if $`deg^{*}(w) + deg^{+}(w) > K`$, then $`w \in V_C`$.
2. otherwise, $`deg^{*}(w) + deg^{+}(w) \le K`$, $`w \not\in V_C`$
   - insufficient neighbors

there are some details here:

if $`w`$ is not in $`V_C`$, then for $`\{w^{'} \mid w^{'} \in nbr(w) \}`$, $`deg^{+}(w^{'})`$ needs to be *decremented*. 

See Fig 8 for example. 

## $`V_C = V^{*}`$

not sure why. 

## maintaining k-order

we need to ensure *Lemma 5.1* is satisfied. 

for each visited $`w \not\in V_C`$, we leave them there (the paper say it "append to $`O_k^{'}`$")

for each visited $`w \in V_C`$, we *prepend* them to $`O_{k+1}^{'}`$ ($`K+1`$ core)



