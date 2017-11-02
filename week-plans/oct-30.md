# week plan

- [X] friendster paper (1 h)
- [X] influence maximization: influence definition, problem definition and approximation method (2~3 h)
- [X] resilience measures (2 h)
- find and read related work: modify graph structure to increase graph robustness (1 h)
  - example: https://www.researchgate.net/publication/301313634_Optimizing_network_robustness_by_edge_rewiring_a_general_framework
- Network Creation Game (1 h)

- extreme multilabel classification (1 h)
  - what's the prediction time of  SIGIR paper? 
  - how does it reduce it?
- two more papers on compression/decompression (new)
- metric learning tutorial: https://arxiv.org/pdf/1306.6709.pdf (1 afternoon)

## goal

- problem formulation of the friendster problem

# Sunday

- read fastxml paper

next step:

- understand the compression-decompression techniques
  - commonality and difference
- understand the tree based methods
  - LPSR and MLRF


# monday

- [X] **frog**: think about how to sample cascade (1.5 h)
  - how to estimate $`H(t_y \mid O)=\int p(t_y \mid O) d t_y`$? using cascades?
  - what distribution should the cascades be drawn from?
  - same question for conditional entropy part
- [X] graph robustness measure: (1.5 h)
  - https://arxiv.org/pdf/1311.5064.pdf
- [X] read https://arxiv.org/pdf/1302.6109.pdf (1.5 h)
  - how social resilience is quantified
- meeting with Cigdem (2 h)

## frog and discussion

problem is how to estimate $`p(t_y \mid O)`$ using simulated cascades

- be formal about the form with hidden variable $`C`$

discussion:

- Cigdem thinks sampling from cascade to estimate entropy is not straight forward
  - she is thinking about querying selection based on minimizing prediction error
  - reminds of the standard and non-standard approach to do active learning
- suggests two papers to check
- plus Aris' two papers

next steps:

- Kleinberg's paper
- effective resistance note
- four papers by Aris and Cigdem

# Tuesday

- [X] anchored k problem paper (1 h)
  - what's the problem formulation
- [X] frog: think about our formulation (2 h)
- [X] Toward optimal active learning through monte carlo estimation of error reduction: http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.137.6296 (1 h)
  - what's the objective to optimize here?
- [X] Fabio's active learning paper (1 h)
  - what's the objective to optimize here?
- [X] active learning for uncovering biological network: http://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005466 (1 h)

## frog

formulated the problem, the objective has recursive form. 

what's unknown:

- is it NP-hard?
- submodularity on recursive function
  - https://arxiv.org/pdf/1701.08939.pdf: section 4.1

next:

- can we reduce the original problem as a special case to our problem?
- if not, can we us the NP-hardness proof in kleinberg's paper to our case?
- related problem: add edges to maximize some function on k-core (ego, or global)
  - what's the driving factor for network unraveling (friendster paper)

## active learning

- uncover biological networks: interesting and different problem. 
- to avoid general query selection model, reminds of sensor placement papers

next:

- sensor placement papers (the one Kiran sends me)

## summary today

- formulated problem for anchored problem, to do
  - NP-hardness
  - submodularity
- ways other than entropy, mutual information to solve problem
  - expected error
  - size of connected component

# wednesday: hobby hackathon

- [X] understand the paper (1h)
- [X] relate it to the Matlab code (1.5 h)
- [X] rewrite it in Python (whole afternoon)
  - and experiment with at least one dataset


# thursday

- [X] frog: how to estimate $`p(t_y \mid O)`$ (1.5 h)
  - integation over all possible cascades part, make it formal
  - uniform sampling part, is it correct?
  - if the above is correct, what's the actual sampling problem?
- if time permitted, think about what's the prediction error in our case and how to plug in the method in Roy 2001. 
- [ ] NP hardness proof of anchored k-core problem (1.5 h)
  - possibly apply the technique to prove our problem
- [ ] related work: modify graph structure to increase graph robustness (1.5 h)
  - cited and citing in https://www.researchgate.net/publication/301313634_Optimizing_network_robustness_by_edge_rewiring_a_general_framework
  - what are resilience definition, problems, methods?
- [ ] discussion with Cigdem (1.5h)

## frog

formally derived $`p(t_y \mid O)`$ which is $`- \frac{1}{P(O)} \sum\limits_{t_y} f(t_y, O) \log f(t_y, O) + \frac{\log P(O)}{P(O)}`$, 
where $`f(t_y, O)=\sum\limits_{C \text{ respects } O \text{ and } t_y} P(X)`$

- how to estimate both `f(t_y, O)`and `P(O)`?
- is it \#P-complete?

## anchored k-core hardness

- reduction from set-cover
- checked the restricted case where `|S_i| < k` (`v` won't be saved unless anchored)
- the more general case has not been checked

tried to prove the NP-hardness by reduction from set cover. 

however, when constructing the graph, how can ensure only the "set" nodes are anchored not the "element" nodes.

- maybe try to "pseudo-anchor" (e.g, contain it in a n-clique) the "set" nodes so that anchoring any "element" does not give more benefit than anchoring "set" nodes. 
  
a related problem: https://cs.stackexchange.com/questions/83330/np-hardness-of-maximum-set-cover-with-element-level-submodular-function

related papers:

- http://luthuli.cs.uiuc.edu/~daf/courses/Optimization/Paperssubmodular/nemhauser.pdf
- multi-cover problem: https://www.cc.gatech.edu/people/home/mihail/D.read2010/Rajagopalan_Vazirani.pdf

# friday

- [ ] sensor placement papers sent by Kiran
  - review it
  - probabilistic infection model