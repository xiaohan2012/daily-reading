# MCMC and Metropolis Hastings

- checked [this](https://arxiv.org/pdf/1504.01896.pdf)
- [some good review on ergodicity by me](2017/august/markov-chain-coupling-stationary-distribution.md)
- how to determine how fast is the convergence

requires the Markov chain (defined by the proposal distribution, $`q`$) is irreducible. 

# local re-wiring

one possible $`q`$ for random Steiner tree $`T`$: called local re-wiring

1. randomly select a node $`v`$ in $`T`$
2. start a random walk from $`v`$ until it re-touches the $`T`$, call this path $`u_1, \ldots, u_k`$, where $`u_1 = v`$
3. the new tree is defined by removing the "old path" and adding the new loop-erased path
   - the old path is the path by traversing from $`v`$ to the root until it touches either a terminal node or $`u_k`$. 
4. call this new tree $`T^{'}`$

this only solves the problem of generating a sample, but what's the form of $`q(T^{'} | T)`$ and $`q(T | T^{'})`$?

ok, 

- $`q(T^{'} | T)`$ should be the probability of taking the removed path, $`\prod\limits_{(u, v) \in \{u_1, \ldots, u_k\}} p(u, v) / p(u)`$
- $`q(T | T^{'})`$ should be the probability of taking the removed path


# basic principle of choosing $`q`$

still, how to design the $`q`$? how to make it mix faster?

[for example](https://stats.stackexchange.com/a/100136/7259)

1. explore the sample space efficiently
2. rejection rate shouldn't be too high, otherwise, the sampler is stuck at one place
3. meanwhile, acceptance rate shouldn't be too high, otherwise, it might be stuck in local region



  

