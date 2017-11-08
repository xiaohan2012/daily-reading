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



# Wednesday

- frog: 
  - https://theory.stanford.edu/~jvondrak/data/submod-tutorial-1.pdf and https://courses.engr.illinois.edu/cs598csc/sp2010/Lectures/Lecture20.pdf (1.5 h)
  - influence maximization submodularity (0.5 h)
  - is the function a submodular function (0.5 h)
- one possible formulation: given some infected node and some infection probability defined on node degree, immunize `b` nodes so that the expected cascade size is minimized. 
  - is the above function submodular (0.5 h)
  - np-hard? (0.5 h)
  - or the infection can start from multiple nodes
  - relation to network immunization strategy: find related papers (1 h)
- active learning experiment
  - calculate the expected prediction error (without using current time, 1h)
  - plot the query selection process and compare it with entropy based method on grid (1 h)
- night (1 h)
  - more training epochs
  - take the mean on l2 regularization 
  - use sparse tensor
    

## frog

- submodular function minimization: polynomial time
- maximizing monotone and submodular function: `(1-1/e)`

## immunization (fixed infection probability)

assume infection probability is fixed. 

problem:

given source node `s`, a sampled graph (by infection probability), we want to remove `b` nodes so that the connected component where `s` is in has minimize size. 

### sub/super-modularity

the size function given removed nodes is super-modular (non-decreasing). 

**prove it!**

for multiple sources, the function seesm to be super-modular as well

### NP-hardness

reduction from [component order connectivity](https://cs.stackexchange.com/questions/12789/find-which-vertices-to-delete-from-graph-to-get-smallest-largest-component)

given a graph `G` such that `s` is connected to many leave nodes. this makes sure the `\text{argmax} C \in cc |C| = C_s`

as single-source version is a special case of multi-source version, the multi-source version is also NP-hard.

## network immunization papers

spectral-based:

- Node Immunization on Large Graphs: Theory and Algorithms
  - SIS model
- [Scalable Approximation Algorithm for Network Immunization](https://arxiv.org/pdf/1711.00784.pdf)
  - greedy

can we define some epidemic threshold for our stochastic process, 
like [Epidemic Thresholds in Real Networks](http://cs.stanford.edu/~jure/pubs/virus-tissec.pdf)
- in contrast to using simulation to approximate the value

TODO: can we apply the technique in this paper to our paper. 

### stay/leave as network games

TODO: can we define such game? and the equilibria is the probability to stay?

## active learning project

done:

- score for prediction error based

not done:
  - `query_strategy_test` using  `simulator`	
  - `QueryGenerator.__init__`  not accepting `obs`

