# Max-Margin DeepWalk: Discriminative Learning of Network Representation, IJCAI 2016

[paper](http://thunlp.org/%7Etcc/publications/ijcai2016_mmdw.pdf)

# overview

input: network $`G=(V, E)`$, labels on some nodes (single label)
output: embedding of nodes that is learned for the labels

**deepwalk + multiclass SVM**

# deepwalk as matrix factorization (MF)

$`M_{ij} = \log [\frac{e_i (A + A^2 + \ldots + A^t)}{t}]_j`$

$`e_i`$ indicator vector.

approximation in this paper

$`M = (A+A^2)/2`$.

why dropping the $`\log`$? author claims adding log gives more non-zero entries -- weird.

## objective function

parameter: $`X, Y \in \mathbb{R}^{k\times|V|}`$

goal: minimize

$`||M - (X^T Y)||^2_2 + \frac{\lambda}{2}(||X||^2_2 + ||Y||^2_2)`$

$`X`$ serves as the node embedding

# SVM DW

## SVM

using the embedding $`X`$ on $`T`$ labeled nodes. 

suppose there are $`m`$ classes, then the linear classifier is $`W=[w_1, \ldots, w_m`]$.

for the $`i`$th example, we need the classifier to give large margin:

1. $`w_{l_i}^T x_i - w_{j}^T x_i \ge 1 - \xi_i`$ if $`j \neq l_i`$
2. $`w_{l_i}^T x_i - w_{j}^T x_i \ge 0 - \xi_i`$ if $`j = l_i`$

also, we want to regularize the parameter $`W`$ and slack variable $`\xi`$

so the objective is:

![svm](https://ibin.co/3XkfbkM1JgXJ.png)

how to solve SVM?


## summing up

just, svm objective + deep walk objective

# learned

1. another way to see deepwalk as matrix factorization
2. review of svm
3. what? this is a IJCAI paper?