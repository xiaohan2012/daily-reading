# matlab code

- `SLEEC/Clustering/multipleClustering.m`: clustering
  - `SLEEC/Clustering/runHierKmeansFt.m`: clustering algorithm
- `SLEEC/sleec_train/clusterSVP_asym.m`: SVP 
  - `SLEEC/sleec_train/WAltMin_asymm.m`: alternate minimization of `U` and `V`
  - `SLEEC/sleec_train/updateU.cpp` and `SLEEC/sleec_train/updateV.cpp`: for the actual update (written in `mex` and `openmp`) 
- `SLEEC/sleec_train/computeW.m`: ADMM part, no idea where `train` comes from

## observation

the source code does not use SVP as claimed (Algorithm 3 in the paper), 
instead, it uses ALS

# related python libraries

- https://github.com/benfred/implicit: ALS in cython


# implementation detail

- used cosine to build the SVP kNN graph
  - not using dot-product
- used Ridge model from sklearn  for optimizating the linear regressor
  - not using ADMM
- `w_thresh` and `sp_thresh`
  - set small values in parameters to zero to ensure sparsity
  - in file `clusterSVP_asym.m`
- some unknown parameters
  - `params.cost = 0.2`: liblinear cost coefficient, related to l2 regularizer?
  - `params.NNtest = 25`
  - `params.normalize = 1`

# notes on lapack usage in `implict`

lapack routines:

- `axpy`: `y=\alpha x + y`, where `x, y` are vector and `\alpha` is scalar
- `posv`: solves a linear system

these routines are used by alternating least square

# next

- enforce sparsity:
  - elasticnet and sparsity on embedding
- least square with l1 regularization
  - http://cvxopt.org/examples/mlbook/l1regls.html
