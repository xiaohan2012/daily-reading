# 

[link](http://www.kdd.org/kdd2017/papers/view/network-inference-via-the-time-varying-graphical-lasso)

# setting 

inferring dynamic network from raw time-series data. 

three requirements:

1. matching the empirical observation
2. sparsity (more interpretability and avoid overfitting)
3. different types of temporal consistensy

# contribution

- model different types of evolutionary patterns (smooth change, sudden change, a single node re-wiring), instead of one
- adapts to streaming setting: what setting?
- scalability via ADMM updates in closed form

related to diffusion-based network inference, however, the input data is time-series data, which is different. 

# problem 

minimize graph lasso objective + time consistency penalty

5 types of consistency penalty:

1. a few edges changing at a time: using element-wise l1 penalty, \sum_ij |X_ij|
2. global restructuring: 
  - why?
3. smooth varying: element-wise l2 penalty (aka laplacian penalty)
  - why it's smooth?
4. block-wise restructuring: \sum_j \max_i |X_ij|
  - given some j, the max change corresponds to i, then other edges of j can change up to the maximum value without incurring extra cost
5. perturbed node

# extensions

## asynchrnous observation

the time gap between each consecutive slice is not constant. therefore, there are large gaps as well as small gaps. 

issue: large time gap (expecting large change) will receive more penalty in general. however we shouldn't penalize a lot because this is expected. 

approach: rescale the time consistency penalty by `(\Theta_i - \Theta_{i-1}) / h_1`, `h_i = t_i - t_{i-1}`

however, not sure why another `h_i` is multiplied


## inferring intermediate network

idea similar to interpolating between points

another minization problem involving two time consistency penalty terms (`\Theta_t` and `\Theta_{t+1}`)

## streaming setting

naive approach: update the ith time slice using the previous parameters trained

however, the longer the time sequence, the slower it takes to update.

approach: time window

# algorithm

admm

# learned

- graphical lasso problem (aka sparse inverse covariance selection)
  - originated from estimating probability in Markov Random Field
  - formulation using `log det` and `trace`, 
    - `det` is normalization term from multivariate guassian distribution
    - `trace` derived from [here](https://en.wikipedia.org/wiki/Estimation_of_covariance_matrices#The_trace_of_a_1_.C3.97_1_matrix)
  - without l1 norm, mean and concentration matrix easy to derive. 
  - with l1 norm, more difficult
    - why? 
    - a lot of algorithms to solve. what are their differences?
- covariance matrix and concentration matrix: interpretation
  - variance: expectation of (x - mean of x)^2, degree of deviation
  - covariance: 
    - if two variables are independent, their cov is zero. the reverse does not hold.
  - use of inverse of covariance (aka concentration matrix): for notational convenience in the objective function

# questions

- group lasso l2 penalty
  - remain "piece-wise" constant
- laplacian penlty --> smoothness
- connection between the different penalty functions and motivation
- admm
