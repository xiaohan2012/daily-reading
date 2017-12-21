#  subcore algorithm

# why use subcore?

not suer why.

**a case where we don't conenct within subcore**


for example, a clique `{a, b, c, d}`, `(d, e)` and `(d, f)`

`e` and `f` are in two different subcores. but we can conenct `(e, f)` to make them a 2-core

# upperbound 

goal: define upperbound on the number of edges required to increase the subcore's core number by 1

define $`\deg^{*}`$ as degree received from higher order edges, $`\deg^{in}`$ as degree received from nodes in the same subcore

then the upperbound is:

$`\sum\limits_{u \in sc} K+1 - \deg^{in}(u) - \deg^{*}(u)`$

why not just `\deg^{total}(u) = \deg^{in}(u) + \deg^{*}(u)`?

illustration:

https://docs.google.com/drawings/d/1trPsXGlF_lzctMlFnHqt8Ic2EV_M_8yKhqujeuqlQR8/edit

# observation

consider the counter example for greedy:

for node `a-e`
- the `\deg^{*}` is: 0
- the `\deg^{in}` is: 2, 3, 3, 3, 3, 2

the above upperbound is 2. 

however, we need just one edge. 

how to detect that?

## a interesting problem

> given a subgraph `G^{'}` whose nodes have the same core number `K`, how to add minimum number of edges so that all nodes in `G^{'}` have core number increased by 1. 

some idea:

- for nodes, whose `\deg^{*}(u) + \deg^{in}(u) = K+1`, no need to add edges for it
- otherwise, for nodes with insufficient edges
  - if there exists some other node with insufficient edges, connect them
  - repeat the above process until it has sufficient edges (or we can just icnrease `\deg^{in}`)
  - otherwise, connect to higher core edges (or we can just icnrease `\deg^{*}`)


questions: is it optimal?

## algorithm

what should the algorithm be like? greedily select the best subcore? 