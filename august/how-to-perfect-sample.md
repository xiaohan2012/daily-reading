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

- cover time: expected time of a random walk starting  starting at vertex $`x`$ in the graph $`G`$ to reach each vertex at least once:
  - the markov process can be modeled as a graph with stochastic adj matrix

# CFTP

3 ingredients:

1. a procedure for **randomly generating maps**: $`f: X \rightarrow X`$ (state space)
   - $`f = RandomMap()`$: $`RandomMap`$ instantiates random mapping
2. a method of **composing** random maps: composing means $`F_{-t}^0(x) = f_0(f_{-1}(\ldots f_{-t}(x))`$
3. a test to determine if a composition of random maps is **collapsing**: for exponentially large state space $`X`$, it's inefficient to enumerate them all. efficient techniques such as "sandwiching" is an example. 

two requirements for $`f`$:

1. $`f`$ must preserve the target distribution

2. the composition of random maps $`f_0 \circ f_{-1} \circ \ldots \circ f_{-t}`$ has non-zero proba of being constant-valued function
  - constant-valued function: outputs a **single** value for **all** inputs
  - just to make sure the chains can collapse

## backward coupling vs forward coupling

1. $`f_0 \circ f_{-1} \circ \ldots \circ f_{-t}`$ is a constant function with proba 1 given $`t \rightarrow \infty`$
2. $`f_t \circ f_{t-1} \circ \ldots \circ f_{0}`$ is a constant function with proba 0 given $`t \rightarrow \infty`$
   - is it $`n`$ *independent* chains?
   - "copies" of the chain?
   - "unique elements" would change?

in orther words, BC is [well-defined](https://en.wikipedia.org/wiki/Well-defined) while FC is not. 

# COVER-TIME algorithm

a method for $`RandomMAP`$

main results:

1. running time bounded by cover time, $`T_c`$
2. $`f(X)`$ satisfies $`\pi`$ if $`X`$ is distributed according to $`\pi`$
3. proba that RandomMap( ) is a constant map is at least 3/8.
   - bounds the running time for coelascing 
4. Theorem 4


# rooted random spanning tree via coupling from the past

- $`\xi`$: set of spanning trees on $`G`$
- $`\Upsilon`$: probability measure on $`\xi`$, where $`\Upsilon(T)=\prod_e w(e)`$
  - $`\Upsilon_r`$: on spanning trees at root $`r`$
- $`M`$: the backward chain described in Broder's paper
  - $`M`$ maintains $`\Upsilon`$ and for rooted version as well (lemma 10). 
- $`M_r`$: a chain where each state is a $`r`$-rooted ST
  - in other words, transition between states requires multiple steps of random walk
  - $`M_r`$ preserves $`\Upsilon_r`$




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
  - a tree can be represented by a vector $`T`$ (length $`N`$) where $`T[i]`$ represents the parent of node $`i`$
  - a random map that sends $`T`$ to $`T^{'}`$ by a vector $`U`$ (length $`N`$) where $`U[i]`$ is the last successor of $`i`$ by random walk if $`i`$ is visited, otherwise it's $`nil`$
  - $`U`$ is not the random map, but one element ($`x \rightarrow y`$) in the mapping

2. what's the composition? 

  - the new tree $`T^{'}`$ (from $`U`$ and $`T`$) has $`T^{'}[i] = U[i]`$ if $`U[i] \neq nil`$ or $`i`$ is root, otherwise $`T^{'}[i] = T[i]`$
  - composition of two random maps, $`U1`$ and $`U2`$:  $`U2`$ overrides the entries of $`U1`$ if the entry in $`U2`$ is not $`nil`$
  - running time $`O(n)`$

3. why returning to the root gives collapsing? 

seems to be inaccurate as the more precise condition is: if the **only** nil entry in $`U`$ is at the root. in other words:

- $`M`$ returns back to root
- all other nodes are visited during the excursion
- each visited node can be seen as a state at a different root
  - they all collapse to one tree with the same root

but they do not necessarily collaspe to the same **state** (root is not the state)


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
   - passive setting: the markov chain is already given, $`NextState`$ just gives the next state based on the given chain
   - active setting: the markov chain is not known, $`RandomSuccessor`$ sets the next state and returns it. 

- $`voter-CFTP`$ $`monotone-CFTP`$ vs $`coalescing-CFTP`$, what are they?
  - voter-CFTP: the graph figure (fig 2) described in sec 1.1 and analyzed in sec 4
  - coalescing-CFTP: in sec 4
