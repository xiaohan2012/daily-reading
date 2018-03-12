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
