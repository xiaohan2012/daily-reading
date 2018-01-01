# Toward Optimal Active Learning through Monte Carlo Estimation of Error Reduction 

naively, each query selection takes $`O(n^2t)`$, where $`t`$ is the time to train the model. 

# incremental update  ideas

## incremental training 

(after adding a few examples): training means updating the model parameters

- [navie bayes] parameter estimation](http://www.cs.columbia.edu/~mcollins/em.pdf)
- [nayes bayes parameter update, Equation 6](https://pdfs.semanticscholar.org/55db/80ba1c68921175e6666068c42d7ddf17f971.pdf)

only affects the parameters associated with the corresponding label. 

Say $`(x, y=1)`$, then only $`\theta_{i1}`$ is affected, where $`i`$ indexes the features. 

ideally, $`t`$ in time complexity shouldbe dropped and it becomes $`O(n^2)`$.

## incremental re-classification

in other words, only class probabilities associated with affected $`\theta_{ij}`$ are affected. 


## skipping the error evaluation for certain examples

aftering including a candidate query, we need to estimate the error for each point in the pool. 

however, for points that are "far away" from the candidate query node, their error should remain unchanged. 

now we define "closeness" between points, if two points share no feature values, then they are totally different. conversely, if they share a lot of feature values, they are very similar (thus its error should be updated)

we can either make it approximate or 

make it "exact", by building a reverted index from feature to data points. 

in this case, one of $`n`$ in $`O(n^2t)`$ should be dropped. 

## candidates can be sampled

dropping another $`n`$

## estimating prediction error

using only a subset of points in pool

# our case

the model parameters are the samples of steiner trees. 

after including each query, we need to update the samples

## incremental re-classification 

not very obvious

## sampling candidates

in our case, I just removed all the queries with $`P(y=1) \in \{0, 1\}`$. 

It can be further generalized. 

## estimating prediction error using subpool

already used, and sampling weight by closeness to 0.5

## skipping evaluation of far away nodes

how to define close nodes? nodes within k-hops?



# learned

- naive bayes incremental update and re-classification
- sampling query candidates 
- skipping evaluation of far away nodes
