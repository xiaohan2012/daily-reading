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

$`w_k`$ can be related to the lower bound in the network games. 

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
2. immunize $`k`$ nodes to minimize spread



# Wednesday

- frog: 
  - https://theory.stanford.edu/~jvondrak/data/submod-tutorial-1.pdf and https://courses.engr.illinois.edu/cs598csc/sp2010/Lectures/Lecture20.pdf (1.5 h)
  - influence maximization submodularity (0.5 h)
  - is the function a submodular function (0.5 h)
- one possible formulation: given some infected node and some infection probability defined on node degree, immunize $`b`$ nodes so that the expected cascade size is minimized. 
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
- maximizing monotone and submodular function: $`(1-1/e)`$

## immunization (fixed infection probability)

assume infection probability is fixed. 

problem:

given source node $`s`$, a sampled graph (by infection probability), we want to remove $`b`$ nodes so that the connected component where $`s`$ is in has minimize size. 

### sub/super-modularity

the size function given removed nodes is super-modular (non-decreasing). 

**prove it!**

for multiple sources, the function seesm to be super-modular as well

### NP-hardness

reduction from [component order connectivity](https://cs.stackexchange.com/questions/12789/find-which-vertices-to-delete-from-graph-to-get-smallest-largest-component)

given a graph $`G`$ such that $`s`$ is connected to many leave nodes. this makes sure the $`\text{argmax} C \in cc |C| = C_s`$

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

TODO: can we apply the technique in this paper to our work. 

### stay/leave as network games

TODO: can we define such game? and the equilibria is the probability to stay?

## active learning project

done:

- score for prediction error based

not done:
  - $`query_strategy_test`$ using  $`simulator`$	
  - $`QueryGenerator.__init__`$  not accepting $`obs`$

## sleec

realized I didn't do validation step, so the result is not very reliable. 

also, $`lambda1`$ should be might smaller than $`lambda2`$ and train with larger iteration number. 

# Thursday

- frog: https://stanford.edu/~jugander/NetworksNIPS2015/papers/NIPS_Networks_2015_paper_28.pdf (2.5 h)
- similarity/difference between IC model and our model (0.5h)
- proof of \#P-hardness: http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.302.362&rep=rep1&type=pdf (1.5h)
- active learning
  - test of simulator on all query methods (1h)
  - experiment using simulator, compare query process using different strategies (1h)


## frog

- a generalization of network design problem based on manipulating edge probabilities
- edge deletion/addition to minimize/maximize spread (super-modular function)
- maniulate edge probabilities on continuous time diffusion model to minimize transportation time

## mapping our model to infection process

mapping our model to infection process. 

- adding dummy node and connect it to all other nodes with infection probability
- edge is associated with some probability to infect the target from source
  - need to play with the probability, for example, if u's two neighbors, x, y get infected at the same time stamp, then we can set $`p_{x, u} = \frac{1}{\deg{u} + 1}`$ and $`f_{y, u}=0`$ to simulate the effect of infection via edge. 

observation:

- edge $`(u, v)`$'s infection probability will be evaluated whenever $`v`$ is infected. 
  - and it depends on $`v`$ current degree. 
- immunizing nodes means setting their outcoming edges' probability to zero.
- consider a star graph, the center nodes have many neighbors. using our model. in expectation half of its neighbors will leave however, because $`N`$ is large, center node will stay with high probability. 

main chanllenges:

- edge probability is evaluated dynaimcally in contrast to IC model with pre-defined edge probability
  - can we fix it somehow? for example, lower-core nodes have a weaker influence on higher-core nodes while higher-core nodes have a stronger influence on lower-core nodes. 

two directions:

- map it to IC model and devise node immunization strategy
  - edge probability needs to be defined to reflect unraveling influence
  - initial infection probability needs to be defined
  - why giving up this approach? dynamic edge probability? not sure if it captures the unraveling process?
  - are there any similar work? related to Friday frog
- add edges to optimize some function on k-core
  - what's the intuition for the objective function?
  - how about add weight to each node? to reflect individual importance. 
  - or add edges to optimize the sum of increase of each node's core number

## active learning

observation: the new query strategy selects nodes at the boundary of the graph

possible reason: these (uninfected) nodes matches the prediction (self-reinforcing):

- `p(y=0 | q)=1` and `E_{D+ (q, 0)}` is maximized because (it matches the current prediction)
- `p(y=1 | q)=0` and `E_{D+ (q, 1)}`: so this term can be ignored

in other words `p(y=0 | q)` is not estimated properly in this case.

1. the observed data is quite focused in one small area (cannot be avoided)
2. the sampled tree is quite small

what can we do?

- sample larger/better tree

# Friday

- frog: supermodular function, example https://dl.acm.org/citation.cfm?id=2623704 (2 h)
  - related work
  - relation to our problem
  - how to prove supermoduarity?
  - how is supermodularity used? for min/max problems? 
  - just read that max submodular is like min supermodular (give some appx-guarantee) and min submodular is like max supermodular (exist polynomial algorithm) is it true?
  - is it worth to do the same for IC model
- try to *disprove* the function is submodular/supermodular (1.5 h)
- think about why active learning experiment gives that result (1.5 h)
  - what would be a good query (without time)? what are other running examples?
  - what are the scores of other nodes? what would the score of the node near the obs be like? and in reality, what is it like?
- discussion with Cigdem (2h)
  - ask her if there exists influence maximization papers on dynamic changing influence probabilities
  - show the result and my thinking
