# Meta-Graph Based Recommendation Fusion over Heterogeneous Information Networks

matrix factorization is the core in RS. in practice, recommendation data is usually in heterogenous networkk with rich information. 

this work copes with information network with rich side information

novelty: it learns all the side informaiton jointly instead of separately

# approach

1. matrix factorization over `L` meta-graphs to learn `L` sets of representations for user and item
2. factorization machine to learn the recommendation model based on the above representations
3. group lasso to reduce features, thus reduce computation time
   - as a side product, it also learns the importance of meta-graphs

meta-graphs: just graphs after projection (matrix multiplication)

factorization machine: 

- input: feature vector use-item pair, in this case, concatenation of represnetation sin `L` meta-graphs 
- model: 2nd order regression (linear regression + 2nd order interaction)
  - captures interaction between different meta graphs



# source

https://dl.acm.org/citation.cfm?id=3098063