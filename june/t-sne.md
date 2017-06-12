# 

[video link](https://www.youtube.com/watch?v=RJVL80Gg3lA&index=1&list=PLJannPdvOwss75ZZmCuAycsu35j7Q5Ho-&t=2557s)

# previous methods

- PCA: emphasizing preserving large distances
  - however, large distances are not reliable
  - example: spiral cord shaped data distribution
- ISO map and locally linear embedding: preserves small distances (local information)
  - with their own problems
  
# t-SNE

Key components:

- pair-wise similarity using Gaussian distribution
- projected similarity on lower-dimension space using student-t distribution 
- KL-divergence as objective function

## Pair-wise similarity

- `p_{j|i}`: conditional on each data point, normalized for each row by using band-width parameter `\delta_i`, the delta
  - `\delta_i` to enforce the same perplexity (intrepretated as density)
  - so that different parts of the data space have density
- make symmetric by `(p_{j|i} + p_{i|j}) / 2`.
  - why made symmetric? intuition: similarity is symmetric

## student t distribution on embedded space

To account for the fact that disimilar points (small `p_ij`) are even further away (even smaller `q_ij` if using the same kernel).

How to make `q_ij` be closer to `p_ij`? Increase `q_ij` a bit using some heavy tailed distribution (Gaussian is not heacy tailed).

## KL divergence

a discrepancy measure between probability distributions.

the asymmetric property is suitable here because:

- if `p_ij` is large, then `q_ij` should be large (close to `p_ij` )to avoid large penalty
- however, if `p_ij` is small, then `q_ij` does not have to  be small

in this way, local similarity is preserved

# intepretating the gradient

A node is pulled/pushed by its close neighbors by different forces. Forces are defined by their similarity and current position, etc.

# time complextiy

`O(n^2)` to compute the similarity matrix `p_ij`.

# Speeding it up

Merge far away (but mutually similar) nodes into "centroid" so we only need to consider one representative. 

Space partition to data points to a tree (similar to KD-tree).

For each target node, it only connects to `log(N)` other "nodes" (`log(N)` because of the tree structure).

- How to select the "other nodes"? DFS on the tree from root until some intermediate/centroid is far enough. 

So final space complexity is `O(N log (N))`

# Multiple maps

The motivation is projecting word into vectors (word embedding).
However, words can be ambiguous.

Example: `river ~= bank ~= bailout`, however `river` is not similar to `bailout`. 

A better approach, associate each word with weights in different contexts/maps. 
For example, `river` has weight 1 in context A (geography), however it has weight 0 in context B (financial).
On the other hand, `bailout` has weight 0 in context A (geography), however it has weight 1 in context B (financial).
Finally, `bank` has weight 0.5 for both contexts.

In this way, we can "differentiate" the similarity by different contexts.


# Learned

- an example on why preserving local similarity
  - preserving large distance is unreliable
- use of KL-divergence to encourage preserving local information
- use of heavy tailed student t distribution (w.r.t Gaussian) to allow disimilar points to be even further away in embedded space
- speedup of t-SNE: reduce the kernel matrix using Quadtree and space partitioning
  - space spartitioning is used for KD search as well
- multi-maps: use different weights to differentiate the similarity under different contexts. 

# further questions

- t-sne applied to graphs
- t-sne applied to graphs with node attributes, etc