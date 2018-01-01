[paper](http://proceedings.mlr.press/v22/lin12/lin12.pdf)

# why sampling from combinatorial space is hard?

if not using MCMC, then the space is exponential, 

if using MCMC:

1. think of Gibbs sampling, the set of possible values of a single variable can be restricted by other variables' values (because of solution feasibility)
2. some times, no variable can be updated without violating the constraint
   - in other words, the space is divided into different "regions" (**disconnected-space issue**). it's non-ergodic

# sampling via "bridging"

- goal: sample according to distribution `\mu` (a vector on `X`) from constrained combinatorial space `X` using MCMC
- issue: regions in `X` are disconnected. how to make the chain ergodic?

approach:

1. define a set of bridging states `Y` that connects regions in `X`
2. sample from the joint space `X \cup Y` and discard the samples in `Y`
3. the transition matrix in the form `[(1-b) P_X, b Q_B; f Q_F, (1-f) P_Y]`
   - `P_X` and `P_Y` are the transition matrix for `X` and `Y`
   - `Q_B` and `Q_F` are the inter-connection

challenges:

- how to do the bridging so that stationary distributions are preserved. 
- what's the mixing time? what are the controling factors?


# other methods

- Barrett and Simma (2005): assign small probability mass to each invalid state
  - mixing can be slow (if the valid solution space is sparse)
- 

# concepts

- stationary distribution: a distribution `\mu` that satisfies `\mu = P \mu`
  - irreducible aperiodic chain ensures unique stationary distribution regardless of initial state
  - irreducible: all states communicate with each other	("communicate" means "reachable"
  - chain of period `d`: starting in state `x`, the chain can return to `x` *only* at multiples of the period d
- mixing time: the time until the chain reaches stationary distribution
  - how to calculate the upperbound on mixing time
  - stated by theorem 1: related to *absolute spectral gap*: `min{1-\lambda_2, 1+\lambda_n}`, where `\lambda_i` is the `i`th largest eigen value.

# algorithm

## bridge construction

1. choose the collection of state subsets, `{S_1, ..., S_m}`
   - each state in `X` is covered by at least one subset `S_i`
   - **how** to choose the collection of state subsets, `{S_1, ..., S_m}`
2. for each subset, `S_i`, create new state `y_i`. this gives `{y_1, ..., y_m}`
3. create a transition from `x` to `S_i` if `x \in S_i` and vice-versa
   - the probabilities are set according to Lemma 1 (Eq 3)

bridge: by `x-y` and `y-y`, `x` links to  `x`

## hierarchical bridging

motivation: the clustering structure of the sample space is largely unknown

def: k-th level bridge -- vector of length `K-k` 
  - assuming the initial vector length is `K`
  - `0-th` level corresponds to `X`

at some level `k`, the sampler has three sets of probabilities:

- going up: to one of its parents `k+1`-th by randomly removing one element
  - the probability is uniform (`b_k / (K-k)`)
- going down: to one of its children, probability `\mu_k(y)` proportional to `\mu` (the density function)
  - evaluating `\mu_k(y)` exactly can be exponential
- for `k != 0`, intra-level transition is not allowed.

## dynamic construction

the sampler builds the chain progressively. 

**key issue**: how to evaluating `\mu_k(y)` efficiently

paper's solution:

- cache intermediate result `\mu_k(y)`
- initially over-estimate it (to encourage exploration)
- later udpate it if it's visited again

# learned

- an general and intersting problem: sampling over combinatorial space
- key properties to check for a MCMC algorithm:
  1. whether it gives stationary distribution
  2. mixing time
- interpretation of "chain mixes":
  - samples are taken as *independently*
  - in other words, there is *small autocorrelation* on the chain samples
- one method to sample over it using techniques:
  - hierarchical bridging: the higher the bridge (smaller `k`), the more abstract (more values removed) and easier to jump
    - a useful way to view it: it higher level bridges facilates faster jump. however it requires evaluation of `\mu_k(y)` accurately
  - dynamic construction of the sampling chain
  - a key problem: evaluating marginal distribution `\mu_k(y)` efficiently. 

## evaluating sample quality

- autocorrelation function
  - a time series compared with itself but with time k lag behind
  - according to the [formula](http://www.itl.nist.gov/div898/handbook/eda/section3/eda35c.htm): essentially covariance normlaized by variance
- evaluating samples quality 1: autocorrelation on energy trajectories
  - energy trajectory: time series of energies by each sample
  - high autocorrelation means chain mixes slowly
- evaluating samples quality 2: correlation on sampled data and true distribution
  - needs to know the true distribution (feasible only for small problem size)

# questions

- how to evaluate `\mu_k(y)` efficiently for our problem?
- don't quite understand the paper's evaluation method for `\mu_k(y)`
