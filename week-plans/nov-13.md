# plan

** immunization **

- monotonicity and modularity of our model: prove or disprove
  - [X] non-monotonic
  - sub/super modularity
- [X] k-core based formulation: add edges to increase total increase of core number:
  - [X] what's the motivation (.5h)? 
  - [X] prove its sub/super modularity (1h)
  - [X] present the formulation to Lorenzo and Francesco (1h)
- [X] adding single edge case
- [ ] adding `k` edges case

** active learning **

- [X] understand the query process
  - try more examples
- [X] precision/recall using sampling based inference
- [ ] precision/recall using inference method in SDM submission


** multi-label **

- [X] search for approaches using label embedding (1h)
- main point of 
  - [ ] SLEEC (0.5h)
  - [ ] Robust Extreme Multi-label Learning (1h)
  - [ ] AnnexML: Approximate Nearest Neighbor Search for Extreme Multi-label Classification, KDD 2017.  (2h)
  - [ ] Deep Learning for Extreme Multi-label Text Classification (1h)
  - [ ] Deep Extreme Multi-label Learning (1h)

** mini hackathon

- [X] understand the paper
- [ ] implement it in Keras 
- [ ] experiemt: network reconstruction, classification


# Monday

- frog: sub/super modularity of our model (3h)
- Fast semi differential- based submodular function optimization (1.5h)
- report precision/recall and/or precision@k (1.5h)
  - sampling-based  
  - SDM submission method
  - on grid, dolphin, karate club
- present result to Cigdem (1h)
  - also ask her about cascade model dynamically evaluated edge probabilities 

## frog

- cannot prove monotonicity for the spread function
- https://gitlab.com/xiaohan2012/daily-reading/blob/master/november/unraveling-problem-submodularity.md

next step:

- other infection functions: k-core, edge-wise, etc
- vertex removal case

## semidifferential

got the main idea, still confusing

## active learnig

todo: evaluation

# Tuesday

- frog: sub/super modularity (1.5h)
- variants of cascade model: based on k-core and edge-wise infection (1.5h)
  - motivation
  - monotonicity
  - submodularity
- experiment evaluation using sampled-based inference(1h)
- review what to say in the meeting (0.5h)
- meeting (2.5h)

## frog

- reducted the form to a simpler one
- if non-monotonicity holds, then neither super-modularity nor sub-modularity holds

## maximizing k-core numbers by add edges

[document](november/core-number-maximization.md)

- monotonic
- but neither submodular nor supermodular

## active learning

- pagerank > entropy > prediction error > random
- used [average_precision_score](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html#sklearn.metrics.average_precision_score)
- http://193.166.24.212:9999/notebooks/average_precision_score.ipynb

## discussion

- switch to maximizing k-core problem

todo:

- write problem formulation, disprove of submodularity and supermodularity
- think about one edge case, how to do it efficiently?

# Wednesday

- frog: understand how prediction error selects the query and why it's so bad (3 h): 
  - is average precision a good measure? understand average precision such as its motivation? 
  - why pagerank and entropy are so good at average precision?
  - if average precision is not a good measure, find more reasonable measures. 
  - pick examples that prediction error-based method perform worse on lattice
- *efficiently* select the single edge to add with the maximum number of affected nodes (1.5 h)
  - there are `O(n^2)` edges to add, can we reduce the time complexity to `O(n)`?
- formalize the formulation (both problems), single edge algorithm, disproof sub/super modularity (1 h)
- discussion with Cigdem (1h)

## frog

- found a bug in infer infection probabilities, need to remove uninfected nodes as well.
- plotted an example on cascade 81, prediction error-based looks better than other methods

after fixing the bug:

the result varies on datasets. 
in general, random and prediction error are the best. pagerank is the worst. 

- on lattice, prediction error is the best
- on karate, random is the best

## single edge case 

observation:

- only nodes with the same core number can be affected and they must form a connected component, this gives an upperbound


then suppose we calculated the effect of an edge, we can filter out connneced components whose upperbound is lower than the effect value. 

ideally, the edge caculate affect as many node as possible. 


## discussion

next:

- try on larger graphs
- generative model with time information
- sampling time-respecting trees
- entropy of tree

some papers recommended by Cigdem

# Thursday

- [ ] implement it in Keras 
- experiemt: 
  - [ ] visualization
  - [ ] network reconstruction
  - [ ] classification
- meeting with Aris (15:00)
- meeting with Francesco (16:00)

## meeting with Aris

- can we sample steiner tree directly?
  - the transitive closure approach
  - can we bound the sampling error?


## meeting with Francesco

- Write also the other objective function where the higher cores are more important
- Prove hardness
- Check paper [1] to get more ideas for pruning or computing good candidate nodes
- Design a smart data structure to keep all the information we need
- Write a detailed pseudo-code at LaTex
- Start coding/trying
- think about adding multiple edges, detecting the quasi-clique version
- paper by Anis, Aris, etc


# Friday

- minihackathon: joint training done


# Saturday

- frog: sampling steiner tree using transitive closure (1.5h)
  - what's the main challenge that affects uniform sampling?
  - how to circumvent it even within reasonable amount of error
  - find papers if possible
- understanding the email discussion (0.5h)
- probabilistic paper (1h)
  - inferring diffusion network
  - back to source paper
  - can we apply these models in our case
- efficient incremental edge selection (1.5h)
  - can we re-use result from previous iteration (greedy approach)
- write a detailed pseudo-code at LaTex and other objective functions with weights (1h) 
  - fix the time complexity
- to implement the greedy approach, how should be code be written? (0.5 h)
  - write the skeleton
- leave work at around 16:00

## frog

problem formulation: http://193.166.24.212/transitive_closure_problem.pdf

## email

different formulations for query strategy and clarification

## closed-form of node infection probability?

assuming the underlying cascade forms a tree

1) because the underlying cascade tree is not known, we always need tree samples to estimate the infection status

I cannot see how we can get rid of the samples. 

2) one work-around is estimate the infection status probability on the most likely tree. 

## "core" maximization

differentiated 3 types of edges.

[quasi clique detection](november/quasi-clique-detection.md)

- corresponds to intra-core, intra-`nc` case
- usefulness: 
  - determine the number of intra-core edges to add to increase the core number of the whole `nc` (multi-edge case)
  - if this number is largar than 1, it cannot be the one best edge

## incremental update