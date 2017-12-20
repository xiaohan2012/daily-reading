#  subcore algorithm

## upperbound 

goal: define upperbound on the number of edges required to increase the subcore's core number by 1

define $`\deg^{*}`$ as degree received from higher order edges, $`\deg^{in}`$ as degree received from nodes in the same subcore

then the upperbound is:

$`\sum\limits_{u \in sc} K+1 - \deg^{in}(u) - \deg^{*}(u)`$

## algorithm

what should the algorithm be like? greedily select the best subcore? 