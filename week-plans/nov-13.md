# plan

** immunization **

- monotonicity and modularity of our model: prove or disprove
  - [X] non-monotonic
  - sub/super modularity
- [X] k-core based formulation: add edges to increase total increase of core number:
  - [X] what's the motivation (.5h)? 
  - [X] prove its sub/super modularity (1h)
  - [X] present the formulation to Lorenzo and Francesco (1h)
- [ ] adding single edge case
- [ ] adding `k` edges case

** active learning **

- [ ] understand the query process
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


## single edge case 

observation:

- only nodes with the same core number can be affected and they must form a connected component, this gives an upperbound


then suppose we calculated the effect of an edge, we can filter out connneced components whose upperbound is lower than the effect value. 

ideally, the edge caculate affect as many node as possible. 


 