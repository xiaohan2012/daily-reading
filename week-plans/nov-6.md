# monday

- [X] frog: network games, two papers and can it be used to define our problem (2.5h)
- [ ] NP-hardness: proof in influence maximization paper and our case (1h)
- [ ] discussion (2h)


## frog

supermodular function:

- http://www-bcf.usc.edu/~shaddin/cs599fa13/slides/lec24.pdf
- increasing marginal returns

nash equilibrium:

- https://www.economist.com/blogs/economist-explains/2016/09/economist-explains-economics

## problem formulation

given a non-negative $`w_k`$ weight for each core $`k`$, add $`b`$ edges to maximize

$`\sum\limits_{k=1}^{K} w_k size(shell_k)`$

`w_k` can be related to the lower bound in the network games. 

learned

- games on network
  - not sure why supermodularity is important
- relation between largest nash equilibria and core number (lower bound)
- proposed a problem formulation on maximization some function on k-core

## np-hardness

in influence maximization:

- IC model: reduction from set cover, edges are created directed so to avoid selection of element nodes. 
- IT model: 

## discussion with Aris

active learning:

1. query selection
2. evaluation using some recontruction method

random process:

1. some node leaves and the contagion spreads
2. immunize `k` nodes to minimize spread



