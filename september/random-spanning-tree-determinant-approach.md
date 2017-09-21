# basic idea

1. calculate the *marginal* probability `\text{Pr}_{T \sim \mu}(e \in T)` of an edge being in the tree
   - $\mu$ is the spanning tree probability distribution
   - the probability is calculated by `\frac{\det(L_{G \text{\\} \{e\}})}{L_G}`, where `\text{\\}` is edge contraction operation
2. sample edges according to `\text{Pr}_{T \sim \mu}(e \in T)`


note that:

1. running time `O(mn^3)`: for each edge we evaluate the determinant
2. it works with weighted graph


*question**

I still don't understand why we sample tree by simple sample from edges

# source

https://homes.cs.washington.edu/~shayan/courses/cse599/adv-approx-1.pdf