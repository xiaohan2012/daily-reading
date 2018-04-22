# Canonical Correlation Analysis

- [introduction](https://onlinecourses.science.psu.edu/stat505/node/63)
- [more mathematical](http://users.stat.umn.edu/~helwig/notes/cancor-Notes.pdf)
- [sklearn.cca](http://scikit-learn.org/stable/modules/generated/sklearn.cross_decomposition.CCA.html)
- [deep cca](https://www.aaai.org/ocs/index.php/AAAI/AAAI17/paper/download/14166/14487)

- connects two sets of variables by finding linear combinations of variables that maximally correlate.

OR

- input: given data on two sets of variables `X` and `Y`, `X` has dim `p` and `Y` has dim `q`
- question: how any the variables in the two sets correlated to each other?



# naive approach

 consider two pair from `X` and `Y` and calculate their correlation, then there `pq` combinations. horrible

# CCA: intuition

For `X` and `Y`:

1. combine them into 1-dimensional value, `U` and `V` respectively 
2. so that `U` and `V` are maximally correlated. 
3. analyze the correlation for `(X, U)` and `(Y, V)` separately

This serves the purpose of dimension reduction. 


# techenical details

- there are `min{p, q}` pairs of `(U_i, V_i)` (called *Canonical Variate Pairs*), each pair maximizing the covariance 
- each `(U_i, U_j)` pair are *uncorrelated/orthogonal* with each other if `i \neq j` (so for `(V_i, V_j)` and `(U, V)`) (similar to PCA)

## quetions

- why the solution corresponds to the eigenvlaues of XX matrices? (relate to PCA?)
- 

# examples

see the [link](https://onlinecourses.science.psu.edu/stat505/node/63)

