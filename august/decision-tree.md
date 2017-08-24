# for classificaiton

[video](https://www.youtube.com/watch?v=p17C9q2M00Q)

basic idea: 

- parition the space into regions like this

![](figs/space-partition.png)

internally, its a tree structure

![](figs/tree.png)

- each leaf represents a region
- prediction is made by going down the tree by evaluating the decision rules and label it by majority voting

# for regression

suppose given a set of 1d points, $`(x_1, y_1), \ldots, (x_n, y_n)`$, where $`x_i, y_i \in \mathbb{R}`$

like the following:

![](figs/regression-tree-input.png)

then we have selected the split points (on real domain)

![](figs/regression-tree-split.png)

and build a tree that minimizes the training error:

![](figs/regression-tree.png)

training error is meaured at each **leaf node** as:

`\sum_i (y_i - \hat{y})^2`