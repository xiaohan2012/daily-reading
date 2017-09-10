# recommendation based on matrix factorization (MF)

recommend movie to user, two main approaches:

- content-based filtering
- collaborative filtering (domain-free): suffer from cold start problem
  - neighbourhood approach: recommend movies based on people of common interest to me
  - latent factor models

# latent factor models: explanation

characterize both movie and users by **factors**, each factor represent an aspect of the movie/user, such as the comedy, animation, male/female, children/adult, etc. however, the factors might also be uninterpretable. 

For each factor, there is a score to measure the degree of the user/movie that adheres to the factor. For example, if a movie is a very typical comedy movie, its score on comedy factor is high.

# basic MF model
input: matrix of user-item rating, $`r_{ui}`$ is user $`u`$'s rating on item $`i`$. note that the matrix is **incomplete**. 

goal: 

- associate each user $`u`$ with a vector $`p_u \in \mathbb{R}^f`$ and each item with a vector $`q_u \in \mathbb{R}^f`$
- such that the score for each observed entry in $`r_{ui}`$ matches $`\hat{r}_{ui} = q^T_i p_u`$

related to SVD, but SVD cannot handle incomplete matrix. 
instead MF models directly on observed entries. 

objective function:

$`\min\limits_{p, q} \sum\limits_{(u, i) \in \kappa} (r_{ui} - q_i^T p_u)^2 + \lambda(||q_i||^2 + ||p_u||^2)`$

just an example objective, that can be others such as using $`l1`$-norm. 


# learning algorithms

both $`p`$ and $`q`$ are unkonown, obj is not convex. 

## SGD

each $`(u, i)`$ is like a training instance (for regression) with correct value $`r_{ui}`$, 
however unlike training by mini-batch, different instances might not share the same parameters $`q_i`$ and $`p_u`$. 

SGD loops through each $`(u, i)`$ pair and update the parameters **for each pair**. 

error for predicting $`(u, i)`$ is $`e_{ui}=r_{ui} - q_i^T p_u`$, so the partial derivative is:

- for $`q_i`$, $`(e_{ui} p_u - \lambda q_i)`$
- for $`p_u`$, $`(e_{ui} q_i - \lambda p_u)`$

if the matrix is dense, it would be impractical. 

## alternating least square (ALS)

update $`p`$ ($`q`$) by fixing $`q`$ ($`p`$) (two sub-problems)

each problem is a least-square problem for each $`i`$ or $`u`$. 

the least-square problem is: given a set of movies $`M`$ associated with one user $`u`$, we want to update $`p_u`$ based on $`r_{ui}`$

in other words, we can update each $`u`$ independently at each iteration (which allows **parallelization**)

# extensions

## adding biases

issues: 

- user can have bias (critical, permissive?): $`b_u`$
- similarly, item can have bias (high rating just because of popularity): $`b_i`$
- normalizing the ratings (like substracting the rating by the average): $`\mu`$ (or average depending on the movie)

then objective is: 


$`\min\limits_{p, q} \sum\limits_{(u, i) \in \kappa} (r_{ui} - \mu - b_u - b_i - q_i^T p_u)^2 + \lambda(||q_i||^2 + ||p_u||^2 + b_u^2 + b_i^2)`$

# other

- implicit feedbacks and attributes
- temporal dynamics
- ratings with different confidene weights. 


# source

- Yehuda Koren, and Chris Volinsky, Matrix Factorization Techniques For Recommender Systems