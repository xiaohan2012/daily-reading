# plan

**core maximization**

- [X] put them in the doc and email the people about the result
- [ ] hardness proof: search related problem of core-number maximization / resilience maximization (1h)

**active learning**

- [ ] report the result 
- [ ] `inference.py` using the `sample_pool.py` with incremental support (1h)
- [ ] measure the score using the sampling based inference method (0.5h)


**SDM**

- [ ] tweet it using hashtag
- [ ] put it in arxiv

**presentation**

- [ ] more technical details

**label embedding xml**

- [ ] visualize the embedding (1h)


# Tuesday

- [X] frog: can we use dynamic programming to solve single node version? (1h)
- [ ] search for common NP-hard problems that are reduced from (1h)
- [X] integrate `random_steiner_tree` to sampling pool (1h)
  - speed comparison
- [ ] https://www.researchgate.net/profile/Minh_Phan22/publication/319259804_NeuPL_Attention-based_Semantic_Matching_and_Pair-Linking_for_Entity_Disambiguation/links/59d7afa9458515bbfee8df7b/NeuPL-Attention-based-Semantic-Matching-and-Pair-Linking-for-Entity-Disambiguation.pdf (1h)

## frog

it seems impossible because getting the gain of the edge being considered requires knowing whether other edges are added.

## speed comparison

`cut` and `loop_erased` is very fast. however, constructing the `GraphView` is costly. 

## integration

why `isolate_disconnected_components`?

# Wednesday

- [X] frog: search papers on how to prove inapproximability (1 h)
- [X] make `test_query_selection` pass why `isolate_disconnected_cc`? 
- [X] search for other related inference methods (1h)
- [X] entity linking paper (LSTM, pair-linking, experiment) (1h)

## related inference methods

- Polina's paper: reconstructing an epidemic cascade over time
  - https://github.com/polinapolina/reconstructing-an-epidemic-over-time
  - in Python
- Hidden hazards: Finding missing nodes in large graph epidemics.
  - http://www.cs.vt.edu/~badityap/CODE/netfill-code.tgz
  - in Matlab
- our SDM 2018 method

three is enough


# Thursday

- frog: [X] GraphSage: https://arxiv.org/pdf/1706.02216.pdf (2h)
- [X] improve the plot (node color consistent with core number, easy to interpret the change) (1h)
- [X] basic structure according to the survey paper (1+1h) 
  - direct method
  - neighborhood
  - convolution-based (why the name)
  - subgraph embedding
  - open challenges (with my thinking and my own problems)


# Friday

- frog: [ ] search papers on metric learning on bipartite graph? (1h)
- [ ] [matrix as factorization](https://arxiv.org/pdf/1710.02971.pdf) (1h)
- [ ] optimize `query_score` method using Cython (2h, do better than 6.4ms, or 13 secs per run)
- [ ] outline the experiment sections, what experiments should we include (1h)
- [ ] run experiment: dataset=grqc, strategy=predition_error with  different sampling methods (0.5h)
- [ ] integrate our order-based steiner into the method (1h)
- [ ] problem and method for label embedding-based xml (0.5h)
  - write down the training objective of learning the projection matrix using the probabilistic approach?

