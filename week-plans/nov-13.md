# plan

** immunization **

- monotonicity and modularity of our model: prove or disprove
  - [X] non-monotonic
  - sub/super modularity
- [X] k-core based formulation: add edges to increase total increase of core number:
  - [X] what's the motivation (.5h)? 
  - [X] prove its sub/super modularity (1h)
  - [X] present the formulation to Lorenzo and Francesco (1h)
- [ ] ask Cigdem if there is any model related to dynamicaly evaluated edge probabilities (0.5h)

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

- [ ] understand the paper
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