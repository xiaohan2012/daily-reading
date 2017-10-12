- k-order: one instance of all possible vertex sequence produced by a core decomposition algorithm


- k-core: no connectivity requried (so unique)
- k-subcore: nodes with core number equal to k and connected
  - $`sc(u)`$: subcore containing $`u`$, $`k`$ is implicit here, $`k=core(u)`$

- $`V^{*}`$: nodes whose core number need to be updated

# previous theorems

suppose one edge $`(u, v)`$ is inserted.

**theorem 1**: core number of each vertex can increase by at most 1. 

**theorem 2**: if $`core(u) < core(v)`$, $`core(v)`$ won't change

*proof*: if $`core(v)=K`$ increases to $`K+1`$, then edge $`(u, v)`$ must be included in the $`K+1`$, therefore $`u`$ is in the $`K+1`$ core, which is impossible becasue its core number can increase at most by 1 (using theorem 3.1). 

**theorem 3**

- if $`core(u) < core(v)`$, then $`V^{*} \subseteq sc(u)`$ 
  - proof partly using theorem 2
- if $`core(u) = core(v)`$, then $`V^{*} \subseteq sc(u) \cup sc(v)`$


# ordered-based algorithm

## main idea

we can narrow down $`V^{*}`$ only to nodes **after** $`u`$ and in the same core $`O_k`$, $`sc(u)`$. 
(using the paragraph **Edge Insertion**)

- in other words, $`V^{*} \subseteq sc(u) \cap \{v \mid u \le v \}`$

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

intuition: if $`u`$ will be moved to $`K+1`$, then some of its neighbors (after it) $`deg^{+}`$ needs to be updated because now $`u`$ is after them! 

that's why we need to collect other candidates as well. 

## scanning process: building $`V_C`$

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

## what makes a difference? the order

because of the ordering, we can exclude nodes before $`u`$ from $`V^{*}`$. 

this is shown in example 5.2. 

## $`V_C = V^{*}`$

not sure why. 

## maintaining k-order

we need to ensure *Lemma 5.1* is satisfied. 

for each visited $`w \not\in V_C`$, we leave them there (the paper say it "append to $`O_k^{'}`$")
  - ok, here I used to misunderstand. the order in $`O_{k}^{'}`$ might change (because of the appending operation)

for each visited $`w \in V_C`$, we *prepend* them to $`O_{k+1}^{'}`$ ($`K+1`$ core)

# implementation

for each $`O_k`$, we maintein a order statistic tree, $`A_k`$, that supports:

- query node rank in $`O(\log|O_k|)`$ time to evaluate if $`u \le v`$
- insertion/deletion in $`O(\log|O_k|)`$ time

also we use $`B`$ to keep track of nodes that are either $`deg^{*}(u) + deg^{+}(u) > K`$ or $`deg^{*}(u) + deg^{+}(u) \le K , deg^{*}(u) \neq 0`$. 
  - nodes that enter first or third loop in Algorithm 2
  - $`V^{+}`$ in other words

$`B`$ is a min-heap, which stores $`(rank(u), u)`$ pairs nodes in $`V^{+}`$

# running time

$`O(\sum_{v \in V^{+}} deg(v) \log \max\{|O_k|, |O_{k+1}|\})`$

the $`\log`$ part mainly comes from order evaluation

# compared to the traversal algorithm

traversal does not use the order information from core decomposition, which this algorithm does. 

# questions

- what if for edge $`(u, v)`$, $`u, v \in O_k`$? --- does not matter, we only consider order. $`v`$ might be changed to $`K+1`$


# batch setting

suppose $`u`$ is the query node and $`core(u)=K`$

we divide the edges $`(u, v)`$ into 3 categories:

1. $`E_{<} = \{(u, v) \mid core(v) < K \}`$
2. $`E_{=} = \{(u, v) \mid core(v) = K \}`$
3. $`E_{>} = \{(u, v) \mid core(v) > K \}`$

inserted edges in the $`i`$the core: $`E_{<}^{(i)}`$
endpoints in the $`i`$the core: $`O_{<}^{(i)}`$

## $`E_{<}`$

observation 1: $`\delta core(vu) = 0`$

observation 2: $`\delta core(v) \le 1`$

consider each $`O_i`$ group separately where $`i<K`$

**updating $`V_C`$** 

we consider each $`O_i`$ separately, 

first, increment each $`deg^{+}(v)`$, for $`(u, v) \in E_{<}^{(i)}`$ and 

if $`deg^{+}(v) > K`$, then include $`v`$ into $`V_C`$

and we update $`V_C`$ by scanning $`O_i`$ from the earliest node in $`O_{<}^{(i)}`$. 

**maintaining order**

again we consider for each $`O_i`$, similar to the paper:

1. prepend $`V_C`$ to $`O_{i+1}^{'}`$ while repecting their orignal order in $`O_i`$
2. append the rest of the scanned nodes in $`O_i^{'}`$


## $`E_{=}`$

observation 3: $`\delta core(u) \le 1`$

*proof*: consider edge insertion separately,
once $`core(u)`$ becomes $`K+1`$, it won't change because of now $`core(v)<core(u)`$for all $`v \in V_{=}`$. then from theorem 3.2.

observation 4: $`\delta core(v) \le 1`$ for all $`v \in V_{=}`$

the argument the same as the case for $`E_{<}`$.

combining the above two cases, we know for all $`v^{'} \in \{u\} \cup O_{=} \cup O_{<}`$, $`\delta core(v^{'}) \le 1`$

## $`E_{>}`$


