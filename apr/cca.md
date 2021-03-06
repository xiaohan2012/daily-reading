# Canonical Correlation Analysis

intro

- [introduction](https://onlinecourses.science.psu.edu/stat505/node/63)

more mathamatical:

- [umn slides](http://users.stat.umn.edu/~helwig/notes/cancor-Notes.pdf)
- [stanford lecture notes](https://web.stanford.edu/class/stats206/notes/cca.pdf): shorter to read

others

- [sklearn.cca](http://scikit-learn.org/stable/modules/generated/sklearn.cross_decomposition.CCA.html)
- [deep cca](https://www.aaai.org/ocs/index.php/AAAI/AAAI17/paper/download/14166/14487)

# why useful?

- connects two sets of variables by finding linear combinations of variables that maximally correlate.

OR

- input: given data on two sets of variables $`X`$ and $`Y`$, $`X`$ has dim $`p`$ and $`Y`$ has dim $`q`$
- question: how any the variables in the two sets correlated to each other?


# naive approach

 consider two pair from $`X`$ and $`Y`$ and calculate their correlation, then there $`pq`$ combinations. horrible

# CCA: intuition

For $`X`$ and $`Y`$:

1. combine them into 1-dimensional value, $`U`$ and $`V`$ respectively 
2. so that $`U`$ and $`V`$ are maximally correlated. 
3. analyze the correlation for $`(X, U)`$ and $`(Y, V)`$ separately

This serves the purpose of dimension reduction. 

# techenical details

- there are $`min{p, q}`$ pairs of $`(U_i, V_i)`$ (called *Canonical Variate Pairs*), each pair maximizing the covariance 
- each $`(U_i, U_j)`$ pair are *uncorrelated/orthogonal* with each other if $`i \neq j`$ (so for $`(V_i, V_j)`$ and $`(U, V)`$) (similar to PCA)

# examples

see the [link](https://onlinecourses.science.psu.edu/stat505/node/63)

# relation to eigen and reduction to generalized eigenvalue problem

main idea:

- transform the lagrange form
- do the derivative 
- find the condition for derivative equal to zero

refer to [this answer](https://math.stackexchange.com/questions/222689/eigenvalue-decomposition-of-block-covariance-matrix-for-canonical-correlation-an)

## reduction to generalized eigenvalue problem

http://mlg.postech.ac.kr/~seungjin/courses/dr/handouts/handout03.pdf

can be extended to multiple set of variables


# note on [sklearn.cca](http://scikit-learn.org/stable/modules/generated/sklearn.cross_decomposition.CCA.html)

- `predict` maps from `X` to `Y`
- `transform` does the dimension reduction on both `x` and `y`
- do not understand what's the `x_rotating` and `x_loadings` mean
- solved using [partial least square](https://github.com/scikit-learn/scikit-learn/blob/a24c8b464d094d2c468a16ea9f8bf8d42d949f84/sklearn/cross_decomposition/pls_.py)


# learned

- intuition of CCA: why is it useful
- formulation of CCA
- relation to eigenvalue
- generalized eigenvalue problem

**what's missing**

- how to solve the eigen value problem
- how to solve generalized eigenvalue problem?

# other related techniques

- [deep CCA](http://people.ee.duke.edu/~lcarin/Shaobo11.7.2014.pdf)
- kernel CCA