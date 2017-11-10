# goal

add/delete edges to maximize/minimize spread size under linear threshold model

relies on:

- alternative representation of LT model, live-edge graph repr
- explores the states in cascade space before/after the edge deletion/addition

# related work

- IC model: maximize spread by adding nodes (non-submodular)
  - http://www.cs.cornell.edu/gomes/papers/UAI2010-cascades.pdf
- influence blocking maximization problem [3, 9]
  - https://wiki.eecs.yorku.ca/course_archive/2014-15/F/4412/_media/social_networks.pdf
  - [Influence blocking maximization in social networks under the competitive linear threshold model](https://arxiv.org/abs/1110.4723)


# super/submodularity optimization problems

- R. Iyer, S. Jegelka, and J. Bilmes. Fast semidifferential- based submodular function optimization. In ICML, 2013.
- G. Nemhauser, L. Wolsey, and M. Fisher. An analysis of the approximations for maximizing submodular set functions. Mathematical Programming, 14, 1978.

# proof related

core idea: think about the space of all possible cascades before and after removing an edge.

- if they states does not have a 1-to-1 mapping, then need to explore how each state in the space correponds to some other state within/cross spaces. 
- also, need to compute the probability of each state to prove monotonicity and superomodularity

for edge deletion problem, they prove the spread size function is:

- monotonically decreasing
- supermodular

this is just like monotonically increasing and submodular function. and greedy gives similar gaurantee

for edge addition, it's monotonically increasing and supermodular. thus, need some other approximation algorithms

# comment on IC model

- it's already done but in a master thesis


# proving the property in our case

- is there a 1-to-1 mapping?
- if so, is it super/sub-modular
- if not, need to probability?