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


- C++ programming
- https://medium.com/towards-data-science/pytorch-vs-tensorflow-spotting-the-difference-25c75777377b

