# plan

## active learning

coding:

- [X] try on larger dataset (1 h)
- ~~steiner tree sampling algorithm in C++ (3 h)~~: 
  - integrate (2h)
  - give up becasue it's not the bottle neck  

reading:

- network entropy tutorial (1 h)
- pac learning paper (1 h)
- find papers on reconstructing from spanning tree on closure (minimize the error) (1h)
- [Sampling Random Spanning Trees Faster than Matrix Multiplication](https://arxiv.org/pdf/1611.07451.pdf) (1.5h)

## core maximization

reading:

- [ ] [Fully Dynamic Algorithm for Top-k Densest Subgraphs](https://arxiv.org/pdf/1610.05897.pdf) (2h)
- check paper [1] to get more ideas for pruning or computing good candidate nodes (which node is more likely?)

thinking:

- [X] intra-core intra-`nc`: how to detect such subgraph, even it's not the inner most core? (1h)
  - related to dense subgraph detection
  - however, the subgraph might not be in the inner most core
- [X] single inter-core edge, we can use the quasi-clique pattern to determine the best node? (1h)
- [X] adding multiple edges, detecting the quasi-clique version
- prove hardness (1h)
- design a smart data structure to keep all the information we need (incremental)

coding: 


## mini-hackathon: SDNE

- [X] pretraining on autoencoder, [ref](https://keras.io/getting-started/faq/)
- [ ] cross validation on the visualization of 20newsgroups
- [ ] tensorboard visualization of label embedding
- [ ] link prediction on test data
- [ ] write blog article


# monday

- frog: intra-core intra-`nc`: how to detect such subgraph, even it's not the inner most core  (1h)
- single inter-core edge, we can use the quasi-clique pattern to determine the best node?  (1h)
- [Fully Dynamic Algorithm for Top-k Densest Subgraphs](https://arxiv.org/pdf/1610.05897.pdf) (2h)

- try on larger datasets (1 h)
  - try graph with one million nodes+, see the bottle neck
- steiner tree sampling algorithm in C++ (2 h)
- disccusion (2h)

## frog

lemma about the "fingerprint" of an `nc` of size `L` be have core `k`. 

proof needs to be done

question:

- can we this fingerprint to decide if an addition edge will cause core number change?
- or even grouping the edges for batch processing so that there are as many batches as possible such that the batch introduces core number updates

## top-k densest subgraphs

- snowball: connected component with highest core number
- update involves moving nodes across different snow balls or moving/in out

## sampling steiner tree without visiting all nodes

[some observation](sampling-steiner-tree-without-visiting-all-nodes.md)

##  try larger datasets

so slow


# tuesday

- frog (2h): 
  - upperbounds for different types of edges
  - formalize greedy algorithm
  - data structure
- meeting: (1.5h)
- pac learning paper (0.5 h)
- active learning large graphs (1.5 h): 
  - profiling on large graphs
  - re-use steiner trees (only delete those infeasible ones)
  - calculate speed-up
- C++ code of steiner tree sampling (2.5 h)

## meeting

learned:

- be specific about the algorithm, data structure
- it's already a good problem, be ready to dive into the details, instead of thinking other high level ideas
- don't rush

- data structures designed on the paper

next questions:

- how to maintein the information incrementally?
- write down the pseudo code

## bottle neck of prediction-error based approach

[two ways to address the scalability issue](november/active-learning-project-scaling-up.md)

## random spanning tree C++

- http://www.boost.org/doc/libs/1_65_1/boost/graph/random_spanning_tree.hpp
- https://www.cs.cmu.edu/~15859n/RelatedWork/RandomTrees-Wilson.pdf

evening:

- tensorboard visualization of label embedding

# wednesday

- 

# thursday

frog:

- [ ] SLEEC (0.5h)
- [ ] Robust Extreme Multi-label Learning (1h)
- [ ] AnnexML: Approximate Nearest Neighbor Search for Extreme Multi-label Classification, KDD 2017.  (2h)
- [ ] Deep Learning for Extreme Multi-label Text Classification (1h)
- [ ] Deep Extreme Multi-label Learning (1h)


