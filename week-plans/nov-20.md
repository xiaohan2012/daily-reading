# plan

**active learning**

coding:

- try on larger dataset (1 h)
- steiner tree sampling algorithm in C++ (3 h)
- integrate (2h)

reading:

- network entropy paper (1 h)
- pac learning paper (1 h)
- find papers on reconstructing from spanning tree on closure (minimize the error) (1h)
- [Sampling Random Spanning Trees Faster than Matrix Multiplication](https://arxiv.org/pdf/1611.07451.pdf) (1.5h)

**core maximization**

reading:

- [ ] [Fully Dynamic Algorithm for Top-k Densest Subgraphs](https://arxiv.org/pdf/1610.05897.pdf) (2h)
- check paper [1] to get more ideas for pruning or computing good candidate nodes (which node is more likely?)

thinking:

- [ ] intra-core intra-`nc`: how to detect such subgraph, even it's not the inner most core? (1h)
  - related to dense subgraph detection
  - however, the subgraph might not be in the inner most core
- [ ] single inter-core edge, we can use the quasi-clique pattern to determine the best node? (1h)
- adding multiple edges, detecting the quasi-clique version
- prove hardness (1h)
- design a smart data structure to keep all the information we need (incremental)

coding: 

# monday

- frog: intra-core intra-`nc`: how to detect such subgraph, even it's not the inner most core  (1h)
- single inter-core edge, we can use the quasi-clique pattern to determine the best node?  (1h)
- [Fully Dynamic Algorithm for Top-k Densest Subgraphs](https://arxiv.org/pdf/1610.05897.pdf) (2h)

- try on larger datasets (1 h)
  - try graph with one million nodes+, see the bottle neck
- steiner tree sampling algorithm in C++ (2 h)
- disccusion (2h)

# tuesday

- 

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


