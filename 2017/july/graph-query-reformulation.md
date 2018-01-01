# graph query reformulation

[paper](http://disi.unitn.it/~mottin/publications/kdd15-gqref.pdf)


- what's query like?
- subgraph isomorphism problem


# contributions

- top-k query reformulations to tackle "information overload" problem in graph database search
  - similar tasks have been done in text retrieval system
  - can be used for anormaly detection
- problem: finding a set of reformulations for a given graph search query
- NP-hardness and 1/2-approximation algorithm
- speed-up

# formulation

goal: coverage by all speicializations and differentiation among  speicializations

- labeled graph (both node and edge)
- isomorphism obeys labels as well. 


definitions:

- a query corresponds to a resutl set.
- coverage of specialization set: |union of all result sets|
- diversity between two queries: number of uncommon results
- objective `f`: `coverage + \lambda \times sum of pairwise diversity`

problem:

- maximize `f` s.t. `|specification set| = k`
- NP-hard (because it's a special case of maximum coverage)


# algorithm

## naive approach

take the top-k frequent subgraph. however, does not capture diversity.

## greedy

for each iteration, choose the subgraph that maximizes the marginal potential gain

important theorem: maximizing function `g=w(U)+lambda \sum_u\sum_v d(u,v)` under cardinality constraint, greedy gives 1/2 approx if:

- `w` is monotone submodular 
- `d` is a metric. 

# speeding up

challenges:

- bottle neck on the `argmax` step at each iteration
- required to enumerate all possible subgraphs wich is `#P`-complete (search space too big)

## computing marginal potential gain `\delta`

- computing `\delta_{cov}` is trivial (linear)
- computing `\delta_{div}` is quadratic w.r.t its form, however, it can be reduced to linear

basic idea of computing `\delta_{div}`: 

- keep track of covered graphs of a query as a vector. 
- use one accumulator vector to keep track of current specializations
- set intersection done via vector multiplication


## faster pruning

basic idea of upperbound:

- given a specialization `R'` and set of selected specialization `S`, certain results by `R'` are covered by the *majority* of `S` and these results actually decreases the final score `f` because of diversity part
- if we remove such "overly" covered results from the result set of `R`, `f` will increase, which serves as an upperbound

important theorem (3):

1. upperbound derivation
2. for any specialization `R''` of `R'`, margin gain of `R''` <= upperbound of `R'`
   - why? 
     1. `cov(R'') <= cov(R')`
     2. `x_{Q''}` cannot be as good as `x_{Q*}` because `R(Q'')` is a subset of `R(Q')`
   - however, marginal gain of `R''` is not necessarily <= marginal gain of `R'`
     - example: `R''` covers the same *uncovered* set as `R'` but does not introduce any redundancy, then `R''` is better than `R'`

though computing upperbound has same time complexity (linear) as computing marginal gain, it's useful because it can be used to prune descendants of the search space. 

## fast\_MMPG  algorithm

- this algorithm tackles the `argmax` part of the main algorithm
- specialization hierarchy is represented as a tree, a child (`Q''`) only adds on edge to its parent(`Q'`). 

safe pruning: 

given the current best marginal gain `f*` explored so far, if `upperbound(R') < f*`, then `R'` and its descendants can be pruned safely. 

     
# further reading

- graph isomorphism (efficient way to do it?)
- graph search problem

# questions

- how to use of monotone submodular and pseudometric to prove approximation factor, how?


# learned

general knowledge:


- [graph isomorphism problem(https://en.wikipedia.org/wiki/Graph_isomorphism_problem): not known to be polynomially solvable nor NP-complete
  - problem: given `G` and `G'`, finding a bijection `f` of `V(G)` and `V(G')` such that for each edge `(i, j)` in `G`, `(f(i), f(j))` is in `G'`.
- [subgraph isomorphism problem](https://en.wikipedia.org/wiki/Subgraph_isomorphism_problem): NP-complete
  - graph query problem is hard because it seems to rely on this problem (can we formulate it differently so that it avoid this reliance?)
- **frequent subgraph mining problem**: given a set of graphs and some threshold `alpha`, find all subgraphs s.t. each subgraph is contained in at least `alpha` fraction of the global set
- [pseudo metric](https://en.wikipedia.org/wiki/Pseudometric_space)
  - identity of indiscernibles does not hold
  - e.g, `d(x, y)=0` does not imply `x=y`


technical part:

- a interesting formulation (objective function is maximize coverage + some pairwise measure)
  - similar problems might use such formulation, e.g, selecting the top-k news (coverage + diversity)
- for the above problem, two requirements for function `g` to have 1/2-factor greedy algorithm
- using upperbound to prune the search space (represented as a tree)
- set cover calculating using vector representation
  - set intersection done via vector dot product