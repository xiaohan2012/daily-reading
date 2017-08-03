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

- `\mu`: stationary distribution

- `\tau`: mean hitting time of markov chain, expected number of steps to travel from one state to another

- `h`: maximum hitting time

# rooted random spanning tree via coupling from the past

in short, given some rooted tree, perform multiple random walks until the root restored to the original one (coupled). 
  - the resulting spanning tree (of the same root) is the next state of the markov chain `M_r`.

one random walk step:

1. given some tree `T` and root `r`
2. randomly pick the successor of `r`, say `s`, make it the new root
3. add edge `(r, s)`
4. delete outgoing edges `(s, *)` 

questions:

- prove that `M_r` is ergodic
- prove that `M_r` preserves the desired distribution
- how is it related to coupling from the past

related to our problem:

- how to avoid constraint violation

# cycle popping

# coupling from the past

what is it?

- a method for sampling from stationary distribution of a markov chain
- it gives *perfect* sampling
  - in contrast, many MCMC algorithms, which give imperfect samples

"If we can figure out the state at time 0 by looking at the outcomes of a finite number of these tosses in the recent past, then the result is an unbiased sample"
- how can w
- composition of random maps?



# learned

## markov chain

- markov chain: one type of markov process (discrete version), contains a set of random variables (indexed by time)
- a markov chain (with irreducible and aperiodic) defines a unique stationary distribution
- given a distribution we want to sample from, we can design a markov chain whose stationary distribution is the desired distribution

## random spanning tree

- whether determinant based or random walk based algorithm is faster depends on the graph structure
  - random walk based algorithm has running time related to cover time (as small as `O(nlogn)`)

- `Broder[12]` approximate random arboescence generation from directed unweighted graph

- approximate version of exact sampling: sampling with bias `\epsilon` w.r.t `\mu`
  - Aldous's procedure (approximate): running time -- `O(\tau / \epsilon^2)`

- hitting time in both graph random walk and markov chain
  - the mean time from one node/state to reach another
  - markov chain ~= random walk in graph
  - indicate they are essentailly the same problem?

# questions

- sect 1.1: what is the two-dimensional array `M`?
  - the matrix where one dimention is time and the other is chain, entry value is the  state.
-  passive vs active? examples?