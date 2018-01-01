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

the author does the benefit approximation $`B_i=b N_i`$, where $`b`$ is an integer to generalize the original coreness definition.

define $`c`$ as the cost of staying. 

if $`B_i > c`$, then user stays. otherwise, it leaves. 

the coreness of a participating user should be at least $`K=(c/b)+1`$

# degree distributions

non-power-law distribution. 

- power-law distribution do not have epidemic threshold. contagion will infect most of the nodes. 

test power law hypothesis instead of goodness of fit.

- Facebook, Friendster, Orkut and Livejournal rejects the power-law hypothesis
- Myspace passes the test (however might be wrong because the data crawling can create bias)

# coreness distribution

friendster has more nodes of large core number than livejournal. 

It other words, nodes in friendster have larger core number on average. 

plus, livejournal's coreness distribution is more skew. 

paper states that livejournal needs to have much lower $`c/b`$ to maintain the network. 

  - interpretation: livejornal is a blog community, where users create large amounts of original content. per social link benefit is ligh. 
  - but is this the cause?

# resilience comparison

Figure 4: x-axis is the $`c`$ value expressed by $`k_s`$, y-axis is the fraction of nodes remaining. 

as cost $`c`$ increases, fewer nodes remain. 

note that result for fb, myspace, orkut can be biased because of the biased crawling method. 

the upper the line, the more resilient. 

then coreness along does not explain the collapse of myspace and friendster. 

other factors should be considered as well, such as service features, etc

# explaining the collapse of friendster

given number of active users over time, the author wants to model this process using core number and CCDF. 

he "fits" the data and assumes the rate of increase of $`K`$ (the cost to stay)

the actual number of active users is not available, and he uses google search volume as a proxy. 

the fitting explains the remaining trend quite well. 

# next

- how to compute the measure?: CCDF of node coreness
- how to find $`b`$ and $`c`$?: not addressed in the paper. the ratio $`c/b`$ is varied to plot CCDF. 
- how it's related to collapse of Friendster?
- Kleinberg's paper

# learned

- one resilience measure based on coreness distribution and cost/benefit ratio
  - however, it solely cannot explain the colapse of a social network.
  - other factors such as UI, management, etc, affect
- model the unraveling process of social networks based on coreness
  - assuming some rate of increase on $`K`$