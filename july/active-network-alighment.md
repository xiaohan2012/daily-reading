
- [paper](https://arxiv.org/pdf/1610.05516.pdf)

# network alignment

core idea: 

- named, alignment consistency
- specifically, if a matches a', b matches to b' and a is linked to b, then we expect a' to link to b'

objective function:

`\sum_ij reward(i, j) x_ij + g \sum_ij \sum_kl A1ij A2kl xij xkl`

s.t. `\sum_j x_ij = 1` for each i and \sum_i x_ij = 1` for each j

- NP-hard
- without 2nd objective term, it's related to maximum weight bipartite matching

# query

- relative query: 
  - "which node in the target set is most similar to the source node"
- instead of absolute query: given a and b, are they matching?

# calculating uncertainty

1. compute top-l best matchings using "some method"
   - each matching gives a different but good matching (w.r.t obj function)
2. then each node is associated with a dict `{target node 1: frequency, ..., target node k: frequency}`
3. uncertainty for each is defined from the above frequency map
   - intuitively, a node that are matched to another node most of times is quite certain
4. definition of certainty is `max_i frequency_i`

# learned

first, the integer program of network alignment and it's NP-hard


second, we can apply similar idea for our active network reconstruction paper

- similar to generating top-l matchings, we generate top-l reconstructed trees
- each node will a list of feasible infection periods
- we need to define some certainty/uncertainty score on the above list of periods.
  - naive approach, take the mean of each period so we get a list of numbers, then use standard deviation
  

