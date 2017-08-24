# abstract

two problems:

1. generating a random sample from a markov chain respecting the stationary distribution
2. generating a random spanning tree respecting the distribution given by the weight

the paper's contribution:

- algorithms for both problems
- explains the duality between the two problems
- by using techniques either: 
  - coupling from the past
  - *loop-erased random walk* (implementing *cycle popping*)
  - one technique for one type of algorithm

# quick link

- section 2: review of coupling from the past
- section 3: CFTP algorithm for random state problem
- section 4: running time of CFTP
- section 5: CFTP for random tree
  - does not rely on the partial ordering
  - time most spent on finding root (however, for our problem, we can assume root is specified)
- section 6, 7: cycle popping-based algorithm for CFTP
  - another class of algorithm with running time bounded by *hitting time*


# notations

refer to: Table 2 (page 10)

- $`\mu`$: stationary distribution

- $`\tau`$: mean hitting time of markov chain, expected number of steps to travel from one state to another

- $`h`$: maximum hitting time

# rooted random spanning tree via coupling from the past

in short, given some rooted tree, perform multiple random walks until the root restored to the original one (coupled). 
  - the resulting spanning tree (of the same root) is the next state of the markov chain $`M_r`$.

one random walk step:

1. given some tree $`T`$ and root $`r`$
2. randomly pick the successor of $`r`$, say $`s`$, make it the new root
3. add edge $`(r, s)`$
4. delete outgoing edges $`(s, *)`$ 

questions:

- prove that $`M_r`$ is ergodic
- prove that $`M_r`$ preserves the desired distribution
- how is it related to coupling from the past

related to our problem:

- how to avoid constraint violation


# coupling from the past and random tree sampling

1. what's the random map here?
2. what's the composition? 
3. why returning to the root gives collapsing? 

- a tree can be represented by a vector $`T`$ (length $`N`$) where $`T[i]`$ represents the parent of node $`i`$
- a random map can be represented by a vector $`U`$ (length $`N`$) where $`U[i]`$ is the last successor of $`i`$ by random walk if $`i`$ is visited, otherwise it's $`nil`$
  - **question 1** done
- the new tree $`T'`$ (from $`U`$ and $`T`$) has $`T'[i] = U[i]`$ if $`U[i] != nil`$ and otherwise $`T'[i] = T[i]`$

composition of two random maps, $`U1`$ and $`U2`$:  $`U2`$ overrides the entries of $`U1`$ if the entry in $`U2`$ is not $`nil`$

- running time $`O(n)`$
- **question 2** done

**question 3**

seems to be inaccurate as the more precise condition is: if the **only** nil in entry $`U`$ is at the root. in other words:

- $`M`$ returns back to root
- all other nodes are visited during the excursion
- each visited node can be seen as a state at a different root
  - they all collapse to one tree with the same root


# learned

## markov chain

- markov chain: one type of markov process (discrete version), contains a set of random variables (indexed by time)
- a markov chain (with irreducible and aperiodic) defines a unique stationary distribution
- given a distribution we want to sample from, we can design a markov chain whose stationary distribution is the desired distribution

## random spanning tree

- whether determinant based or random walk based algorithm is faster depends on the graph structure
  - random walk based algorithm has running time related to cover time (as small as $`O(nlogn)`$)

- $`Broder[12]`$ approximate random arboescence generation from directed unweighted graph

- approximate version of exact sampling: sampling with bias $`\epsilon`$ w.r.t $`\mu`$
  - Aldous's procedure (approximate): running time -- $`O(\tau / \epsilon^2)`$

- hitting time in both graph random walk and markov chain
  - the mean time from one node/state to reach another
  - markov chain ~= random walk in graph
  - indicate they are essentailly the same problem?

# questions

-  passive vs active? examples?