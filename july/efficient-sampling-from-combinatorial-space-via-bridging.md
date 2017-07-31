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

# learned

- an general and intersting problem: sampling over combinatorial space
- key properties to check for a MCMC algorithm:
  1. whether it gives stationary distribution
  2. mixing time
# questions

- what's the bridging state for our problem