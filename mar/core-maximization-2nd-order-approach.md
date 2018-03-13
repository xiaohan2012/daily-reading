# core maximization using 2nd order approach

basic idea:

instead of evaluating on each edge separately, 
we evaluate on two edges at a time. 
naively, there are quadratic possibilites. 
we can use the forward propagation process to reduce the number of pairing possibilities. 

finally, given $`(e, e^{'})`$ and $`f(e, e^{'})`$, the set of promoted nodes, we can build a quadratic progrom. 

main questions:

1. how to build $`f(e, e^{'})`$
2. how to solve the quadratic program? is greedy good?
3. can we consider higher order relations such as adding 3, 4 even 5 edges?


# March 13th

## 2nd order approach

- 2nd-order approach: consider a pair of edge if their $`V_c`$ intersects (synergy effect)
  - can end up with an edge graph where two edge nodes are connected if they intersect on $`V_c`$
  - might go to higher order
- can be approximated using greedy or quadratic programming

however, the pairing method does not work for the karate club example as their $`V_c`$ do not intersect. 
Might need to improve the pairing method. 

## finding (important node and promotion number) pair

also thought about finding the important pair of $`(n, \Delta c)`$ and compute the set of promoted nodes because of the promotion of $`n`$ by $`\Delta c`$.

this is related to:

- k-anchored problem as in their case $`\Delta c=\infty`$
- collapsible core problem as in their case, nodes are "demoted" instead of promoted

however, issues are below:

- how to promote a node $`n`$ by $`\Delta c`$ is not very clear.
- does not take into account of the effects of promoting multiple nodes


