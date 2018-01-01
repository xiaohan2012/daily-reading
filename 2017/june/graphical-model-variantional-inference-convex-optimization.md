# graphical model and convex optimization

- [paper](https://people.eecs.berkeley.edu/~wainwrig/Papers/WaiJor08_FTML.pdf)
- [slides](https://people.eecs.berkeley.edu/~wainwrig/Talks/A_GraphModel_Tutorial)


# goal of interest

- compute log partition function
- local marginal distributions
  - the effects of observations can always be absorbed by modifying the canonical parameters `\theta` and/or the sufficient statistics `\phi` appropriately.
- most likely configuraiton (`argmax_x`)
- page 19 of slides


# message passing on trees

- exact inference boils down to variable elimination order
- directed graphs are converted to undirected graphs so that algorithms for undirected case are enough
  - parents for each child are connected
  - factors correspond to cliques

goal:

- infer `pr(o)`
- exact inference done via dynamic programming
  - split the tree by node(s) o into subtrees
  - for each subtree, it is a smaller subproblem
  - what's the time complexity
- "message" `M_{ij}(v)`: message passed from node i to node j if `x_j=v`
  - produced by variable elimination
  - in the above case, variable `i` is eliminated

sum product and max product:

-  they are almost the same except for the operators. 

# junction tree algorithm

motivation: temptating to use the inference algorithm on tree to non-tree graphs

related to concept of [tree decomposition](https://en.wikipedia.org/wiki/Tree_decomposition)
  - goal: a mapping of a graph into a tree that can be used to define the treewidth of the graph and *speed up solving certain computational problems* on the graph

running intersection property:

- def: if variable `x` is in cluster `i` and `j`, then `x` is also in the unique path between `i` and `j`
- equivalence to graph triangulation

triangulation:

- for cycle of length four or longer, add an edge 

clique tree of graph `G`: nodes defined by cliques of `G`

a clique tree that satisfies running intersection property is a *junction tree*.

- tree inference algorithm can be directly applied on junction tree.

junction tree algorithm:

1. triangulation
2. form junction tree
3. do tree inference

# approximate message passing algorithms

## loopy sum-product/belief propagation

essetially run message passing for trees on general graphs. 

however, it's approximate because of cycles in the graph

## naive mean field algorithm

- `\mu_s`: variable `s`
- `\theta_s` and `\theta_{st}`: parameter for node and edge
- update rule for `\mu_s`: `(1 + exp(-(\theta_s + \sum_{t \in N(s)} (\theta_{st} \mu_t)))^{-1}`
  - essentially node `s` receiving  messages from its neighours
- **core questions** of the book
  - does the update have fixed point?
  - does it converge?

# exponential family

general form:

- `exp { <\theta, \phi(x)> - A(\theta) }`
  - `\phi`: a set of potential functions or sufficient statistics
    - each function corresponds to a factor, like feature
  - `\theta`: parameters associated with each factor
  - `<..>` inner product
- bridge between convex analysis and inference algorithm (**why?**)

general goal: find a probability density function for the input space `X`

maximum entropy principle : 

1. maximize entropy of probability density function, `H(p)` *(form of `p`?)*
  - an example of `p_\theta(x) = exp{ \sum_{\alpha \in I} \theta_\alpha \phi_\alpha(x) - A(\theta)}` (exponential family)
  - `A(\theta)`: log normalization constant
2. `p` is "faithful"(?) to the observed data

a constrainted optimization problem

- set `I`: the set of feature function, each feature function corresponds to a clique
- `\phi_i`: ith potential function, mapping input space `X` to `R`, `i \in I`
- each `\phi_i` is associated with a parameter `\theta_i`

## Ising model

- `p_theta(x) = exp(\sum_{s \in V} \theta_s x_s + \sum_{(s, t) \in E} \theta_{s,t} x_s x_t - A(\theta))`
- domain: `x_s \in {0, 1}` (binary)

## Gaussian Markov Random Field (GMRF)

- continuous version of Ising model
- `p_theta(x)=exp( <\theta, x>  + trace(\Theta x x^T)  - A(\theta, \Theta))`
- `<...>` is inner product
- `trace` = Frobenius inner product on symmetric matrices (sum of all elements)
- parameters `\theta` and `\Theta`
- potential functions:
  - `\phi_s=x_s`
  - `\phi_{st}=x_s x_t`

## Mixture models

basic *building block*:

- `X_s`: multi-nomial random variable to determine the choice of mixture component/Gaussian distribution (instead of one Guassian distribution)
- `Y_s`: *conditional* Gaussian distribution (depending on `X_s`)
- parameters `\theta_s`: 
  - `\alpha` for `X_s`: dim=`r`
  - `\gamma` for mean of `Y_s`: dim=`r`
  - `\gamma^{'}` for standard deviation of `Y_s`: dim=`r`
- density function:
  - `p_{\theta_s}(y_s, x_s) = p_{\alpha_s} (x_s) p_{\gamma_s}(y_s | x_s) = exp(\sum of \alpha indicator(x_s) + \sum \gamma \indicator(y_s))`

can be embedded into more sophsticated models such as GMRF

three components: 

- `p(x_s)`: multinomial variable, corresponds to vertices in graph
- `p(x_s, x_t)`: corresponds to edges in graph
- `p(y_s | x_s)`: the mixture model described above

## Latent Dirichlet Allocation

variables:

- document `U`: dirichlet variable (vector)
- topic `Z`: multinomial variable (one-hot vector)
- word `W`: multinomial variable (one-hot vector)

parameters:

- `\alpha`: prior topic distribution
- `\gamma`: topic-word probability

model/density function:

- prior generates document topic vector: `pr(u) = exp(sum_i \alpha_i log u_i)`
  - why `log u_i`? apply exp and log  on the definition of dirichlet distribution
  - [http://www.cs.columbia.edu/~jebara/4771/tutorials/lecture12.pdf](more exponential family functions)
- topic is generated from the vector via multinomial distribution: `pr(z | u) = exp(sum_i I_i(z) log u_i)`
  - again, take exp and log
- topic generates word: `pr(w | z)=exp(\sum_i \sum_i \gamma_{ij} I_i(w) I_j(z))`
  - `\gamma`: 2d matrix capturing the word probability conditional on topic


## error correcting code

problem: two sides communicate by sending sequence of bits of length `m` via a noisy channel, however:

- each bit has probability `\epsilon` to flip
- the sender consider only a subset of `{0, 1}^m` code ("code book")
  - code book consists of a set of parity check constraints (for example, `x_i + ... + x_j = 0`)
  - "hard core constraints"
  - each constraint can be thought as a factor (like a bipartite graph, Figure 2.9)
- given an observed bit sequence `y`, can we recover the original sequence `x`
  - the problem is essentially calculating `pr(y | x)`

how to cast it as exponential family? I don't quite understand. 


# mean parameterization and inference problems

exponential families can be characterized alternatively via *mean parameters*, 
which fascilitates understanding of marginalization and maximum likelihood esitimation. 

mean parameter (single real value):

- `\mu_{\alpha}`: value of `\phi_{\alpha}(x)` integrated over `x` on `p(x)` (Equation 3.25)
- `E_p [\phi_\alpha(x)]`: expectation of factor `\alpha`, `\phi_{\alpha}` (x) under distribution `p` 
- "marginal"

all realizable mean parameters:

- `M` (Eq 3.26)
- set of all mean parameters (set of real-valued vectors) such that there exists some probability distribution producing it


## Example: Gaussian MRF

- `\mu = E[X]`
- `\Sigma = E[XX^T]`: second order moment matrix

covariance matrix: 

- `cov(X_i, X_j) = E[(X_i-\mu_i)(X_j-\mu_j)] = E[X_i X_j] - \mu_i \mu_j`
- matrix form: `cov(X)=E[X X^T] - E[x] E[\mu]^T`
- every covariance matrix is semi-definite positive

then 

- `M`: `(\mu, \Sigma)` s.t. `\Sigma - \mu \mu^T` is semi-definite positive
- `M` is a convex set

## digression: concepts related to "convex"

- convex set `S`: for any `0<=\theta<=1`, `\theta x_1 + (1-\theta) x_2 \in S`, where `x_1, x_2 \in S`
- convex combination: weighted sum of points in `S`, where weights sum up to 1
- convex hull: set of all convex combinations of points in `S`
- polyhedron: intersection of a finite number of half-spaces
- polytope: bounded polyhedron

## Ising mean parameters

- `\mu_s = Pr[X_s = 1]` for all `s \in V`
- `\mu_{sT} = Pr[(X_s, X_T) = (1, 1)]` for all `(s, t) in E`

example: two node model

- three parameters: `(x_1, x_2, x_1 x_2)`
- M corresponds to polytope in 3D space

# role of mean parameters in inference problems

- forward mapping: compute canonical parameters to mean parameters
- backward mapping: the opposite as above and our interest

maximum log likelihood:

- maximize the log likelihood: `1/n \sum_i \log_{\theta} (X^i)=<\theta, \mu> - A(\theta)`
- defines the connection between mean parameter and canonical parameter
- `\mu` is **empirical mean parameter**: 1/n \sum_i phi(X_i)

questions:

- how to compute `A(\theta)`?
- relationship between maximum likelihood and maximum entropy?

# properties of `A`

motivation:

- A is convex
- leads us to conjugate duality
- under certain conditions, there is a one-to-one mapping between `\theta` and `\mu`

properties:

1. first order derivative is the mean parameter
2. second order derivative is covariance matrix of `\phi`
   - is PSD
   - thus, convex

## forward mapping: `\theta` to `\mu`

relationship between 

- gradient `\nabla A(\theta)`: mapping from `\Omega` to `R^d` 
- `M`: all realizable mean parameters

two questions:

### when does `\nabla A` define one-to-one mapping from `\Omega` to `M`?

answer: if and only if the exponential representation is minimal

- minimal exponential family: *only* by setting parameters to zero can we have constant function value. 
- proof: used the properties of convexity

motivation of this question:

- unique identifiability of a propability distribution. 
- if this mapping holds, then the paramerization is unique
- each pair of `(\theta, \mu)` is called dually coupled

why using gradient:

- gradient of exponential family is equivalent to sufficient statistics, which is `M`

### when does `\nabla A` cover all `M`?

image of `\nabla A` turns out to be interior of `M`

why it matters?

- if all points in `M` can be covered 
- it means, all points in `M` can be realized by a member of the exponential family

# Conjugate duality: maximum likelihood and maximum entropy

## digression: conjugate function

the conjugate function `f^*` of function `f` is `f^*(y) = sup{y^T x - f(x)}`

direct interpretation: 

- the maximum gap between linear function `y^T x` and `f(x)`
- maximum achieved at `x` s.t. `f^{-1}(x) = y`
- `y` can be seen as the gradient of `f(x)` (as is the case of `\mu=\nabla A(\theta)`)
- example in Figure 3.8 of cvx book

geometric view:

- intercept of supporting hyperplane (`y` is the slope)
- `y^T x - c <= f(x)`, `c` is the intercept
- related concept: epigraph: area above `f(x)`
- in summary: `y` and `c` defines the supporting hyperplane



## back to main point

given function `A`, conjugate dual function is 

- `A^*(\mu) = sup_{\theta} <\theta, \mu> - A(\theta)`

maximum likelihood problem as a special case, `\mu` is the empirical mean parameter

entropy of density: `\int_X p(x) \log p(x) v(dx)`

notations:

- `\Omega`: domain of `A`, where `\theta` is a member
- `\theta(\mu)`: unique vector in `\Omega` that satisfies `\mu` (gradient/expected value of suff stat)
  - unique because the one-to-one mapping

Theorem 3.4 main idea (Appendix B.2):

1. **equivalence between negative entropy and dual function value**: given `\mu`, the value of the conjugate dual function equals to negative entropy of `p_{\mu(\theta))`, where `\theta` is determined by the one-to-one relationship
  - if exponential family is minimal, then `-H(p_\mu(\theta))` is the optimum (because of one-to-one mapping, no other feasible values)
2. **variational representation of log partition function**: 
`A(\theta)` has a variational representation w.r.t conjugate dual function (Eq 3.45)
  - computing the value is equivalent to maximize over set of `M`
  - thus, the nature of `M` determines the complexity of computing `A(\theta)`
3. **moment matching condition**: one-to-one mapping between `\mu` and `\theta` by moment matching conditions (bijection between `\Omega` and `\mu`)

## why theorem 3.4 matters?

first, `A^*` equals to the negative entropy

second, by solveing the variational representation of `A(\theta)`, we can achieve both of the following:

- computing `A(\theta)`
- the optimal `\mu`

because of the duality, we can tackle it from the other way around:

- given `\mu`, we can get the optimal `\theta`

meanwhile, the optimization problem is concave and differentiable over  convex set, thus can be solved by off-the-self cvx methods. 

third, stationary point (optimal) satisfies moment matching condition. 

## chanllenges

- `M` is difficult to characterize in explicit form
- negative entropy, `A^*`, has no explicit form

# variational principle

reformulate a problem into a optmization problem

"variational" means "alternative", (e.g, variational representation)

example:

- solve linear system: given y, solve `Ax=y`
- variational representation: solve the minimization problem `1/2 u^T A u - y^T u`
  - minimum is achieved when `x=A^{-1} y`, same as the previous problem

v methods for graphical models reply on:

- exponential families
- convex duality

# learned

- interpretating conditional independence and vertex cut
  - equivalent view: pdf is propotional to factorization over all cliques
- update rule for Gibbs sampling on Ising model
  - essentially tossing a coin (binary variable) with  `pr(x_s=0)` and `pr(x_s=1)`
- dynamic programming -- divide and conquer
- LDA: 
  - model: topic vector -> topic -> words
  - dirichlet distribution, multinomial distribution in exponential form (take exp and log)
- difference between supremum and maximum
  - in short, maximum must be in the set while supremum does not
  - see [this post](https://math.stackexchange.com/questions/160451/difference-between-supremum-and-maximum)
- exponential family encompasses many probability distributions, for example:
  - bernoulli
  - binomial/multinomial
  - gaussian
  - dirichlet
  - [and many others](http://www.cs.columbia.edu/~jebara/4771/tutorials/lecture12.pdf)

# questions

- base measure `v`?
- for LDA, how to bind them all together for a document corpus? how to train it? how to do inference?
- why exponential is good?
  - from multiplication to summation, easier computation?
  - related to "mean parameters"
- Ising model  (P4.1)
- 3.4.2, why mean parameters have a central role to play in marginalization problem
- 