# learning to rank

## classifical IR models

based on vector space model:

- input: if/idf/tf-idf vectors on query and document
- outut: similarity(consine) between the two vectors

drawback: 

- only a few features
- parameter tuning can be done by hand

## learning to rank

- more features
- parameters tuning must be data driven


# point-wise approach

given query document pait $`(q, d)`$, return a similarity score. 

## example

using $`q`$ and $`d`$ we can get features such as:

- $`\alpha`$: cosine similarity under vector space model
- $`w`$: the minimum word span that $`q`$ is covered in $`d`$ (the small the more relevant)

given training data (with relevant/irrelevant labels), we can learn a linear regression model that fits such data. 

so variation can be:

- features
- the regression model: SVM, etc

## issues

- class imbalance: more irrelevant than relevant
  - can reweight training instance by class label

- bias towards popular queries
  - can reweight training instance by query frequency

- training objective does not match evaluation: nDGC, MAP
  - reminds the paper on optimizing nDGC directly

# pair-wise approach

given the features of two documents $`d_i`$ and $`d_j`$, predict whether $`d_i`$ is ranked higher than $`d_j`$ or the opposite. 

note the features are derived from the query and the document. for example, the featues can be:

- bm25: depends on both query and document
- pagerank: depends only on document

## example: ranking SVM

transforms rakning problem into classification problem

- input: features on $`d_i`$, $`d_j`$: $`\phi_i`$ and $`\phi_j`$
- output: $`d_i>d_j`$ if $`\mathbf{w}(\phi_i - \phi_j)>0`$

parameter to learn $`\mathbf{w}`$

## pros and cons

- optimizes partial ranking, a better objective than point-wise approach
- still does not directly optimize ranking

## weighting pairs

intuition: some pairs are more important.

- if we switch the order of document $`i`$ and $`j`$, the objective (nDCG) will change accordingly. but this differs w.r.t wich pair $`(i, j)`$

example: LambdaMART

# learned

- design the model/objective based on the evaluation function:
  - for example, for ranking problems, objective based on classification does not capture well enough
- pairwise approach
  - weighting pairs

# questions

- how to construct absolute ranking from partial ranks?

# resources

- https://people.cs.umass.edu/~jpjiang/cs646/16_learning_to_rank.pdf
  - pointers to dataset, feature list, 
- https://www.slideshare.net/HasanHTopcu/learning-to-rank-from-pairwise-approach-to-listwise
