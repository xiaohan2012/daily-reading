# machine learning coffee talk, Jan 15

main challenges:

- computational
  - model complexity: many parameters
  - space complexity: to store the model
- statistical (label imbalance)


for one-vs-rest classifier on wikipedia

- model size large (970 GB)
- training time long (3 months)

however, 

- 97% of the weights (abs value) are < 0.1 (unnecessary) --> 3GB (if we remove them)
- distributed computing (merit of one-vs-rest classifier) --> 6 hours (using 400 cores)


some idea on why it works

- algebraic connectivity (eigen value of the laplacian matrix of the label cooccurence graph)
- the larger the label space, the smaller value of algebraic connectivity


lessons

- hamming loss might be useful for this task
- need to doubt the unverified claims in papers
- simple sometimes is good (for example the binary relevance method)