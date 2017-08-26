# overview

for learning to rank tasks, learn a loss function defined by nDCG, because that is the evaluation metric.

however, optimizing by nDCG involves the **rank position**, thus not very easy. 
main idea:

- relax the objective by expected nDCG loss thus, providing a lower bound
  - the relaxation goal is to convert the rank position to real-valued variable
- then, maximize the lower bound

further, adaboost is used

the weak learner is just a binary classifer: $`f(d, q) \rightarrow \{0, 1\}`$. 

the input to the learner is just a set of features between $`d`$ and $`q`$

# learned

- bound optimizing method: define a lower/upper bound of an objective function, and optimize the bound
- a pointer for direction on relaxing nDCG objectives
- different learning to rank approach:
  - point-wise: $`F(q, d)`$
  - pair-wise: $`F(q, d_1, d_2)`$
  - list-wise approach: $`F(q, d_1, \ldots, d_m)`$, nDCG belongs here.