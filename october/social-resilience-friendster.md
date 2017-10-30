# Social Resilience in Online Communities: The Autopsy of Friendster

# overview

goal: 

- define resilience measure for OSN
  - the measure is based on generalized k-core
- how it's related to the fall of an OSN

# related work

- on smaller scale subgraphs, e.g, communities
- anchored k problem

# k core 

k core decomposition can be viewed as a cascading effect. 

let's say nodes with fewer than 3 friends will leave, then:

during the process, the leave of low degree users might cause high degree users to be removed

this is essentially the k core decomposition process.

finally, an equilibrium graph will be reached

# generalized k core

it consists of:

- a property function $`B(H)`$ to quantify the "benefit" of staying in the network for each node
- a constant cost value $`c`$

a node will:

- stay if $`B^{i}(H)-c \ge 0`$
- leave if $`B^{i}(H)-c < 0`$

a subgraph $`H`$ is said to  be k-core if $`B_i(H) \ge k`$ for every $`i \in H`$

- $`k`$ is like the cost

# resilience

the author does the approximation $`B_i=b N_i`$, where $`b`$ is an integer. 

define $`c`$ to be the maximum value such that $`bN_i > c`$:

- the largest possible cost for at least one of the user to withstand
- like the maximum core value of the graph (in the original k-core definition)

then, define:

$`K=c/b+1`$

and resilience is the size of the $`K`$ core

- or size of the core with largest core value

# next

- how to compute the measure?
- how to find `b` and `c`?
- how it's related to collapse of Friendster?
- Kleinberg's paper