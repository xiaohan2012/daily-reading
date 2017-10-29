# week

- parallel paper
- different definition of communities: k-truss, k-core, quasi-closure
- community search (how to define a community and algorithms)


# Tuesday

- GAN
  - a generative model
  - generating synthetic data (images for example), to fight label inbalance problem for example
  - fill missing part of an image

# Wednesday

## "parallel" paper

two main ideas:

- parallel processing of edges in a matching
- for edges in the same core, do it in batch

# Thursday


## community search papers

- k-truss decomposition
- simple index
- motivation for TCP index

## guided/biased cascade generation

for continuous time model, one way is:

- first generate cascade samples
- then use sampling-important-resampling to resample the cascasdes. 
- however, requires assuming the source node and `t_s`

related:

- assuming the source is known
- joint inference on source and other infected nodes. 

## near optimal sensor placement

- gaussian process works on the finite space, how prediction works not so clear
- gaussian process gives closed form of conditional entropy
- mutual information formulation simplified to the different between two conditional entropy terms
- scaling up using lazy evaluation and local kernel

## mutual information for continous time diffusion model

`\text{argmax}_y H(y) - H(y \mid V^{'} - y)`, where `V^{'}=V-O`

how to evaluate the conditional entropy

## pytorch vs tensorflow

https://medium.com/towards-data-science/pytorch-vs-tensorflow-spotting-the-difference-25c75777377b

- pytorch: more pythonic, developer friendly, dynamic graph, pdb debugging supported, no native support for tensorboard but there are alternatives
- tf: static graph, easier deployment, supports distributed training

## source code for order-based core maintenance

- `GLIST::ComputeCore`:
  - computes `core` 
  - builds the `O_k` (`node_`, `head_` and `tail_`)
  - computes `mcd`

# Friday

## revisiting community search

new questions:

- comparison between different community definition, k-truss, k-core, quasi-clique, etc
  - k-truss vs k-core for example
- what is good and bad about k-truss? (no explicit diameter constraint)
  - related paper is *Closest Truss Community Search* by Huang, VLDB 2016

- not so many work on community search, even fewer on complex graphs (attribtued, etc)

## community search in heterogenous graphs

can be seen as fined-grained version of social circle detection. it gives extra information on each circle

two entities are reachable from each other via at least `k` paths constrained by certain meta-path. 

examples:

academic network, given an author `a` as query, find the subgraph constaining its co-authors, papers, topics and venues

a straightforward baseline: 

1. label the authors by paper topics
2. perform attributed community search
3. filter the co-authored papers by topic

the goal is not clear. 

**to read**: what is a good community in heterogenous information networks?


## mutual information for cascading process

`H(y) = \int p(t_y \mid O) \log p(t_y \mid O) d t_y`

the goal is to generate cascades `C` that respects `O`

note that `p(t_y \mid O) = \int p(X \mid O) p(t_y \mid X) d X`

## sampling cascades

idea of `delay-bfs`: connect the terminals level by level (level refers to time)

`delay-bfs` can be modified to sample a order-respecting cascade. 

however, if transmission delay information is available, how is the sampling done?

# week review

