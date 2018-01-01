# order statistic tree

goal: besides insertion/removal, support:

1. search: find the node of rank `k`
1. rank: calculate node's rank


variant of binary search tree:

- same structure as BST
- stores additional information on each node `v`: *size of the left subtree*
  - or the number of nodes that are smaller than `v`
  - in other words, `v`'s rank

# search

given rank `k` (1-indexed), find the node of such rank

define the function as `find(tree, k)`

1. start from the root, `u=r`
2. if `size(u)+1=k`, return `u`
3. else if `size(u) + 1 > k`, return `find(left_tree(u), k)`
4. else, return `find(right_tree(u), k-size(u)-1)`

some boundary checking is omitted

# get rank

if `u` is the *right child* of its parent, then parent's left subtree and itself are ranked lower than `u`. 

we climb up the tree until the root. 

1. `r = size(left(x)) + 1`
2. `u = x`
3. while `u != root`
4. if `u = right(u.p)`, then `r += size(left(u.p)) + 1`
5. `u = u.p`

# resource

http://www.geeksforgeeks.org/find-k-th-smallest-element-in-bst-order-statistics-in-bst/